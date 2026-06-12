---
title: "What kind of partitioning scheme is that ?"
date: 2014-01-26
forum: General Help
---

### Post by iulian X on 2014-01-26
Recently I saw on notebook this  partitioning scheme can you tell me if there is something wrong.

[B]/dev/mapp/  [COLOR=#ff0000]? [/COLOR]        EXT4
/dev/sda2/boot                  EXT2 [COLOR=#ff0000]?                 [/COLOR](i use this kind of partition but not ext2, why did they use EXT 2 and not EXT3 or EXT4 ?)
/dev/sda1/boot/efi  [COLOR=#ff0000]?[/COLOR]           Vfat  [COLOR=#ff0000]?[/COLOR][/B]




[IMG]https://dl.dropboxusercontent.com/u/17279480/%3F/20140106_110644.jpg[/IMG]

---

### Post by CharlesA on 2014-01-27
Probably because you are using LVM with /dev/mapper/something mounted as root (/). If you use LVM, you need a separate boot partition, which is usually ext2 because it doesn't need jounalling.

---

### Post by iulian X on 2014-01-27
This is not my notebook, i saw that partitioning scheme on those notebooks [http://ubuntuforums.org/showthread.php?t=2199524](http://ubuntuforums.org/showthread.php?t=2199524)

I have never installed Ubuntu a the notebook ( with or without UEFI ) so I want to learn if ever I will have do it to know how to do it and not embarrass me .

This is my partitioning scheme on SSD ( i have the swap partion on the HDD ) :

[IMG]https://dl.dropboxusercontent.com/u/17279480/%3F/tabela-partitii.png[/IMG]

---

### Post by Bashing-om on 2014-01-27
iulian X; Hi !

Your present partitioning scheme is OK but,
With this caveat :
There should exist extenuating circumstance to use a separate /boot partition (say UEFI or GPT partitioning schemes).
However, sharing /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything. That said; At this time there is no need to  repartition the disk from scratch.
&&

If you want to install GRUB2 to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector.

[INDENT][INDENT]I think that says it all
[/INDENT][/INDENT]

---

