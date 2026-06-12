---
title: "Remote access from Ubuntu to Mac : how to ?"
date: 2014-02-18
forum: General Help
---

### Post by christophe.maillot on 2014-02-18
Dears,

I sometime need to work from home.
Home, I'm running Ubuntu 12.04 ... at work I'm running a Mac with Osx 10.8.
How to remote access my Mac please ?
I know how to access it while on the same network but not from another town / country / planet ... 

thanks a lot.

---

### Post by Lars Noodén on 2014-02-18
What method do you use to access it on the same network?  There is a good chance that it can be used or modified to work over longer distances.  Probably you need a way in through the router with the help of your network administrator.

SSH, for example, works securely over the net.

---

### Post by christophe.maillot on 2014-02-19
the method used for accessing on the same network is vnc ... how to configure it to be accessible from another network ?

---

### Post by Lars Noodén on 2014-02-19
Can you connect to your Mac via SSH?  You have to have Remote Login enabled for your account, but if that works then you can [tunnel VNC over SSH](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html).  VNC is not very secure by itself so it is normal to tunnel it anyway and SSH works over the open Internet as well as over the LAN.

---

