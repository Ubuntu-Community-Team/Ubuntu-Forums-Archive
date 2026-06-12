---
title: "vnc4server startup"
date: 2005-07-25
forum: General Help
---

### Post by coniferous on 2005-07-25
Heya folks, i'm having trouble getting my vnc4server to startup when my computer starts up. i currently have it set to start up when i log in as part of a session. while it works, its not an ideal solution for me beacuse i would like to be able to disconnect the mouse and keyboard from the computer beacuse i'm using it as a file server. if the power goes out or somthing like that i'm kinda messed  :???: 

[http://www.ubuntuforums.org/showthread.php?t=16953](http://www.ubuntuforums.org/showthread.php?t=16953)

i read this thread here and tried making a script, but even that didnt work. i cant even get it to call it on startup. surely theres an esier way of doing this i dont know about. anyone know of some scripts that will load things on startup?

thanks in advance for any help :)

---

### Post by jason_dc on 2005-07-26
you could just add this line to the file /etc/rc.local

/etc/init.d/vncserver start

rc.local starts anything up after everything else has been started

simple way ...

---

