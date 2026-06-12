---
title: "apt-get upgrade woes: lirc!"
date: 2008-06-17
forum: General Help
---

### Post by JeffElkins on 2008-06-17
(k)ubuntu 8.04
> 
(Reading database ... 140065 files and directories currently installed.)
Preparing to replace lirc 0.8.3~pre1-0ubuntu7.1 (using lirc_0.8.3~pre1-0ubuntu7.1_i386.deb) ...
* Stopping remote control daemon(s): LIRC [fail]
Unpacking replacement lirc ...
Setting up lirc (0.8.3~pre1-0ubuntu7.1) ...
* Reloading kernel event manager... [ OK ]
dpkg: error processing lirc (--install):
subprocess post-installation script returned error exit status 20
Errors were encountered while processing:
lirc


Nothing I've tried fixes this. I've tried apt-get install -f.  Anyone else run into this?

Edit: Nevermind. Apt-get remove lirc followed by a re-install fixed things.

---

