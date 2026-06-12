---
title: "change hard drive name"
date: 2006-10-12
forum: General Help
---

### Post by rhuarch on 2006-10-12
I just installed ubuntu on a computer with 3 hard drives.  One of them I got a chance to name during the liveCD install.  I have managed to mount the other 2 drives, but when they show up in /system:media they have really generic names.  Does anyone know if there is a way to change those names permanently?  I thought they would adopt the names of the folders I mounted them to, but apparently that is not the case.

Thanks,
Grah

---

### Post by encompass on 2006-10-12
Just to tell you, you can mount anything as anything from almost anywhere.  That is something cool about linux.
You can make a new directory in the media folder. (or where ever you want).
Then look at your fstab file, this file, located in /etc/fstab.
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Notice the old drive that would want mounted is looking at the old directory, with the aperently bland name.
Just change the directory with the new one that you have made.  Should work from there.

---

### Post by rhuarch on 2006-10-12
Thanks for the quick reply.  I looked in the fstab file and here are what I "think" are the applicable lines.
 
 /dev/hdd1 /mnt/FireTree ext3 users,atime,auto,rw,nodev,noexec,nosuid 0 0
 /dev/hdc1 /mnt/BlackHand ext3 users,atime,auto,rw,nodev,noexec,nosuid 0 0

What I thought would happen was that my drives would be named FireTree and BlackHand respectively but they aren't for some reason.  Maybe there is a line I can add to insert a label?  Btw I am an EXTREME noob here.  Tonight is the first time I have ever actually used Linux and I am diggin it. :D My plan is to use this machine as a fileserver on my network (hence 3 hard drives) and the label thing is purely a vanity, but I want to figure it out nonetheless.

Thanks,
Grah

---

### Post by encompass on 2006-10-12
"I bet you think this song is about you..." :P
did you make a FireTree directory?
> sudo mkdir /mnt/FireTree
That will make it for you.
The reboot and see if it worked.
What did it say before?

---

### Post by lobtoc on 2006-10-29
> **rhuarch said:**
> I just installed ubuntu on a computer with 3 hard drives.  One of them I got a chance to name during the liveCD install.  I have managed to mount the other 2 drives, but when they show up in /system:media they have really generic names.  Does anyone know if there is a way to change those names permanently?  I thought they would adopt the names of the folders I mounted them to, but apparently that is not the case.

Thanks,
Grah

Hi!

I had the same "problem" and couldn't find a way to change the names (or labels) of hard drives / partitions in Ubuntu.
Now I just noticed that, when I change those names in WinXP-Explorer (I have Windows and Ubuntu in my machine), they get the same names in Ubuntu, too!
For example I have "WINXP" for C:\ (hda1), "FAT32" for D:\ (hda3), ...

Ubuntu seemed to recognize the changes I made in Windows and adopted it.
This works for me now, but what if one hasn't an extra Windows installed?

Maybe someone with more experience could explain this, please!

Greetings,
lobtoc

---

