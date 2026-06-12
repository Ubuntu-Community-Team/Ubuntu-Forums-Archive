---
title: "Quirky partition question"
date: 2008-06-28
forum: General Help
---

### Post by Shane10101 on 2008-06-28
Hi.  I'm running U Hardy 64bit from a fresh install.  When I partitioned my hard drive, I wanted to use a separate large partition (on a different drive, though that seems irrelevant) as a photo archive.  So, I have:

/boot on a partition on hard drive A
/ [root] on a partition on hard drive B 
/home on a second partition on hard drive B
and 
/home/shane/photos on its own partition on hard drive C

Everything's working peechy, but I can't figure out why the partition that /home/shane/photos is on shows up on my desktop, as though it's not one of the normally-mounted volumes.  None of the other partitions do this; just CD's & key drives & the like.  

Do I have something set wrong in my partition table that's causing this strange behavior?!  It's only slightly annoying; but my curiosity for learning about all things linux is getting the best of me.  ;)

Someone enlighten me, please.

Thanks!

Shane

---

### Post by p_quarles on 2008-06-28
How is this drive connected? Are drives A and B physically separate drives, or are they just different partitions?

There are a couple of ways to get rid of such icons, if that's what you're after. The "why" is, I believe, just the way that Gnome treats volumes that it doesn't consider to be part of the essential filesystem structure.

---

### Post by Shane10101 on 2008-06-29
Thanks, p!  I'm glad you asked -- I double-checked, and found that I got it backwards when I explained it:

/[root] and /home/shane/photos are different partitions on the same drive; /home (and thus /home/shane) are in a partition on a separate drive.  

So as for the "why", Gnome would display an icon for any partition designated for use outside the standard fs structure?  I didn't realize that.  (I guess I've never set aside a partition for anything that specific.)

So how do I go about getting rid of the icon?  

Thanks Again,

Shane

---

### Post by lswb on 2008-06-29
Surprisingly (to me anyway) one way to keep these icons from appearing on the desktop or in the nautilus sidebar is to mount them at boot in /etc/fstab.

---

### Post by Shane10101 on 2008-07-03
hmm.  It is mounted at boot.  Here's the line from fstab.  Do you guys see anything here that would make it appear on the desktop anyway??

# /dev/sda4
UUID=70862de0-5bdb-455c-9c77-eb7d00c626cd /home/shane/photos xfs     relatime        0       2

---

