---
title: "Which application is using the disk?"
date: 2008-05-08
forum: General Help
---

### Post by soofsoof on 2008-05-08
Hi all,

I would like to monitor which application is using the disk, and have some king of a measure like "cpu usage". I am not talking about disk usage in terms of space occupied. I sometimes see that the disk is working hard with no obvious reason and I would like to know which application causes that.

Do you know of any application (preferably command line) which does that?

---

### Post by Patb on 2008-05-08
Soof, perhaps you could try "gnome-system-monitor".  You might also wish to install and look at conky, a lightweight but highly configurable system monitor.  You may need to search for the many config options - there is a small army of conky enthusiasts out there. 

Cheers, Pat.

---

### Post by Choad on 2008-05-08
it's most likely tracker. if you are using hardy, there should be a little magnifying glass in the system tray. right click on it and press "pause all indexing" and see if the activity stops

if it does, then you can re-enable it. tracker works with only the unused resources of your computer so you don't need to worry about it too much. it makes searching for your files instant 

if it's not tracker...take a look at system monitor and at the memory and swap usage. what's that like?

if you have < 256 mb memory you may just be going a bit swap happy (when your computer runs out of memory and "swaps" the information on to the hard disk)

---

### Post by soofsoof on 2008-05-08
Thanks a lot for the answers!

Conky is great. Almost what I needed (I cannot sort apps by disk usage, but still nice).

Tracker is disabled, but I have google desktop, and this is what's using the disk.

Thanks again.

---

### Post by Whiffle on 2008-05-08
if you do

sudo  echo 1 > /proc/sys/vm/block_dump 

it will dump what is using what to dmesg.  Just run "dmesg" to see it.

---

