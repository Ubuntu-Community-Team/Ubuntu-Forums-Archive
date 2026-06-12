---
title: "cant run any admin programs from GUI"
date: 2007-12-15
forum: General Help
---

### Post by lmlypfan on 2007-12-15
I can't run any application under system>admin while in gnome

I recently changed processors and motherboard,  But when I try to run synaptic (or any other admin process) i get "failed to run /usr/sbin/synaptic as user root", substitute the absolute directory for what ever admin application I am trying to run.

Also says "Unable to copy the user's Xauthorization file"

when starting the xserver "failed to initialize HAL!"

I have been trouble shooting the HAL issue, but can't solve that either.

Help?

---

### Post by lmlypfan on 2007-12-15
bump

---

### Post by fsando on 2007-12-23
I don't know if can be of any help to you but regarding the hal issue there may be some info in this thread:
[http://ubuntuforums.org/showthread.php?t=456395](http://ubuntuforums.org/showthread.php?t=456395)

Poster #7 says hal is basically a list of all hardware, when it fails it could be due to any entry in the list. 

Personally I have a small fat32 partition I use for sharing files between windows and linux. I always change its mount point (in /etc/fstab) to a folder in my home folder. but now the permissions are wrong which causes hal to fail. After changing to umask=000 and gid=1000 hal works again.

info on what went wrong from this command
```
sudo /usr/sbin/hald --daemon=no --verbose=yes
```

---

### Post by Craigus on 2007-12-23
This might be helpful:

[http://www.mepislovers.org/forums/showthread.php?t=602]("http://www.mepislovers.org/forums/showthread.php?t=602")

---

