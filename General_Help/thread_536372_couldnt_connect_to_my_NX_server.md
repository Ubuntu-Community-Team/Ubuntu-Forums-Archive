---
title: "couldnt connect to my NX server"
date: 2007-08-27
forum: General Help
---

### Post by bigboss2200 on 2007-08-27
hi..

  I have installed freenx using [this]("https://help.ubuntu.com/community/FreeNX") tutorial and went exactly in every single step there.. but when i try to connect to it using a client that was installed in the same machine, i got the following error: 

> 
.
.
.
.
.
.
.
.
.

NX> 148 Server capacity: not reached for user: faris
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="faris" --type="unix-gnome" --geometry="1280x974" --kbtype="pc105/us" --screeninfo="1280x974x24+render" 

ssh: connect to host 127.0.0.1 port 22: Connection refused
Killed by signal 15.




i think i missed a file, can any one pin point it for me so i can edit the host and port? 

Thanks...

---

### Post by bigboss2200 on 2007-08-27
edit: what im missing is the port.. this port is closed by my country proxy server so i cant use it.. and when i cange it from /etc/nxserver/node.conf and restart ssh, i still get the same error.. any help there..?!

---

