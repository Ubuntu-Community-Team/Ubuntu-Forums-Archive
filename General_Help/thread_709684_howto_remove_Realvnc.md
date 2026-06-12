---
title: "howto remove Realvnc"
date: 2008-02-27
forum: General Help
---

### Post by madzib on 2008-02-27
I've installed realvnc enterprice by using the vncinstall script. 
But now I can't get it of my machine. 

Any help please. TIA

---

### Post by amd-64 on 2008-02-27
Assuming there is no uninstall script supplied 

look for executable files under /usr/bin

cd /usr/bin
ls *vnc*
and delete them using sudo 

Also look for a startup script in /etc/init.d
cd /etc/init.d
ls *vnc*
and similarly delete them. The rest of the files will be quite small and harmless.

---

