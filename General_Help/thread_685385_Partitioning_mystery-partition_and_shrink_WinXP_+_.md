---
title: "Partitioning: mystery-partition and shrink WinXP + related questions ..."
date: 2008-02-02
forum: General Help
---

### Post by El_Belgicano on 2008-02-02
Hey guys, some partitioning questions here :)

Here's my partition configuration: "sudo fdisk -l"
```
Disque /dev/sda: 60.0 Go, 60011642880 octets
255 heads, 63 sectors/track, 7296 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2d3c2d3

Périphérique Amorce    Début      Fin      Blocs    Id  Système
/dev/sda1               1         230     1847443+  1b  Hidden W95 FAT32
/dev/sda2   *         231        4474    34089930    c  W95 FAT32 (LBA)
/dev/sda3            4475        6085    12940357+   f  W95 Etendu (LBA)
/dev/sda4            6086        7296     9727357+  83  Linux
/dev/sda5            4475        5107     5084541    b  W95 FAT32
/dev/sda6            5108        5204      779121   82  Linux swap / Solaris
/dev/sda7            5205        6085     7076601   83  Linux
```
What'd like to change:
1) **remove sda1** (never used it intentionnally, I guess even the system doesn't use it either, it just contains some files of ASUS, seems to be meant for recovering...)
2) **move sda2** to the start of the disk and **shrink** it to about 20Gig.
3) **extend sda5** to 15 Gig

My questions:
1) Isn't it better to shrink sda1 to 1Mb or something insignificant?
1b) Will removing the first partition result in a renaming of the others? 
2) Is it safe for both installations Windows and Ubuntu to do that?
3) Does someone know what's the purpose of that "mystery-partition" ?
4) Can Gparted handle all this?
5) Does someone know a program that can take an image of an entire disk to a removable HD (just in case I mess things up)

Thanks

---

### Post by LaRoza on 2008-02-02
> **El_Belgicano said:**
> 
What'd like to change:
1) **remove sda1** (never used it intentionnally, I guess even the system doesn't use it either, it just contains some files of ASUS, seems to be meant for recovering...)
2) **move sda2** to the start of the disk and **shrink** it to about 20Gig.
3) **extend sda5** to 15 Gig

My questions:
1) Isn't it better to shrink sda1 to 1Mb or something insignificant?
1b) Will removing the first partition result in a renaming of the others? 
2) Is it safe for both installations Windows and Ubuntu to do that?
3) Does someone know what's the purpose of that "mystery-partition" ?
4) Can Gparted handle all this?
5) Does someone know a program that can take an image of an entire disk to a removable HD (just in case I mess things up)


What are your goals? Are you trying to dual boot? If so, with what?

The partition that you don't seem to use is probably for system recovery.

You can use Clonezilla to make an image of the hard disk or partitions and restore with it, in case you want to undo anything.

See the link in my sig for clonezilla.

---

### Post by El_Belgicano on 2008-02-02
I'm already dual-booting (XP/Gutsy), but I got 10Gig unused on my Win partition and It will be more soon since I'll remove programs I've already found a Linux alternative for ... so I'd like to make a partition for file exchange between XP & Ubuntu out of the created space. And an extra 2Gig would also be welcome ...
Thanks for the reply...

---

### Post by LaRoza on 2008-02-02
When the recovery partition is first like that, I don't know if you can delete it. You could try it, if you have another means of restoring it.

---

