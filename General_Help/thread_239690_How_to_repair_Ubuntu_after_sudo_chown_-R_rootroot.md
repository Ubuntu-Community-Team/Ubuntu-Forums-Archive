---
title: "How to repair Ubuntu after sudo chown -R root:root /"
date: 2006-08-19
forum: General Help
---

### Post by ludovicc on 2006-08-19
Hello,

I played with scripts to automate changing users and groups on a directory, and I run by mistake something like 
sudo chown -R user:users /
Ok, this was pretty dumb, but it was so...
I manage with the live CD to return /bin /etc and so on to their normal root user, but my Ubuntu (Dapper) is still a bit broken, with the connection to Internet and other services that don't work anymore. I can login and access my graphic session. 

How can I salvage this installation without losing any personal data and installed application (if possible)?

Thanks

---

### Post by steve.horsley on 2006-08-19
I think you need to reinstall. You'll never get the ownerships right any other way.

Use a live CD to rescue the stuff you need to keep first. 

If you have enough space, you may be able to shrink the correupt partition enough (using gparted) to make room to make a temporary backup partition.

---

### Post by Patrick-Ruff on 2006-08-19
yikes! yes, backup EVERYTHING! lol. good luck man :P...

---

### Post by matthew on 2006-08-19
Eeehhh. Bummer. All I can suggest is use a live cd to rescue and back up your data and reinstall.

If it makes you feel any better, most of us have a similar story of doing something we shouldn't have done and learning the hard way.

---

### Post by ludovicc on 2006-08-21
Hello all, 

Thanks for your support. Unfortunately, I didn't make a backup of my system, a big mistake that I will try to correct next time I reinstall Ubuntu. 

Just for curiosity, is there a planned feature for auto-healing Ubuntu? I mean, if there is some compressed snapshot of all installed files, with their size and permision settings, it should not be too difficult to detect what has changed since the last working configuration, and then run from the live CD a repair install that tries to recover Ubuntu without losing too many user settings. 

Ludovic

---

