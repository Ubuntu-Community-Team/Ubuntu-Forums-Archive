---
title: "Probmes with Partimage-server"
date: 2007-03-15
forum: General Help
---

### Post by tscharf on 2007-03-15
I have been running partimaged for a while on my ubuntu 6.10 system, and all is working well with one glaring problem:  no matter what I change the TARGET variable to in the startup script, the images are ALWAYS saved in /var/lib/partimaged/.   Because I dont have that big a system partition, I would much prefer to have these images get written to my /data directory, which is on its own much larger drive.  

the only way I can get it to work, is if I manually start the daemon with the correct target parameter.   is there any way I can fix this?

Thank you,

---

### Post by auburn on 2007-08-22
I don't know. I thought I did.

---

### Post by brentoboy on 2008-04-14
I'm resurrecting this thread because I am about to get into the same situation, and I am going to post the way I am handling it -- I'm setting it up on a beta Hardy server.

I have exactly the same situation.  I have a small(er) system drive, and I want backup images to go to /data/images/backups instead of  /var/lib/partimaged/

I'll play around with the config file first, because a lot can be fixed in 10 months, but if it has the same issue, I intend to do this.

sudo rm /var/lib/partimaged/
sudo ln -s /data/backup/images/  /var/lib/partimaged/

I imagine that will take care of it.  I'll post back if it doesn't.  If anyone else has any advise for using partimage, please chime in.

---

