---
title: "Root password not recognised"
date: 2006-10-27
forum: General Help
---

### Post by jude999 on 2006-10-27
I was in the middle of the upgrade to Edgy when I did smth wrong and quit the upgrade. I tried to re-launch it but when I type my pw in Updade Manager, It says wrong pw. I know I have the right pw.

What's wrong? What should I do?

---

### Post by black_rob on 2006-10-27
If you have a live cd handy, like knoppix or grml, something that logs you in as root, boot it up.
Mount your ubuntu disk partition somewhere: I usually go "mkdir /mnt/ubuntu && mount /dev/hd? /mnt/ubuntu", with replacing hd? with whatever your ubuntu partition is (like hda1).  
Then "chroot /mnt/ubuntu", then "passwd".  This lets you update your root password.  Exit out of the chroot, "umount /mnt/ubuntu", reboot and your new password should work.

---

### Post by beanfoto2 on 2006-10-28
I installed hoary hedgehog,(I only have 128Meg on this College machine,so the Dapper Drake Live /Install CD is a no no for me, as it requires 256 Meg). I found the root password screen less than user friendly, as in my case it didn't even show me the number of characters I've typed. On Chinese keyboards the character repeat is usully set at a very fast rate, as they're usually only used for online games. 
Anyway, I carried on and Ubuntu did fully install, problems will come later with specific sotware I'm sure, it always has on my other Linux installs. However, the first time I tried to use anything from the W.I.M.P. side of things it told me "Incorrect password.
So I reinstalled, tried again, and...
So I re installed tried again and...
I won't repeat myself too much, but this is the third reinstall.
This time I also tried being brave, opening a terminal and su ing.
That worked!
My linux installs are widely spaced, I have yet to get an installation that worked well enough for me not to lose patience and remove Linux after a few weeks. 
So, my knowledge is patchy, and easily obscured by the effort of trying to convince Chinese students theat because something is done THIS way in China, the rest of the world does NOT have to automatically follow suit.
Am I dong anything wrong? Why is this happening? What do I do about it?
Oh yes, and how do you mount the Windows partitions in Gnome? KDE was so much more familiar.
I'm dowenloading Kubuntu 6 thingy as we speak. Is that about to make unrealistic memory demands on me too?

---

### Post by galileon on 2006-10-28
get the -alternate version, they work on low mem systems

---

### Post by aysiu on 2006-10-28
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) might help.

---

