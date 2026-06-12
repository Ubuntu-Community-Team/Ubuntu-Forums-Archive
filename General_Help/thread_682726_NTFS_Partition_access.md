---
title: "NTFS Partition access"
date: 2008-01-30
forum: General Help
---

### Post by Flanker37 on 2008-01-30
I have decided to try my dads computer out on linux.  I tried putting ubuntu 7.10 but it would'nt have anything to do with it.  So i tried PC Linux OS instead.  that went on great.  and my dad likes it.  Using Amule, the linux version of emule however caused some problems.

All the stuff he has saved on the second disk whilst in windows, now wont let him save to it whilst in PCLinuxOS.  So i decided i might try and stick ubuntu studio on and see if that works.  And it did.  However, amule will not save to that hard drive, saying that we do not have the access right to use this drive.

How can we get it to work.  Because it isn't a matter of just changing the drive options as far as i can see.

---

### Post by orbish on 2008-01-30
The easiest method would probably be to install ntfs-3g

sudo apt-get install ntfs-3g

Easiest way to configure it would be to use ntfs-config

sudo apt-get install ntfs-config

Find ntfs-config from System Tools > NTFS Configuration Tool
Check "Enable write support for internal device" and click ok

Now you might be able to avoid a reboot at this point by just doing
sudo mount -a

Try creating a folder on the NTFS drive to try it out.  If this doesn't work, give the machine a reboot and let me know if this helped.

---

