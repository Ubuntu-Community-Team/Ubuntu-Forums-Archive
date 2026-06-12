---
title: "vncviewer over ssh fails if no monitor connected"
date: 2012-12-11
forum: General Help
---

### Post by irose123 on 2012-12-11
I have a headless Ubuntu 10.04 system with a shared desktop. Normally I can connect wirelessly to it (it hosts a Wi-Fi access point) tunneling via SSH just fine using:

```
vncviewer -via myuser@10.0.0.2 localhost:0
```I enter the user password for SSH and the sharing password for VNC, and all is fine.

_**HOWEVER**_ if when the system boots there is no monitor attached via VGA cable, whether the monitor has power or not, the SSH connection is refused. But SSH still works OK independently!

```
ssh myuser@10.0.0.2
```I presume this is something to do with the server's on-board graphics stopping the desktop sharing working properly if it appears there's no monitor on the end of the cable, maybe due to pins not being connected.

Does anyone know of any setting to stop the server from being so fussy? When I move the server from development in the lab (with a monitor) to deployment (headless) then all services work OK except for desktop sharing because of this problem.

Thanks.

---

