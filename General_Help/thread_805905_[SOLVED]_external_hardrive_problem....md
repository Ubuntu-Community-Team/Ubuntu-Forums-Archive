---
title: "[SOLVED] external hardrive problem..."
date: 2008-05-24
forum: General Help
---

### Post by no1cares on 2008-05-24
i have a seagate, free agent external harddrive, The first
time i plugged it in it dident find it, i turned the power
off and on to the external drive and it found it and worked.
 so today i go to plug it in and it finds it but wont let me
access it, this is the error i get.

Cannot mount volume.
Unable to mount the volume 'FreeAgent Drive'.
Details:
$logfile indicated unclean shutdown (0,0) failed to mount '/
dev/sdb1': Operation not supported Mount is denied because
NTFS is marked to be in use>  Choose one action: choose 1:
if you have windows then disconnect the external devices by
clicking on 'safely remove hardware' icon in the windows
task bar then shutdown windows cleanly
Choice 2: if you dont have windows then you can use the
'force' option for your own responsibility.  For example
type on the command line: mount -t
ntfs-g/dev/sdb1/media/freeagent drive -0 force      or add
the option to the relevant row in the /etc/fstab file:      
/dev/sdb1/media/freeagent drive ntfs-3g force 0 0

ive tried restarting and unplugging the power to external
drive and different things. ad keep getting this error..

---

### Post by carl99fan on 2008-05-24
I understand you pain..

Here is MY thread. I have been working on this same thing for a while now... Still no results
BUT read some of the material in here, it MAY help you.
[http://ubuntuforums.org/showthread.php?t=796814](http://ubuntuforums.org/showthread.php?t=796814)

---

### Post by no1cares on 2008-05-24
what i dont get is that it was working, i got information off of it and its on my computer now.... just why all the sudden it stopped.... and got this error???

---

### Post by itaintover on 2008-05-24
Did you do what it said?
```
Choose one action: choose 1:
if you have windows then disconnect the external devices by
clicking on 'safely remove hardware' icon in the windows
task bar then shutdown windows cleanly
Choice 2: if you dont have windows then you can use the
'force' option for your own responsibility. For example
type on the command line: mount -t
ntfs-g/dev/sdb1/media/freeagent drive -0 force or add
the option to the relevant row in the /etc/fstab file:
/dev/sdb1/media/freeagent drive ntfs-3g force 0 0
```

---

### Post by no1cares on 2008-05-24
what does that mean??? im new...

---

### Post by no1cares on 2008-05-24
ive dont that in terminal and nothing happens....

mount -t
ntfs-g/dev/sdb1/media/freeagent drive -0 force

i think im just going to get a new one. anyone know a external hardive that works with linux

---

### Post by wthex on 2008-05-25
> **no1cares said:**
> i have a seagate, free agent external harddrive, The first
time i plugged it in it dident find it, i turned the power
off and on to the external drive and it found it and worked.
 so today i go to plug it in and it finds it but wont let me
access it, this is the error i get.

Cannot mount volume.
Unable to mount the volume 'FreeAgent Drive'.
Details:
$logfile indicated unclean shutdown (0,0) failed to mount '/
dev/sdb1': Operation not supported Mount is denied because
NTFS is marked to be in use>  Choose one action: choose 1:
if you have windows then disconnect the external devices by
clicking on 'safely remove hardware' icon in the windows
task bar then shutdown windows cleanly
Choice 2: if you dont have windows then you can use the
'force' option for your own responsibility.  For example
type on the command line: mount -t
ntfs-g/dev/sdb1/media/freeagent drive -0 force      or add
the option to the relevant row in the /etc/fstab file:      
/dev/sdb1/media/freeagent drive ntfs-3g force 0 0

ive tried restarting and unplugging the power to external
drive and different things. ad keep getting this error..
no1cares,

I just recently installed Ubuntu, and I had a usb, FreeAgent connected and have been using via winxp.

After the first time that I viewed the drive I experienced the same problem. what I ended up doing was rebooting into winxp, then restarting the computer to boot into Ubuntu.

This seemed to "fix" the problem. I dont remember for sure but I think that i tried to force the mount and it didnt work.

So, if you have a dual boot system, reboot to windows then back to Linux.

See if that works.

wthex

---

### Post by scouser73 on 2008-05-25
> **no1cares said:**
> ive dont that in terminal and nothing happens....

mount -t
ntfs-g/dev/sdb1/media/freeagent drive -0 force

i think im just going to get a new one. anyone know a external hardive that works with linux

Maxtor hard drives work with Linux, although they're now owned by Seagate, and I can say I've not had any problems with either of my external drives, just simple plug & play

---

### Post by no1cares on 2008-05-25
> no1cares,

I just recently installed Ubuntu, and I had a usb, FreeAgent connected and have been using via winxp.

After the first time that I viewed the drive I experienced the same problem. what I ended up doing was rebooting into winxp, then restarting the computer to boot into Ubuntu.

This seemed to "fix" the problem. I dont remember for sure but I think that i tried to force the mount and it didnt work.

So, if you have a dual boot system, reboot to windows then back to Linux.

See if that works.

wthex

unforntuanly i dont have duel boot- but i do have another computer with windows is there anyway i can use that computer to help???

---

### Post by poi_pounder on 2008-06-16
Another path would be to try and delete your $LogFile. And then try and mounting the External Harddrive after rebooting/reattaching. I saw the same issue with an external Maxtor and my OS X.

---

