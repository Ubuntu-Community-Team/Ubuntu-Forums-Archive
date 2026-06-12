---
title: "Please help!"
date: 2007-04-28
forum: General Help
---

### Post by toothe on 2007-04-28
So I've installed Ubuntu (on a partition of the hard disk named c:/) , but I've also had Windows XP on the same hard disk but on another partition (G:/). Now the problem is, when the computer boots, it automatically runs Ubuntu and I can't choose whether I want to run Ubuntu or Windows XP. I really don't know how to fix this so any help would be greatly appreciated.

---

### Post by lw5 on 2007-04-28
I'd be easier to help you if we would know what your /boot/grub/menu.lst looked like. Perhaps posting your partition table is a good idea as well.

---

### Post by toothe on 2007-04-28
Thank you.

The partition table (in french) :

Disque /dev/hda: 61.4 Go, 61492838400 octets
255 têtes, 63 secteurs/piste, 7476 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        1147     9213246   83  Linux
/dev/hda2            1148        7475    50829660    f  W95 Etendu (LBA)
/dev/hda5            1148        1274     1020096   82  Linux swap / Solaris
/dev/hda6            1275        7475    49809501    7  HPFS/NTFS


The menu.lst file :


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=795cb590-2cec-4b77-b49f-bcfb945effb7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=795cb590-2cec-4b77-b49f-bcfb945effb7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professionel
rootnoverify	(hda0,5)
makeactive
chainloader +1

Because the NTFS partition is mounted on the hda6 partition. I tried every single combination of :
map
rootnoverify
root
chainloader +1
makeactive

but it never boots xp, instead gives error messages like "error while parsing number", or "invalid drive requested", etc...

I also tried to dual boot using GAG, which doesn't work either, it detects the xp partition but when I select it, I only have a black screen and nothing happens.

Thank you

---

### Post by toothe on 2007-04-28
bump

---

### Post by Bigbluecat on 2007-04-28
I'm not sure that this is solvable. Windows is quite inflexible and likes to be on the first partition.

By all means search for some more info but I think you need to have windows on the first partition and Linux and any other partitions (it is much more flexible and does not care where it is).

---

