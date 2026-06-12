---
title: "Re-organising partitions"
date: 2006-10-17
forum: General Help
---

### Post by falcon15500 on 2006-10-17
Hi all,

  Looking for some feedback.  Initially upon installing Ubuntu, I went for a dual boot scenario with WinXP already installed on the first partition on the drive, Ubuntu second (swap last).  Now that I have mirrored my XP setup over into a VMWare virtual machine I don't need the physical partition anymore and want to reclaim the space.

  As the Xp partition is first on the drive, I can't just wipe it and grow my ext3.  I also don't really fancy re-installing as I have got things 'just so'.

  What I am thinking of doing is, wiping the xp partition and reformatting it as ext3.  I will then mirror my Ubuntu drive across to it (they are the same size).  Once _everything_ has been mirrored across I will chroot to the old xp partition and re-install grub to boot from there.  Once that is working I will delete my old Ubuntu partition and either grow the remaining partition to the whole disk size (minus swap), or possibly go for  a / + /home setup.

Any problems I should be aware of?

falc

---

### Post by Sef on 2006-10-17
Why not use [GParted]("http://gparted.sourceforge.net/livecd.php") and resize the partition?

---

### Post by aysiu on 2006-10-17
I have a better idea.

Why not reformat your XP partition as Ext3 and make that new Ext3 partition your /home partition?

Then you don't have to move your Ubuntu drive over--just your /home folder.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do want to move Ubuntu over:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by falcon15500 on 2006-10-17
> **aysiu said:**
> Why not reformat your XP partition as Ext3 and make that new Ext3 partition your /home partition?

Ahhh... Yes.  Of course.  Of all the things I have lost, I miss my mind the most. ;)  Thanks for the head-slap!  That's exactly what I will do.

Cheers,

falc

---

### Post by aysiu on 2006-10-17
Post back if you run into any problems.

---

