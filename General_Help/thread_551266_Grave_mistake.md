---
title: "Grave mistake"
date: 2007-09-14
forum: General Help
---

### Post by fascigo1618 on 2007-09-14
I am a noob to ubuntu, and linux for that matter, I am running 6.10 currently and had a folder permissions issue. So i googled it and found a post saying that i should go to the terminal  and type "gksudo nautilus"
which opened a folder browser, with me as root. anyway i was stupid enough to go to filesystem, select all, right click, go to properties and set all permissions to allow me to do everything, afterwards every thing could not open, icons were different or the red "x". after all this i restarted thinking, it needed one(windows corrupted me) and it gave me the following error:

   BusyBox v1.0.1 (Debian 1:0.1.3-2ubuntu3) Built in shell (ash)
   Enter 'help' for a list of built-in commands.

   /bin/sh: can't access tty; job control turned off
  (initramfs)

what do i do?

---

### Post by MrFSL on 2007-09-15
WOW! :eek::-o

I'm not going to lie... reinstall.

I know that this is not a helpful post. ... We all did things like this when we started out. It's all great learning.

---

### Post by rsambuca on 2007-09-15
Wow, to get things back to the normal working state, you would have to go through all of the folders and change the permissions back to what they need to be.  I am afraid I agree that a reinstallation would probably be easiest.

---

### Post by OoooMatron on 2007-09-15
> **rsambuca said:**
> Wow, to get things back to the normal working state, you would have to go through all of the folders and change the permissions back to what they need to be.  I am afraid I agree that a reinstallation would probably be easiest.

:lolflag:

---

### Post by fascigo1618 on 2007-09-15
unfortunately reinstall not an option. too much important stuff on and cant shift it how do i change permissions back to root. currently i am attampting livecd. then doing what i done select all right click and change permissions look at it this way i CANT MAKE THING WORSE.(i hope)

---

### Post by fascigo1618 on 2007-09-15
scratch that that dont work now what??

---

### Post by jocko on 2007-09-15
You'll probably have to find out and set the correct permissions for every single file separately. That will take weeks. The quick and easy way is to reinstall.

---

### Post by peabody on 2007-09-15
> **fascigo1618 said:**
> unfortunately reinstall not an option. too much important stuff on and cant shift it how do i change permissions back to root. currently i am attampting livecd. then doing what i done select all right click and change permissions look at it this way i CANT MAKE THING WORSE.(i hope)

You can attempt a reinstall without formatting.  You might still have some problems on bootup, but it'll keep its hands off of /home anyway, which is where I take it your user data is correct?

You did keep your important data in /home...correct?  Not other parts of the filesystem?

---

### Post by mojoman on 2007-09-15
> **fascigo1618 said:**
> unfortunately reinstall not an option. too much important stuff on and cant shift it how do i change permissions back to root. currently i am attampting livecd. then doing what i done select all right click and change permissions look at it this way i CANT MAKE THING WORSE.(i hope)

Back-up your personal data on DVD or CD. Do you by any chance dual-boot? If so, you can boot up into your other OS and burn the files from there. If not, you might consider removing the HDD and connect it to another computer and then back-up all your personal files. A third option might be to use a live CD to resize your HDD partition to make room for another partition and make a fresh install on the new partition and then make a back-up from there.

But when it comes to the old install, my guess is that the filesystem is beyond repair and you'll have to re-install your OS.

In the future I recommend that you have your /home on a separete partition. I myself have two users on my computer which each have a folder in /home and I also have five or six shared folders in /home (for music, movies etc) which belong to a group both users a members of. All of this resides on a seperate partition. That way, I can f**k up quite a lot (and I do every now and then) without losing my personal files or favorite configurations.

---

