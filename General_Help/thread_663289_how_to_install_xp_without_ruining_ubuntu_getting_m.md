---
title: "how to install xp without ruining ubuntu getting missed up??"
date: 2008-01-10
forum: General Help
---

### Post by jcer93705 on 2008-01-10
Hello, well I am dual booting on my laptop. My laptop is running great in ubuntu. But xp i'm having trouble. I would like to reformat my window partition and fresh install but i don't want to loose ubuntu. How can i do
that?

---

### Post by aquavitae on 2008-01-10
First, make backups.  You should be able to reinstall windows without affecting ubuntu, but I never trust the windows installation.  As far as I rememeber, you can format the partition windows is on (either using the windows installation cd or from ubuntu), then just install windows, making sure to select the right partition to install to. Windows will wipe out the grub boot manager, so you'll have to reinstall that as well.  The easiest way to do that is probably to use the [SuperGrub Disk]("http://supergrub.forjamari.linex.org/"), but there are also plenty of guides on the internet and these forums for reinstalling grub.

Hope this helps!

---

### Post by jcer93705 on 2008-01-10
Thank you for answering and how do i make backup? And backup of what? I already downloaded super
grub disk, hopefully tomarrow i'll burn it with nero and start installing xp. :) hope i don't missed up
my ubuntu. Anyways backing up ubuntu partition by backing up just folders i have of pic and such
or the whole system files as well?

---

### Post by zionpsyfer on 2008-01-10
I believe he means that you should back up all of the important files in ubuntu that you don't want to lose (just in case).   Pictures, music, etc.  Just burn the stuff you want to keep no matter what to a cd/dvd or another hard drive, etc.  


Better safe than sorry when it comes to stuff like that. :)

---

### Post by ozorba on 2008-01-10
If you have a separate partition for Ubuntu it gives you less headache. However, if you have not partitoned your HDD then you will loose your ubuntu all together. 

If you have a different partition for XP ensure that you install it to the correct one. After the installation of XP you will need tthe Ubuntu CD to restore GRUB. Make sure that you know which partitons your linux and XP are on (hda1, sda1 etc). You will need this when restoring GRUB.

---

### Post by dcstar on 2008-01-10
> **jcer93705 said:**
> Hello, well I am dual booting on my laptop. My laptop is running great in ubuntu. But xp i'm having trouble. I would like to reformat my window partition and fresh install but i don't want to loose ubuntu. How can i do
that?

Have you considered Virtualisation?, I run XP inside of Ubuntu in VMware server, that way I can run both simultaneously (if I need to).

Dual booting is so early 21st Century.....     ;-)

---

### Post by jcer93705 on 2008-01-10
dual booting works best for linux and for windows. Why people dont say that to ubuntu, have u tried
ubuntu in vmware. LOL we wont run it in vmware because? It just sucks to use any os under another
os. I play games, and i want full os running fast, not slow. I've been using vmware for almost
10 years. Maybe I would install vmware someday in ubuntu but i just having problem on doing
so and that virtual box is not working neither. But for now, its very important to run xp without
running under linux os lol. I use xp for gaming and stuff, even though i do play games under linux. 
Yes i tried that wine program, still use it, not for games though. I can play halflife 2 in it, but i wont.

---

