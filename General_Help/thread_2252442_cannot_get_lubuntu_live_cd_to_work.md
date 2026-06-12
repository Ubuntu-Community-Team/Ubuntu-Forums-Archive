---
title: "cannot get lubuntu live cd to work"
date: 2014-11-11
forum: General Help
---

### Post by DeadManDying on 2014-11-11
Hello. I am new to the Ubuntu forums but not new to Linux. Well now onto the issue. I recently found a old desktop in my basement and it is completely intact. It is a HP 512n. It has a blank HD in it and 384 mb of ram in it. So I decided to attempt to install lubuntu from a livecd. But when I try to install it from one it does not register that I put a CD in. Am I doing something wrong here? Can anyone help me here? If you need more information please feel free to ask. I need some help here please.

---

### Post by lisati on 2014-11-12
How did you burn the file to disk, as a file on a data disk, or as a disk image?

On a side note, I'm wondering if 384mb is sufficient RAM.

---

### Post by Yulra on 2014-11-12
You mentioned that the computer was old. Could it be that the disk drive no longer reads?

That said the machine should have some usb ports according to the specifications I found. Have you considered a Live USB instead? I find the best way to get something onto a stick is to use Gparted's restore disc image (everything else usually fails for me).

---

### Post by Al1000 on 2014-11-12
The computer's BIOS may well not have the option of booting from USB. Neither of my computers do, and they are not *that* old.

Which version of Lubuntu are you using? You may have better luck with 12.04 than with 14.04. I couldn't get Lubuntu or Kubuntu 14.04, or Ubuntu 12.04 for that matter, to boot on my old laptop (which has 768MB of RAM) because the hardware isn't capable of handling the graphics, but for some reason Kubuntu 12.04 boots just fine on it, and I have been reliably informed that Xubuntu 12.04 should work on it too.

The operating system by itself uses around 50% of the RAM on my laptop though, so I would also wonder if 384MB will be sufficient on this computer of yours. Even if you do get it to boot up, it might run out of RAM if you try to open any applications.

One option would be to boot up with [Puppy]("http://puppylinux.org/main/Long-Term-Supported%20Puppy.htm"), which by itself only uses around 75MB of RAM. Then use GParted which comes with Puppy to create a Linux swap partition on your hard drive, so that Lubuntu or whatever other Linux distro you might try, will be able to use swap from the outset.

Or, you might decide when you find that Puppy runs so much faster than anything else, that it would be the best option for this old computer.

---

