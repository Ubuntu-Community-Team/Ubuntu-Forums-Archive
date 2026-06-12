---
title: "Have I wrecked my Ubuntu installation?"
date: 2006-08-19
forum: General Help
---

### Post by PhoenixHorizons82 on 2006-08-19
I thought I'd try to speed up my Dapper installation by running the Faster-Dapper script (found here [http://www.dylanknightrogers.com/faster-dapper.sh](http://www.dylanknightrogers.com/faster-dapper.sh). Anyway, I discovered that it deletes certain services, so I made sure it didn't delete the "mdadm" service (which I need for my software RAID setup). 

Anyway, after rebooting I was faced with a "/bin/sh: Cannot find interpreter" error. I managed to fix this by re-installing bash with apt-get.

(1) The first problem I'm having is that every time I boot up, Linux attempt to do an fsck on all my Reiser partitions, and it fails because they are not mounted read-only. When I do mount them read-only, the system is able to boot.

(2) The second problem is that after booting, the location "/dev/null" does not have the correct credentials. Something like "crw--------". I can do a "chmod 666 /dev/null", however, when I next boot-up, the problem is still there.

(3) This is a more minor problem - when GDM loads up, and I try to type my login name, the letters don't appear straight away, and sometimes it acts like a key is "stuck down". This is definitely not a keyboard error. The only way out of this is to restart my X-Server (and that doesn't always work).

Once I've changed the permissions on /dev/null, and bypassed the fsck stuff, I can boot up into Ubuntu as normal.

Thanks in advance for ANY help :-)

---

### Post by Mau on 2006-08-19
The link you provided doesn't work, but why would you want to speed up the installation?  It already takes about 15 minutes. :-)  

Try the normal install?

---

### Post by PhoenixHorizons82 on 2006-08-19
EDIT: I've now fixed the link - so it should work now. 

If I do a normal install - presumably I'll lose all my software and everything that doesn't reside on my /home directory (which is on a separate partition). I don't really want to do that until I know I've exhausted all other possibilities.

Every time I boot up, I get the fsck program giving me an error - so I'm now trying to rebuild the Reiser FS tree on all my partitions. It's going to take quite a few hours !! :(

---

### Post by PhoenixHorizons82 on 2006-08-19
UPDATE: Very frustrated now - I rebuild the tree on all my Reiser partitions (didn't take as long as I thought) - and after the next reboot - I STILL get the fsck error... and the /dev/null problem is back again ](*,)

---

### Post by kriding on 2006-08-19
when you do a normal install, at the partioner, select your home partition, set the mount point ashome, but leave the line that says 'leave data instact' (or whatever it is, just don't format that partition)

One you reinstall, all your files in the home partition will be preserved, however, you would still need to install yourprogrammes again.

I know it may seem like a chore, but it's better then your current situation.

---

