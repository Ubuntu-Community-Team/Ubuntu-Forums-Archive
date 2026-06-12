---
title: "Not installing with unetbootin"
date: 2014-06-26
forum: General Help
---

### Post by blahh2 on 2014-06-26
[COLOR=#000000][FONT=verdana]Can't use a cd drive and can't boot from usb..[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]So, I was trying to install lubuntu 

[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I have: [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]lubuntu-14.04-desktop-amd64[/FONT][/COLOR]
also tried with [COLOR=#000000][FONT=verdana]lubuntu-14.04-alternate-amd64[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I run unetbootin select lubuntu and 14.04 live 64, check the disk image box select the ISO, for type i put hard disk and C:\  install, A message in unetbootin says that I should reboot and select unetbootinin the boot menu.[/FONT][/COLOR]

I reboot and Windows 7 starts normally, no boot menu... tried F8 but 'Windows 7' is the only OS option

[COLOR=#000000][FONT=verdana]My C: drive has a new name: 'Install lubuntu' and a red cirle as the icon. [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]am I doing something wrong?[/FONT][/COLOR]

---

### Post by kalehrl on 2014-06-26
Yes, you are.
You can't use unetbootin to install Lubuntu on your hard drive.
It is used for making bootable USB flash sticks.
You then boot from them and install Lubuntu.
You should consider yourself lucky you didn't mess up your windows installation.

---

### Post by Mike_Walsh on 2014-06-26
Hi, blahh2.

I think I can help you with this one. I'm a relative newbie to Ubuntu (I have both Ubuntu AND Lubuntu, in a dual-boot configuration), but I have tried several of the various distros, and each time I've used Unetbootin to put them on a flashdrive. Mainly because I have a rather noisy combo drive, which may need replacing before too long!

Anyway; make sure you've plugged the USB drive in that you want to use, before starting UNetbootin. It helps to re-format the flashdrive before you use it, in order to make certain it's free from old data.

Where you're going wrong is in selecting the hard disk for type; only use this if you do indeed want to put the distro onto a previously set-up partition on your hard drive. I don't know how good you are at disk admin stuff!

1) Select Disk Image. Leave ISO selected.
2) Browse to your downloaded distro, and select.
3) Type should be USB drive. The 'Drive' box, next to it, simply shows the location of your flashdrive as a path address; there should be no need to change this.
4) As you want Lubuntu, don't enter anything where it says "space used to preserve files across reboots" (that's Ubuntu only, and is merely used if you make changes during the Live Session, and wish to re-boot BACK into the Live Session before choosing to commit fully, and install.)
5) Hit OK, and let UNetbootin do its thing.

When it's finished, either re-boot straight away, or you can do this at a later point in time. When you do, you will need to select your boot menu as soon as the computer starts, and use your arrow keys to select your USB drive, then hit 'Enter', and you should boot into Lubuntu.

One point; when things initially start, you will see the UNetbootin menu appear; use the arrow keys to select 'Try with out installing', and hit Enter...then just leave it alone. The menu WILL take a little while to disappear!

Hope that helps.

Mike.

PS: kalehrl is indeed correct; you are VERY lucky you didn't mess up Windows 7!!!

---

### Post by Mike_Walsh on 2014-06-26
I actually installed Ubuntu originally onto a pre-prepared partition on a Seagate external hard drive; but that was done with 'wubi', which is a bit old-fashioned now.

Strictly speaking, kalehrl IS correct; Unetbootin IS intended for flashdrives. However, you CAN use Unetbootin to put distros onto a hard drive, but ONLY if:-

1) You have set-up a partition first, and
2) You have formatted that partition to behave as a flashdrive. This means formatting to FAT32, and you have a maximum partition size of 32Gb anyway, which appears to be an industry maximum for that particular file-system type on hard drives.

It's ALL about file-system types; your computer cannot physically distinguish between a hard drive and a flashdrive.....it's the file-system type that is recognised; typically NTFS, FAT32 (or 16), or, in the case of Linux, usually ext3 or -4.

---

