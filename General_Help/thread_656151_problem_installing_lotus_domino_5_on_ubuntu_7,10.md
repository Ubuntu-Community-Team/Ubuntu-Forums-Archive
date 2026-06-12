---
title: "problem installing lotus domino 5 on ubuntu 7,10"
date: 2008-01-02
forum: General Help
---

### Post by uffa14 on 2008-01-02
hallo!
I'm very new to linux... and have to install lotus domino server 5,0,11 on a virtualized ubuntu 7,10 for some testing purpose.
I succedeed installng after some google search... 
but when i try to start the next step after installation (it should start an http server to configure domino) something goes wrong!! 
the command was "/opt/lotus/bin/http httpsetup", here the response!!
==================
notes@jars-desktop:/local/notesdata$ /opt/lotus/bin/http httpsetup
01/02/2008 02:11:12 PM  Created new log file as /local/notesdata/log.nsf
01/02/2008 02:11:12 PM  
*****************************************
*      Lotus Domino Server Setup        *
* To setup this server, please connect  *
*     your web browser to port 8081     *
* Example: [http://this.server.com:8081](http://this.server.com:8081)  *
*****************************************
Segmentation fault (core dumped)
notes@jars-desktop:/local/notesdata$ 
===========================
what does "Segmentation fault" mean?:confused:
I need some help!!
Thank's for any help!

---

### Post by Webdawgz on 2008-02-07
Use the domino administrator client from your XP machine.
Then follow these instructions:
[http://www.windelen.be/windelen/wwwindelen.nsf/(All)/10664EE3D8B77D2BC1257091004D1CE8](http://www.windelen.be/windelen/wwwindelen.nsf/(All)/10664EE3D8B77D2BC1257091004D1CE8)

it worked for me.
The only problem i have now, i cannot start the Server again.
which means i cannot access the log file.

---

### Post by SpaceTeddy on 2008-02-08
> **uffa14 said:**
> 
what does "Segmentation fault" mean?:confused:
I need some help!!
Thank's for any help!

i have never worked with domino 5 (i didn't even know it comes for linux :( ) but i know the seg fault means...

it basically means that your domino is trying to read or write memory that it is not allowed to access. I suspect that happens because some system libraries that domino 5 uses have changed since the release of domino 5. i won't go into much more details here, since i am half guessing aswell

as for a solution... try to use an older version of the libraries (if you know which ones domino 5 uses), or an older version of ubuntu (i guess that that the 6.06 LTS server would work better... but that it works is still questionable).

sorry i cannot be of more help

---

