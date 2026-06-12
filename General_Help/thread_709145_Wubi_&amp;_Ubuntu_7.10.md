---
title: "Wubi &amp; Ubuntu 7.10"
date: 2008-02-27
forum: General Help
---

### Post by NeonLore on 2008-02-27
Hi to all! I'd like to try Wubi, so I've downloaded it, the version
**Wubi-7.10-alpha-rev386**
and the ISO image of
**ubuntu-7.10-desktop-i386**

Lanched wubi and rebbot PC. ok
Then at dual boot I've choose Ubuntu-Linux. ok

Start installing of Ubuntu but is always BLOCKED at 45%!! So I've to reset my pc :((

I've tried more times and always the same. How never? Or what can I have to do?
Thanks, bye bye

---

### Post by ago on 2008-02-27
Use 8.04 (requires new ISO)

---

### Post by NeonLore on 2008-02-28
> **ago said:**
> Use 8.04 (requires new ISO)

I've done like you said, but at finish of the installation, reboot and have this error :(

BOOTING "UBUNTU HARDY (development branch)" kernel 2.6.24-8-generic

FILESYSTEM TYPE IS NTFS, partiotion type 0x7
KERNEL /boot/vmlinuz-2.6.24-8-generic root= UUID=3A7CA63F7CA5FB3loop= /ubuntu/disks/root.disk ro quit splash

ERROR 15: file not found

Which is the file that I haven't?? :(

---

### Post by ago on 2008-02-28
Did you use Wubi 440 with the latest daily ISO?

You can fix it manually too. Edit /ubuntu/disks/boot/grub/menu.lst change the 2 numbers in

root (hd0,0)/ubuntu/disks

First number is the disk number -1, 
Second number is the partition number -1

---

### Post by NeonLore on 2008-02-29
> **ago said:**
> Did you use Wubi 440 with the latest daily ISO?

You can fix it manually too. Edit /ubuntu/disks/boot/grub/menu.lst change the 2 numbers in

root (hd0,0)/ubuntu/disks

First number is the disk number -1, 
Second number is the partition number -1

Ok thanks the problem was that ubuntu was in the second hd :p Rename all ok thanks for now!

Ah another question I've attivated visual effects in ubuntu (ok I've had a bit of problem but I've solved with some option) my question is:

" when I move the window and do the animation, even with the cube, is not "flowing", I don't know how say.... like snapping...Can I do something? Thanks :KS

My video card is a **ATI Radeon HD 2600 XT**

---

### Post by ago on 2008-03-01
There might be problems with the card driver since generally desktop effects are extremely smooth even with old hardware, but follow up in the general forum, this does not seem like a wubi issue.

---

