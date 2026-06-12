---
title: "Another Ubuntu Crash? Hardware or Software?"
date: 2006-11-06
forum: General Help
---

### Post by Kurt_Alan on 2006-11-06
**[SIZE="5"][/SIZE]**

About a month ago I had a crash that prevented me from accesssing GDM: searches on the Net and forums proved fruitless and I had to re-format.  I assumed that my error was a misuse of sudo and chmod.

Hundreds of hours later, after re-configuring the OS from the ground up, I am again locked out.  I have not re-booted for 6 weeks as I am running Folding At Home.  

Tonight I never used sudo.  I only did a 3 MB SBackup.  But after a double check of df -h, I found to my amazement that 5 GB disappeared and df read ZERO disk space.  I then dumped a few hundred media files, but df still read ZERO disk space.  

Now I reboot and I can't even get into a terminal.  My user name and passwsord is accepted but I am re-cycled back to the log-in window with the error message:  "GDM would not write to your authorization file.  This could mean that you are out of disk space . . ."

I can't afford to waste another hundred hours starting over.  Dump Ubuntu for SUSE or replace hdd??  I am extremely frustrated.

---

### Post by dcstar on 2006-11-06
> **Kurt_Alan said:**
> **[SIZE="5"][/SIZE]**
...........
Tonight I never used sudo.  I only did a 3 MB SBackup.  But after a double check of df -h, I found to my amazement that 5 GB disappeared and df read ZERO disk space.  I then dumped a few hundred media files, but df still read ZERO disk space.  

Now I reboot and I can't even get into a terminal.  My user name and passwsord is accepted but I am re-cycled back to the log-in window with the error message:  "GDM would not write to your authorization file.  This could mean that you are out of disk space . . ."

I can't afford to waste another hundred hours starting over.  Dump Ubuntu for SUSE or replace hdd??  I am extremely frustrated.

You have run out of disk space, something may well have filled up the log files and crashed your system.

Boot up off the live CD, mount your hard disk and clear out some files to get enough space to boot normally (do a search for details on this procedure), once you do that start looking for the problem and then do a forum search for previous posts about it.

---

### Post by Kurt_Alan on 2006-11-08
> **dcstar said:**
> You have run out of disk space, something may well have filled up the log files and crashed your system.

Boot up off the live CD, mount your hard disk and clear out some files to get enough space to boot normally (do a search for details on this procedure), once you do that start looking for the problem and then do a forum search for previous posts about it.

Thanks, Dcstar.  OK, I want to boot off my live CD and mount my hard disk.  I have booted from my live CD and am at a terminal. I am just now reading wiki on* mounting and fstab*.

When I do: ```
gedit /etc/fstab
``` I get: 

unionfs /unionfs rw 0  0
tmpfs /tmp tmpfs nosuid, nodev 0  0
/dev/hda5 swap swap defaults 0  0

I do not see my ext3 partition on which Ubuntu is mounted.  

Where do I go from here?

---

