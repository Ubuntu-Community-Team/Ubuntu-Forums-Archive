---
title: "Ubuntu Server with Docker - Random Disconnect from internet"
date: 2023-07-18
forum: General Help
---

### Post by tjelite on 2023-07-18
I have a issue with my Ubuntu Server with docker, its a mediaserver with plex and jellyfin.


The server will disconnect from the internet and need to be manuelly restaded. 
it have been better after I buy new Router and Networkcard but 
the issue is still there. It happen many times when I download 
media and adding more content to Sonar/radarr at the sametime.
Last night I watch 3-4 episodes and when the last episode ended the server get disconnected. The issue always came in random moments, My and 1-2 friend can Stream at the same time plus can download without the issue come. 
When the issue comes I cant connect to the ssh with Public or Local IP.
it will come when I working/streaming or when No body using the server.
I have tried disable IPv6 and only have the IPv4 enable, I think it get better with only IPv4. 
Did try Ubuntu Desktop some time but the issue is the same. The server are headless so no graphics card or screen is connected. 
Have done alot of different settings have I find on Forums nothing have get it fixed. 
I have no internet issue on my main computer, mobile, tablet, android box, on any smart devices in the home network only the server.
Do I looking for the error at the wrong place maybe its no Internet issue? 
If it should be a network issue it should fix with new router and networkcard and cable right?


Installation 1:
  Ubuntu Server
  Docker
  Containers
  
Installation 2: (current setup)
  Proxmox
  VM: Ubuntu Server
  Docker
  Container
  
Containers: 
  Portainer (Container management)
  Ngnix Reverse proxy R-proxy)
  Dashy  (Dashboard)
  Jackett ( Indexer, Torrentsource)
  Radarr (Movies)
  Sonarr (Tvshows)
  bazarr (Subs)
  Metube (YTDL, and more)
  Plex (Mediaserver)
  Jellyfin (MediaServer)
  Qbittorrent ( Download Client)
  Transmission (Seeding)
  Dozzle (logs)
  Filebrowser (Filebrowser)
  Code-server ( Code Editor)
  Ngnix-Webserver (html, PHP) (Webserver)
  Watchtower (Auto Update Containers)
  
Spec:
  Ryzen 7  8core
  Motherboard I do t remember
  16 GB Ram and 32GB ( memtest86 pass)
  M2 SSD 256GB
  1.5TB HDD
  4 TB HDD
  1TB ( not right now)
  1TB ( not right now)
  500GB ( not right now)
   TP-Link TG-3468 10/100/1000 ( New Networkcard)
   D-link DIR-X5460, AX5400 WiFi 6 ( New Router)
   Network 100/100 
   Public IP
   Cloudflare
   Reverse proxy (ngnix)
   
I have done:
  Enable IPv6
  Disable IPv6
  Tried 1 router with OpenWRT ( Custom Firmware) and New router
  D-link DIR-X5460, AX5400 WiFi 6.
  With Reverse proxy (ngnix) and without proxy.
  With Public IP and Without Public IP
  Reinstall Server with my completed Code and with clean code.
  Different Networks Settings.
  More Airflow less Airflow
  Different Networks Cables
  With and Without Graphics Card
  With all Containers running with only the base container
  Allot of different settings.
  More/Less Memory
  Different hdd Mount settings
  Watched logs but have not find/understand 1/2 of it.
  auto reboot when no internet connection.
  Flashes Bios
  Diffrent Bios settings
  And many more

---

