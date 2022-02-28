# Perth Nerd Herd Game Servers

Repository is to store configurations, builds and preferable a single docker compose for deploying a suite of Perth Nerd Herd game servers

Initial build contains Garry's Mod with Prop Hunt using Workshop Collection designed by Labrat
https://steamcommunity.com/sharedfiles/filedetails/?id=657069545
(as at 27/02/22 this collection is pending an update to replace depreciated and EOL prophunt components)

# Initial Setup
- Install docker and docker compose on host
- Clone from Git
- Copy "example.env" to ".env"
- Update .env with relevant settings
- Run "docker-compose up"

*** Important to note, the initial install process does appear to hang after installing the gamemode (for prophunt for example, it installs a 3.9Gb app, then seems to start the server, but nothing runs). This is due to the server instance not properly reporting workshop addon install processes to stdout (console). Expect the initial install to take 1-2 hours.
Subsequent starts of the server will not take as long
Adding a server instance DOES redo this but only on the new instance, which again will survive past reboots (unless the volume is deleted)


# Adding a server
- In .env file, copy variables and update server number appropriately (eg SERVER1_NAME copy to SERVER2_NAME)
- Update new numbered server with appropriate config
- Copy Server service in docker-compose.yml and update name
- Change the volume name and add a new volume instance to the config
- If Network is in host mode ensure Server ports are different (srcds will autochange to next numerically from 27015 anyway)
- Update variable names in new service definition to match new server variable numbers
- Run "docker-compose up" (Not this will also restart existing servers)
