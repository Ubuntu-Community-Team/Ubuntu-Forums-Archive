---
title: "Partioning Problems"
date: 2007-10-06
forum: General Help
---

### Post by -Stevey-Wonder-1990- on 2007-10-06
Ok here's my dilema, i want to dual boot windows with linux... i have a reasonable old computer and would like to run Windows 98, Xubuntu and perhaps Puppy/DSL. I have a 30GB hard drive, how would you go about partioning this harddrive? How much space would need allocated to each OS? I have 192MB RAM although i dont think this is important?!

Thanks

---

### Post by SpiritIsReality on 2007-10-06
howdy
I've done a bit of this but am no expert., by a long shot.
I'd install micsoft first off.(no I wouldn"t)
then get a gparted live cd here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
then partition the disk so it has 5GB partition for each os. and a swap partition of 1 or 2 times the size of ram, to a max of 2GB?
you could make a small fat 32 partition so you could swap files back and forth from micsoft and linux.
the rest ext3 /data partition
something like this
hda1 5GB Windows98
hda2 5GB puppy
hda3 5GB Empty
hda4 extended partition meaning from here to end of hd including all the logical partitions that follow.
hda5  400MB swap
hda6 1GB Fat 32
hda7 5GB Ubuntu
hda8 rest of disk Data
install w98,
if you install ubuntu last, Xubuntu, you shouldn't have to read too much of this
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)
[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)
[http://www.google.ca/search?hl=en&q=grub+booting+100+os+howto&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=grub+booting+100+os+howto&btnG=Search&meta=)
UUID's are a pain in the butt, in the /etc/fstab. it used to be just /dev/hd__ easy. I think debian is still like that? but if you get into trouble with changing partitions around and grub can/t boot ubuntu because some partition has changed. post the question to this forum. or search for an answer. sometimes just comment out the partition that ubuntu wants to auto load, but has changed...best to not automount once you know what you're doing?
there's a tutorial on the forum about /etc/fstab or it's called something fstab I'd have to look for it.

buds

---

