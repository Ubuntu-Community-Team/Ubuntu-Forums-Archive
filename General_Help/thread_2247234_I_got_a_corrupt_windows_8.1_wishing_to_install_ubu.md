---
title: "I got a corrupt windows 8.1 wishing to install ubuntu but there is a problem"
date: 2014-10-06
forum: General Help
---

### Post by dhruv3 on 2014-10-06
Hey guys, I'm wishing to install a Ubuntu over my old windows 8.1 software... But there is one problem... When ever I put in the disk/live USB (tried both) bios and boot menu won't detect the software on it.... Yes I did burn/place it correctly on the disk/USB... Is there anybody that could help?

---

### Post by FormatSeize on 2014-10-06
Did you try turning off the 'secure boot' option in the BIOS (or whatever Windows 8.1 has)? If you have already done that, then you can press the Windows key, search for either 'Troubleshoot' or 'Advanced Startup' and one of those will let you boot from the USB/CD. 

The second option doesn't work if you can't get into your Windows installation, though.

---

### Post by dhruv3 on 2014-10-06
Okay I'll try that if it doesn't work I'll come back if it works I'll come back :lolflag:

---

### Post by dhruv3 on 2014-10-06
Still on boot menu...
No option :(
[IMG]http://i.imgur.com/v8ioTNq.jpg[/IMG]

---

### Post by oldfred on 2014-10-06
Did you download the 64 bit version which is the only one that is UEFI compatible?
Did you use the instuctions on the download page to create bootable flash drive or use unetbootin?

       Also how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
      
 If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

What does UEFI boot show, additional options?

What hardware? Vendor model number, video card/chip?

---

### Post by dhruv3 on 2014-10-09
Omgggg i downloaded 32 bit silly meeee

---

### Post by dhruv3 on 2014-10-09
Works now but I don't know I it'll work.
[IMG]http://i.imgur.com/UZGrd0S.jpg[/IMG]

---

### Post by stalkingwolf on 2014-10-09
the live can take some time to boot.  i have had several minutes depending on the specs.  personally i would do a dual boot first.then if all is ok use the win partition for storage.

---

### Post by dhruv3 on 2014-10-09
Been on this screen for about 10 mins usb live :(
[IMG]http://i.imgur.com/Lm4rBLv.jpg[/IMG]

---

### Post by yancek on 2014-10-09
Ten minutes seems a little long to be on that screen with a new computer.  Did you select the "Try Ubuntu" option to test your internet connection from the flash drive or just go to the install options.  What type on connection do you have?  You might try de-selecting Download updates and install third party software and do it after the installation.

---

### Post by dhruv3 on 2014-10-09
> **yancek said:**
> Ten minutes seems a little long to be on that screen with a new computer.  Did you select the "Try Ubuntu" option to test your internet connection from the flash drive or just go to the install options.  What type on connection do you have?  You might try de-selecting Download updates and install third party software and do it after the installation.

i tried that, I have a Fiber internet connection (250/300)

---

### Post by Dennis N on 2014-10-10
Getting stuck at this installer screen has been a problem for some people for a long time. There is no single answer that works for all, but different ways people have found to get the installer moving ahead can be found by googling "stuck on preparing to install ubuntu".

It happened to me once a few years ago - after failing over several retries, I then tried a different make of flash drive and for some reason, that worked the first try. Maybe a coincidence.

---

### Post by dhruv3 on 2014-10-10
> **Dennis N said:**
> Getting stuck at this installer screen has been a problem for some people for a long time. There is no single answer that works for all, but different ways people have found to get the installer moving ahead can be found by googling "stuck on preparing to install ubuntu".

It happened to me once a few years ago - after failing over several retries, I then tried a different make of flash drive and for some reason, that worked the first try. Maybe a coincidence.
I installed windows 7 onto it making a "clean partition" maybe it'll work now

---

### Post by dhruv3 on 2014-10-10
Also should legacy support be enabled?

---

### Post by oldfred on 2014-10-10
Depends on how you installed Windows 8.
If you installed Windows in UEFI mode, then you should install Ubuntu in UEFI boot mode.
IF you installed Windows in BIOS/Legacy/CSM boot mode then Ubuntu should also be in that mode.

And if drive was gpt and using UEFI and you used Windows to convert to BIOS with MBR partitioning you will have issues as Windows does not convert correctly.

Post this if you can get into live mode:
sudo parted -l

How you boot installer is how it installs:
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

