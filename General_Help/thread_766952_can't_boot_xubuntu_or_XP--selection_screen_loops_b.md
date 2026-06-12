---
title: "can't boot xubuntu or XP--selection screen loops back to startup"
date: 2008-04-25
forum: General Help
---

### Post by Sorandal on 2008-04-25
I originally posted in the beginner forum, but I think this may be related to Wubi.

Okay, so I have Xubuntu installed on a laptop running XP. I installed Xubuntu with wubi. Yesterday both were working fine, today I was using Xubuntu, and I restarted my computer. It did not shut down properly, the screen went white and froze (this has happened before). I held down the start button to turn off the computer and restarted it. It loaded the menu that lets me select either ubuntu or windows XP. If I select either one it loops back as if the computer were just turned on and loads the menu for selecting ubuntu or XP again. I pressed F8 and tried the safe mode menus, but it takes me back to the ubuntu/XP selection screen and loops back if I select one. Right now I'm running from the Ubuntu live CD. I'm at a bit of a loss as to what happened and what to do about it. The only idea I have for what happened is that maybe something to do with wubi could have been corrupted when it crashed.

The advice I got from a link in the beginner forum was to [https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a) and follow the section on: How can I access my Wubi install and repair my install if it won't boot?

It says:
Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein...


How do I find the partition number and disk letter?  my drive is not partitioned, so I would think it would be 0 or 1.

---

### Post by ago on 2008-04-25
run chkdsk /r from windows

---

### Post by Sorandal on 2008-04-25
Ago, is there any way without going into windows?  I don't have a boot disk.  I could borrow a copy of XP, but it isn't registered to me, so I don't know if I can boot off of it.

---

### Post by ago on 2008-04-25
yes you can boot off it and go into recovery console

---

### Post by mdkaneda55 on 2008-04-26
yeah, running "chkdsk /r" from a windows command prompt should help, but be warned, because u installed via Wubi, your running in a ntfs non-journalized filesystem, so you may have actually lost some of your data by doing the hard reset... I've lost quite a bit of data on fat32 partitions in the past because of kernel crashes, and it really bites. hehe. 
anyways, to answer your other question about your drive letter / partition #... it most likely is /dev/sda1, but u can check on the ubuntu live cd in a terminal..  "sudo sfdisk -l", it's probably the only partition u have =) if ur still not able to boot after running the disk error check, atleast u can recover some data this way.

---

### Post by Sorandal on 2008-04-27
Well I wasn't able to boot into XP off of the disk, because I was dumb and bought this computer from someone who didn't know the admistrator password.  For some reason my computer magically fixed itself, and now it boots into either OS just fine.  I guess I should find a way to reset the password while everthing is working.  I ran chkdsk /r from windows, and it said the drive was in use but it could run it on startup.  The results in startup flash up for about a second and then it boots up, no chance to read them.  I guess it would work if I were booting from a CD though since the drive would not be in use.  mdkaneda55, that worked, and you were right, thanks, Good to know in case this problem comes back later.

---

