---
title: "Newbie struggling with Docker image for Schedules Direct"
date: 2023-04-11
forum: General Help
---

### Post by elsmandino2 on 2023-04-11
[COLOR=#000000][FONT=Verdana]Hi there.

[/FONT][/COLOR]This is not specific to Ubuntu but if any of you guys might be able to help, it would be much appreciated.

[COLOR=#000000][FONT=Verdana]I have just installed Openmediavault 6 on my server and am trying to use Docker images, wherever possible.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have just installed TVHeadend on Docker and managed to get it working - I am using Portainer and used the Docker-Compose code to get everything working.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]However, I need to get Schedules Direct EPG data for TVHeadend and am struggling to find a Docker image that works.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have found this:[/FONT][/COLOR]

[https://github.com/mar-mei/guide2go](https://github.com/mar-mei/guide2go)

[COLOR=#000000][FONT=Verdana]and deployed the following code:[/FONT][/COLOR]

> [COLOR=#000000][FONT=Verdana]
version: "3.4"
services:
guide2go:
container_name: guide2go
image: chuchodavids/guide2go:stable
ports:
- 8080:8080
environment:
- TZ:Europe/London
volumes:
- /SSD/appdata/guide2go:/config
- /SSD/appdata/guide2go:/data/livetv/
- /SSD/appdata/guide2go:/data/images/
restart: always[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]

However, I keep getting the following error:[/FONT][/COLOR]

> [COLOR=#000000][FONT=Verdana]
2023/04/10 15:08:23 [G2G  ] Version: 1.1.3
2023/04/10 15:08:23 [ERROR] open /app/config.yaml: no such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
Any help would be much appreciated.[/FONT][/COLOR]

---

### Post by TheFu on 2023-04-11
```
open /app/config.yaml: no such file or directory
```
That's the error. Fix that.

I don't know docker, but often parts of Linux Containers need added mounts to hold data and config files.  Those mounts need to be provided by the container creation script.

TVHeadend always seemed like a mess to me.  Would you consider using Jellyfin?  It supports HDHR tuners and Schedules Direct for automatic schedule loading, in addition to IPTV streams with m38u files.  Jellyfin is pretty easy to get working, but does have some limitations.

---

