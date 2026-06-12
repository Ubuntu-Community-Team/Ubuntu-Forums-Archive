---
title: "Grub after WinXP install"
date: 2005-05-12
forum: General Help
---

### Post by shmk on 2005-05-12
Need a little hand (or a big one):
I had a disk with Ubuntu + Winxp and grub in the mbr and all was well. I had to reinstall winxp and after that grub disappear.

The question is:
"In this condition is there a method to recover grub, or make win found ubuntu, without reinstalling one of 2 os ?"

Thx

---

### Post by defkewl on 2005-05-12
It should've been WinXP first then Ubuntu.

I think WinXP took over grub from the mbr

---

### Post by el000 on 2005-05-12
You don't need to reinstall. Check this:

[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

Hope this helps.

---

### Post by bigbangbigbigbang on 2005-05-12
[QUOTE=shmk]Need a little hand (or a big one):
I had a disk with Ubuntu + Winxp and grub in the mbr and all was well. I had to reinstall winxp and after that grub disappear.

The question is:
"In this condition is there a method to recover grub, or make win found ubuntu, without reinstalling one of 2 os ?"

Thx[/QUOTE]

1. Boot from knoppix with knoppix 2
2. mount your linux partition by hand: mount /dev/hda? /mnt/hda?
3. go into your linux partition: cd /mnt/hda?
4. If you have several linux partitions mount at least the partition containing your /usr into the usr folder within this root partition
5. Run chroot . (do not miss the . at the end) This makes your current folder (your mounted ubuntu partition) to your root
6. Type mount -a
7. Type mount proc -t proc /proc
8. Run grub-install /dev/hda (without a partition numer) this reinstalls grub into the mbr
9. Edit /boot/grub/menu.lst and make sure that your Windows partition is included
If your windows partition is your first one (/dev/hda1), than write the following to the end of this file:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

10. Leave your chroot with exit
11. Reboot your computer

---

### Post by DutchLau on 2005-05-12
I agree with el000, you don't need to do all the complicated stuff bigbangbigbigbang is telling you to do. Just follow the steps of the Ubuntu guide and you'll be back on your feet in no time. Let us know once you've fixed your problem!

Greets,

DutchLau

---

### Post by shmk on 2005-05-12
[QUOTE=DutchLau]I agree with el000, you don't need to do all the complicated stuff bigbangbigbigbang is telling you to do. Just follow the steps of the Ubuntu guide and you'll be back on your feet in no time. Let us know once you've fixed your problem!

Greets,

DutchLau[/QUOTE]
 Thanks. All resolved 
:)

---

### Post by DutchLau on 2005-05-12
Good to hear! Happy "Ubuntuing!" 

Cheers,

DutchLau

---

