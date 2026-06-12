---
title: "Stuck in grub resque after deleting all partitions"
date: 2015-05-28
forum: General Help
---

### Post by noah20 on 2015-05-28
Hey guys,
I got a decent problem.

I have a notebook (Asus X51R) on which I installed Linux mint some time ago. Unfortunately I deleted the windows xp partition back then. But nonetheless I have two partitions now, one ext4 and one empty NTFS one.
But I noticed a problem some days ago - the keyboard doesn't work in bios. After researching I found out that it's a common problem on this particular laptop and that it can only be fixed with a bios update.
I tried to reinstall XP to get access to an Asus bios flashing program, but as I wrote before the keyboard doesn't work when the PC says "press key to boot from CD" (not even a external one).
But luckily the PC boots from Linux CDs.(I don't know why)
But the problem is that I deleted all partitions on the hard disk now. And as you know the PC still tries to boot with grub but its deleted.
I already tried to reinstall mint and to fix it with boot-repair on a life CD but it doesn't work too.
Is there any opportunity to completely remove grub as well as making the PC boot from the windows CD without using bios?
I'm completely stuck here, I even tried mirroring an old xp partition the notebook drive but yeah - it only boots to Linux as grub doesn't work neither.

I hope you understood my problem and I appreciate every help!

---

### Post by leunam12 on 2015-05-28
Remove the hard drive and see if the computer defaults to booting from the CD

---

### Post by mörgæs on 2015-05-28
Hi, welcome to the fora.
If you create a bootable USB stick with Freedos you might be able to install a new BIOS from here regardless of BIOS and partitions.

Maybe you need to attach an external keyboard for the operation.

---

