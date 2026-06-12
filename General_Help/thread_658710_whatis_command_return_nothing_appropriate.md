---
title: "whatis command return nothing appropriate"
date: 2008-01-04
forum: General Help
---

### Post by jorgeg on 2008-01-04
Every single time I use the whatis command it returns: nothing appropriate. I believe that is not a normal behavior. 

I have tried with common commands like: 
whatis rm
whatis mv
whatis ls

and they all return the same: simply "nothing appropriate"

Any opinions?

---

### Post by yabbadabbadont on 2008-01-04
Try running, in a terminal window, "sudo makewhatis -u", and see if it helps.

---

### Post by jorgeg on 2008-01-05
yabbadabbadont, Thank you very much for replying. Unfortunately, the shell can't find the "makewhatis" command. I'm using Ubuntu Server JeOs editon. Could this be a problem with the edition I am using? 

Some details:
The Ubuntu Server JeOs version I have it installed on a VMWare virtual PC.

---

### Post by yabbadabbadont on 2008-01-05
On a normal Ubuntu installation (server or desktop), there should be a "makewhatis" cron job script somewhere in one of the /etc/cron* directories.  Probably in /etc/cron.daily.  If you can find it, then run it (using sudo) and it should update the whatis database for you.

I've never heard of the "JeOs" version, so I have no idea if the above will hold true for it.

---

### Post by jorgeg on 2008-01-05
yabbadabbadont, 

thanks again for replying. Based on your suggestion I tried **running the script 'man-db' on directory '/etc/cron.daily' **since I could not find the script "makewhatis" and it fixed the problem. Now the 'whatis' command returns the short description for each command.

Ubuntu Server JeOS edition is an variation of the regular server version but configured specifically for virtual appliances. See it here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

Allow me to say that I tried finding the ''makewhatis" script by running (in this JeOS version):

$ sudo find / -name "*makewhatis*"

... and  it could not be found in the system.

Since this edition is not a full server installation, then it is probable that it misses the 'makewhatis' script and the 'makewhatis' database was not created by default (probably to save disk space in the virtual appliance).

Again, thank you very much for your help.

---

### Post by p_quarles on 2008-01-05
> **jorgeg said:**
> Since this edition is not a full server installation, then it is probable that it misses the 'makewhatis' script and the 'makewhatis' database was not created by default (probably to save disk space in the virtual appliance).
That's correct. JeOS is short for "Just Enough Operating System," and the OS is as minimal as the name implies. Since it's not designed to be used independently, you're going to find a lot of normal server tools to be missing. Those tools will be available, however, in a virtualized installation of Ubuntu server edition.

---

### Post by yabbadabbadont on 2008-01-05
On a Gentoo system, /usr/sbin/makewhatis, is a shell script that is included with the "man" package.  Now that I think about it some more, I don't think that Ubuntu includes it on any version of the distribution.  I think that I ended up running "man-db" too...  Sorry for the confusion.  Since it is just a shell script, it should work on your system.  (It looks like it might have originally been written for Slackware from the comments)  I'll attach it in case anyone wants to try it out.

---

