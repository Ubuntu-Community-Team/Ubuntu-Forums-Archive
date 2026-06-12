---
title: "This is getting annoying...(rezising partition)"
date: 2008-04-30
forum: General Help
---

### Post by jorgecarrillo150990 on 2008-04-30
Well, I want to resize my XP partition in order to install Hardy.
When I use the Live CD's GParted, it opens one big partition. Then I click Resize/Move but when I try to resize it, it just doesn't move! Then the up/down buttons are greyed out so I can't resize it that way.
Finally, I clicked on Install, and in the Partitioning Step I just get two options: 
Guided with using my whole HD 
Manual (which is also useless since I can't edit my partitions.

This is getting way to annoying since I want to dual-boot XP and Hardy, with Hardy as my main OS.

Please, I need some help.

---

### Post by johnn1949 on 2008-04-30
Try the alternate install cd.  I'm pretty sure it has an option to resize windows partition and use unallocated space for install.

---

### Post by jorgecarrillo150990 on 2008-04-30
where can I find that CD?
where do I download it?

---

### Post by johnn1949 on 2008-04-30
go here:[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

choose a site near you, there will be live cd, server download, and below that alternate install download.

The alternate usually works better than the live cd anyway.

---

### Post by louieb on 2008-04-30
GParted is pretty safe when it come to resizing also its very slow. It's also picky. Make sure to defrag your windows drive before trying to shrink it. It doesn't hurt to clean up you window partition. And then run chkdsk you want to make sure your windows partition is in the best shape it can be before trying to shrink it.

---

### Post by johnn1949 on 2008-04-30
Might as well check these out first.

xp + hardy

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

prepare for install

[http://www.users.bigpond.net.au/hermanzone/p17.htm](http://www.users.bigpond.net.au/hermanzone/p17.htm)

---

### Post by SlalomMan on 2008-04-30
Yeah, I would recommend what Louieb said. You're running XP, so the defragger is pretty good. I would run it a few times until it is completely white on the right hand side of the partition (in the XP defragmenter). If you can't do that, I would probably try to get rid of large files...otherwise, you might be out of luck.

---

### Post by the8thstar on 2008-04-30
Windows XP has a built-in tool to create, edit and resize partitions. It's much safer to use it than fiddling with gparted. This way you won't erase any vital hidden files XP laid around the disk.

Check this link for a quick how-to: [http://www.d-silence.com/feature.php?id=246]("http://www.d-silence.com/feature.php?id=246")

Hope it helps.

---

### Post by SlalomMan on 2008-04-30
I thought that XP's partitioner was destructive...I know Vista's works fine (the one thing they did right).

---

### Post by forrestcupp on 2008-04-30
Either unmount your drive while using the Hardy LiveCD, or try the [GParted LiveCD](http://gparted-livecd.tuxfamily.org/).  It's made specifically for that and it doesn't mount any of your drives when you boot to it.

---

### Post by jorgecarrillo150990 on 2008-05-01
Ok, I have used everything in this forum, but still I get no help, using GParted, alternate CD and even SystemRescuer CD I cant resize my XP partition. 
I remember that when I installed XP i told my PC to use the whole hardrive, so I think that is why I can't resize that partition...
When I use GParted, Live CD's and everything, when I get to the edge of the partition to drag it and resize it won't do anything.
Also the buttons that are below the bar are greyed out so I can't change it either.
Maybe I should reinstall XP, but now I will create an special partition for it during the installation and then installing Hardy in the other partition, what do you think?

---

### Post by joshsmith on 2008-05-01
run a full scandisk on windows too (the one that does 3 stages)

when you are running the ubuntu installer, can it work out how much free space you have oon the ntfs drive?

---

### Post by sweeneytodd on 2008-05-01
maybe "partition magic"

---

