---
title: "I can't install Ubuntu."
date: 2016-02-12
forum: General Help
---

### Post by hatim2 on 2016-02-12
Hello, I have a Sony Vaio laptot, the VPCEL3S1E with Kubuntu 14.04 installed. The problem is that, i have installed Ubuntu 14.04 in a USB, but when i try to install it (bootable USB) the screen keeps black with a white underscore  in the left top computer's screen. After that i tryed to install other OS (kali linux) and after that the same thing happens, i do not know how to solve it, i tryed a lot of things, i would like someone helps me, i want to install Ubuntu in my computer. 

Thanks for reading and i'm sorry for my bad english writting, i am from Spain.

---

### Post by yancek on 2016-02-12
What are you doing differently than when you installed Kubuntu?  They both use the same installer.
How did you put Ubuntu on the flash drive?  Did you do an md5 checksum on the downloaded Ubuntu iso file?
Have you tried booting the flash drive in another computer to eliminate that as a problem?

Kali Linux is designed to be used by computer forensic experts.  If you want it to learn about computer forensics, try installing it to a flash drive from the detailed instructions on their site.  It is not designed to be used as an "everyday home user" system.

---

### Post by hatim2 on 2016-02-12
> **yancek said:**
> What are you doing differently than when you installed Kubuntu?  They both use the same installer.
How did you put Ubuntu on the flash drive?  Did you do an md5 checksum on the downloaded Ubuntu iso file?
Have you tried booting the flash drive in another computer to eliminate that as a problem?

Kali Linux is designed to be used by computer forensic experts.  If you want it to learn about computer forensics, try installing it to a flash drive from the detailed instructions on their site.  It is not designed to be used as an "everyday home user" system.

I just flash the iso in my USB via UNetbootin, i do not know how to do the md5 checksum, if you can told me i will listen you. The Kubuntu OS was in my friend's USB, so i do not know how does he installed it. Also i do not have other computer :( 

When i install the iso in a USB i just format the USB in a FAT32 format and then I launch UNetbootin. Thanks for answering.

---

### Post by yancek on 2016-02-12
How to do an md5 checksum is explained at the link below.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by andrewlrharris on 2016-02-12
I used an iMac and a USB stick and a free ISO to USB utility to install Ubuntu 15.10 on my really slow Windows 7 HP Mini 110-1197TU (which I now use daily and absolutely love).

I had to format the USB stick on the Windows 7 HP Mini prior to booting and installing Ubuntu. I found that FAT16 or FAT32 was the most universally compatible format (I plan on transferring files from Mac to Windows to Ubuntu in the near and far future - and without any troubles).

So, I used the Mac utility to download and copy the Ubuntu 15.10 ISO/DMG file to the USB, set the HP Mini to boot from the bootable USB drive.

Then, chose the install Ubuntu 15.10 OS onto the HP Mini, answered some rudimentary questions and voila! Ubuntu running flawlessly and now much faster and much more stable than ever before! Love it.

I used the iMac initially as the Windows 7 OS running on the HP Mini was just too slow and unreliable. I'd added and hacked Windows to pieces and should have rebuilt it but couldn't be bothered only to have it replaced with Ubuntu anyway.

Let me know if you have any questions on how I did this without any errors at all.

---

### Post by hatim2 on 2016-02-13
I solved the problem, first of all thanks for answering and reading, the problem was that i was formatting the usb via the konsole, aun flashing the os via UNetbootin. You should format the usb via gparted and flash the usb via kubuntu software, which is preinstalled. Ubuntu 15.10 running perfect.

---

### Post by mörgæs on 2016-02-13
Thanks for trying to mark the thread 'solved'. Better though to use Thread Tools.

---

