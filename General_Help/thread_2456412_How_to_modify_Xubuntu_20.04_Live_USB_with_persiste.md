---
title: "How to modify Xubuntu 20.04 Live USB with persistence created with Rufus."
date: 2021-01-11
forum: General Help
---

### Post by kagashe on 2021-01-11
I have come to a relative's place and borrowed his Dell Inspiron Laptop for personal use. It has Windows 7 and I created Xubuntu 20.04 Live USB with persistence using Rufus.. I had uploaded my gnucash and required office files to Drive from my personal Laptop before leaving home and downloaded them on this Live system. I installed gnucash and happily using the Live system..

The Live system boots into the desktop asking for Try Ubuntu and Install Ubuntu options. I got rid of this irritant by removing ubiquity.

Now there are two more irritants. There is file system check on every boot which I interrupt by pressing Ctrl plus C. But I would like to get rid of it.

The second irritant is the system asks for removal of USB on shutdown. How can I get normal shutdown with USB kept inserted since it is required on every boot till I use this Laptop.

Kamalakar

---

### Post by howefield on 2021-01-11
Unable to test at the moment but the following two threads appear to have confirmed solutions..

[https://unix.stackexchange.com/questions/528577/how-to-skip-please-remove-the-installation-medium-then-press-enter](https://unix.stackexchange.com/questions/528577/how-to-skip-please-remove-the-installation-medium-then-press-enter)
[https://askubuntu.com/questions/1229050/how-do-i-disable-filesystem-checking-on-boot-in-20-04](https://askubuntu.com/questions/1229050/how-do-i-disable-filesystem-checking-on-boot-in-20-04)

---

### Post by ActionParsnip on 2021-01-11
Could install Ubuntu to the USB (you'll need a separate install media so 2 USB drives) and you can tell your BIOS to boot USB first when you insert the stick into the system. Far far easier than messing with Rufus and persistence and whatnot

---

### Post by HermanAB on 2021-01-11
I don’t know why Ubuntu still support the persistent thing. With a USB stick or SD card, you can do a normal install.

---

### Post by agvantibo on 2021-01-12
Hey, using a LiveUsb to do stuff is suboptimal. It should be used for just servicing and installing Ubuntu, not running it.
You can just install it on a USB drive, with the custom partitioning option, this will take up to 30 minutes, and you will have a complete, unhindered Ubuntu system.

---

### Post by kagashe on 2021-01-12
> **howefield said:**
> Unable to test at the moment but the following two threads appear to have confirmed solutions..

[https://unix.stackexchange.com/questions/528577/how-to-skip-please-remove-the-installation-medium-then-press-enter](https://unix.stackexchange.com/questions/528577/how-to-skip-please-remove-the-installation-medium-then-press-enter)
[https://askubuntu.com/questions/1229050/how-do-i-disable-filesystem-checking-on-boot-in-20-04](https://askubuntu.com/questions/1229050/how-do-i-disable-filesystem-checking-on-boot-in-20-04)
Thanks.
The first solution for removal of usb works.
The second solution to skip file system check does not work. I get an error on giving the command.
```
sudo tune2fs -c 0 /dev/sdb1
tune2fs 1.45.5 (07-Jan-2020)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1 contains a vfat file system labelled 'XUBUNTU 20_'

```

Kamalakar

---

### Post by kagashe on 2021-01-12
@ActionParsnip
@HermanAB
@agvantibo
Thanks for your advise. I am using Ubuntu for last 16 years and I know what I am doing.
I am happily working on this Live USB and it is much faster than installed system and it is temporary.

Kamalakar

---

### Post by CelticWarrior on 2021-01-12
I cannot be any faster than the same system installed in the exact same drive.

---

