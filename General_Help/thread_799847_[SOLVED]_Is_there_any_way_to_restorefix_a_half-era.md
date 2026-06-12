---
title: "[SOLVED] Is there any way to restore/fix a half-erased Ubuntu partition?"
date: 2008-05-19
forum: General Help
---

### Post by DayOldPorridge on 2008-05-19
It was sort of my own mistake; I had mounted /dev/sda3 onto the /tmp directory in my Yoper partition, and had forgotten that the system empties out /tmp at shutdown.  Luckily, the /home directory and a few others are still on /dev/sda3, but /boot, /bin, and some others have gotten deleted, so I can't boot back into it.

I would've made a backup, but that would've meant squeezing a sixth partition on here, and unfortunately I don't have an external hard drive yet.

Is there any kind of restore CD that can re-add missing system files?

---

### Post by DayOldPorridge on 2008-05-19
Bump.

---

### Post by mahuyar on 2008-05-19
Why can't you just reinstall it?  You'll just have to tell the installer where your /home partition is located along the way, and things should be back in business as usual.  :D

---

### Post by DayOldPorridge on 2008-05-19
Hmm.  It wouldn't overwrite the existing /home directory?

---

### Post by mahuyar on 2008-05-19
> **DayOldPorridge said:**
> Hmm.  It wouldn't overwrite the existing /home directory?

On a second thought, do you have your /home on a separate partition?

EDIT:  Otherwise, it won't work, unless you have it on its own partition.

---

### Post by DayOldPorridge on 2008-05-19
No, but that's a good idea.

I'll just copy all the directories to another partition, and then reinstall Hardy on sda3, and then copy the old directories back onto the reinstalled partition.

I could just as easily put my directories on sda2, but I'm not sure if some system files (such as those in /root, or /initrd) point to /dev/sda3 specifically.

EDIT: Nevermind, I'm just gonna copy /home onto sda2.  It makes things easier.  xD

---

### Post by mahuyar on 2008-05-19
Why would you want to copy back your /home partition back into /sda3 ?  If you choose to install Hardy into /dev/sda3, have your /home on a different partition.  So, if you make a mistake like today, you'll just have to reinstall the OS into /dev/sda3 again, and along the way, tell your installer where your /home partition is.  Just make sure it is not to be formatted.

Hope this clears up a bit.

EDIT:  You can just leave /root in /dev/sda3 together with the rest of the installation.

---

### Post by mahuyar on 2008-05-19
> **DayOldPorridge said:**
> 
I could just as easily put my directories on sda2, but I'm not sure if some system files (such as those in /root, or /initrd) point to /dev/sda3 specifically.

EDIT: Nevermind, I'm just gonna copy /home onto sda2.  It makes things easier.  xD

As long as you choose to install "/" into /dev/sda3, all those will be taken care of automagically...  that includes /root, /boot, /etc, /var, etc.

Just your /home is an exception here.

---

