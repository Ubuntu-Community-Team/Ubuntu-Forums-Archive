---
title: "Can't boot/install Lubuntu 14.04 from Live CD"
date: 2014-07-20
forum: General Help
---

### Post by Unlocker9000 on 2014-07-20
Hi all

So I've been trying to install "Lubuntu 14.04 i386" on one of my pc's (specs: Pentium D 945, Intel D101GGC, 1gb DDR 400mhz), but with the latest release I keep getting stuck during boot, and the error comes no matter if I choose "Install Lubuntu", "Try Lubuntu without installing" or "Check disc for defects".
I'm currently doing it with a CD, but I've also tried it with a USB thumb drive.
I've also tried other older versions of Lubuntu with no luck, It wasn't  the same error, but it still didn't work. I have Windows XP running at  the moment and I've had other Linux OSes running on it before, so it  shouldn't be a hardware problem.

[IMG]http://i.imgur.com/XYxMtYa.jpg?1[/IMG]

I think it's during the hardware initialization, but do anyone of  you know what's causing this error and if so, can do something to fix  it?

Thanks

---

### Post by Rex Bouwense on 2014-07-20
I would check the MD5Sum on your download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It is entirely possible that you have a bad download since it is not working on either CD or flash drive.

---

### Post by Unlocker9000 on 2014-07-20
I've tried to download the .iso multiple times, but I got the same result. I even tried the 64bit version on a USB stick, but that hangs after 30 of drive activity.

---

### Post by Rex Bouwense on 2014-07-20
Did you check the hash?  If it is not correct then it will not work.  Only use the 64 bit version if your computer can handle 64 bit.  I am not sure if your hardware is set up for 64 bit but if it came with Widows XP then it is unlikely that it is.  However Pentium D is supposed to be capable of using 64 bit.

---

### Post by Unlocker9000 on 2014-07-20
The system is runnung Windows Xp Pro 64bit Edition, so I know that the system is 64bit capable, but there is no reason to install the 64bit version of Lubuntu, as there's only 1gb of RAM. And I've just verified the hash and it's the same, so the file isn't corrupt. When I tried to install Lubuntu 13.10, the system rebooted shortly after selecting a option in the boot menu, but I got Bodhi to boot by replacing the DVI cable with a VGA cable (I'm using a XFX 8800gt) (my monitor is weird and doesn't work with Windows Vista or 7).

---

### Post by Unlocker9000 on 2014-07-20
A quick update, I got Lubuntu 13.04 to work and installed it on the machine. Would have been nice with the newer version though.

---

### Post by michal15 on 2014-11-25
Hi, I was experiencing the same issue with USB install (Ubuntu 14.04). The USB was originally formatted with NTFS. Formatting as FAT32 made this particular screen disappear, but installation did not work anyways.. I run disk check (from Ubuntu installation menu) - results showed 2 erroneous files. I finally decided to try 14.1 - this one installed without any issues. Hope this helps.

---

### Post by stiv2k on 2014-12-03
Hi,

Can confirm, same problem here with a DELL Dimension 3000 (Pentium 4 2.8 GHz, 1GB DDR). See the attached photo below. I can also confirm its not a hardware problem as I just installed XP flawlessly on it, but who wants to use XP :(

[IMG]http://i.imgur.com/ipxk8eg.jpg[/IMG]

Any solution would be appreciated, thanks

---

### Post by mörgæs on 2014-12-03
Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by stiv2k on 2014-12-08
SOLVED, thanks, perhaps it will work for OP as well.

---

