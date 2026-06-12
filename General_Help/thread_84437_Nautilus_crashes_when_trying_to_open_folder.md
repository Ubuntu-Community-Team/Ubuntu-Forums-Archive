---
title: "Nautilus crashes when trying to open folder"
date: 2005-10-31
forum: General Help
---

### Post by linbetwin on 2005-10-31
I've posted a [thread]("http://ubuntuforums.org/showthread.php?t=81522") a while ago asking for help because my Nautilus crashed whenever I tried to open a folder on a mounted NTFS partition or DVD. But now I reinstalled Ubuntu, haven't mounted my NTFS partitions yet, haven't popped in any DVD or CD yet, but Nautilus still crashes every time I try to open ANY folder!](*,) 
 
The only thing I did after installation was change my kernel form 386 to k7. Could this be the problem?

---

### Post by 23meg on 2005-10-31
[QUOTE=linbetwin]
The only thing I did after installation was change my kernel form 386 to k7. Could this be the problem?[/QUOTE]

What processor do you have? Did you try with another kernel as well?

---

### Post by linbetwin on 2005-10-31
I have an AMD Athlon XP 2200+ and I heard k7 is the right kernel for AMDs.
The only othe kernel I tried was the 386 that Ubuntu installs by default. It is still listed in Grub.

---

### Post by 23meg on 2005-10-31
Try booting with the 386 kernel and see if the same happens to narrow down the problem.

---

### Post by linbetwin on 2005-10-31
The problem is narrowed down and pinned to the ground! The k7 was the culprit. Thanks, 23meg!

So, do I uninstall it in Synaptic? Will it be completely removed from my system?

---

### Post by 23meg on 2005-10-31
If you uninstall it with apt / Synaptic, yes it will be. But I say keep it for a while and keep googling / asking around, since the K7 is a supported Ubuntu kernel, and the one that's optimized for your processor.

---

### Post by 23meg on 2005-10-31
Things you can do to see what exactly is going wrong with the K7 kernel:

- Replicate the crash, note the exact time it occured, fire up the gnome system log tool (gnome-system-log) and see what's reported in each of the logs at the time the crash occured. 

- See if Nautilus still crashes when you run it as root.

- Start a failsafe Gnome session and see if you can replicate the crash there as well.

---

### Post by SreckoMicic on 2006-04-05
I have the same problem, this ubuntu version works fine for couple months and then Nautilus just started to crash whenever I try to open document. but if i'l loged as root everything just works fine.
Please Help this is driving me crazy.

---

