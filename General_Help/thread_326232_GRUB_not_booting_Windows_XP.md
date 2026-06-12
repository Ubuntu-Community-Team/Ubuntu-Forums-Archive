---
title: "GRUB not booting Windows XP"
date: 2006-12-27
forum: General Help
---

### Post by jamadagni on 2006-12-27
My GRUB is not booting Windows. In my device.map, hd0 = sda and hd1 = hda. Windows resides on hda1. GRUB is on sda and /boot/grub is on sda8. My menu.lst has:

title Windows XP
    chainloader (hd1,0)+1

Do I need to use "map" in GRUB? What do I do to enable GRUB booting Windows? Thanks.

---

### Post by Bartender on 2006-12-27
I've read several times that you can't mix PATA and SATA.  It sounds like that's what your're trying to do?

---

### Post by jamadagni on 2006-12-27
Yes. Why can't I mix SATA and PATA? Is it a GRUB bug or what? Thanks.

---

### Post by tszanon on 2006-12-27
> **Bartender said:**
> I've read several times that you can't mix PATA and SATA.  It sounds like that's what your're trying to do?

I believe this is not true, since I did it myself for months.
Windows on the PATA HD, Ubuntu on two SATA HDs.
hd0=sda
hd1=sdb
hd2=hda

I remember that I had to use MAP in menu.lst, because I set sda as the first boot disk.
So, it was something like this:
map (hd2) (hd0)
map (hd0) (hd2)

Without using map, grub used to give me an error message when trying to load Windows.

---

### Post by rhbowman on 2006-12-27
Here is the deal

/boot must be located in the first 1024 cylinders for linux (probably old)

Winxp install drive must be in the first 4.5 or 6gb of the drive.


I.e.

Paritition your disk like this for a 40gb hdd:

first 500mb is /boot
Second is say 25gb for c:
Third is say 15gb for /
Fourth is whatever is left over for SWAP

Does this sound like your problem?

---

