---
title: "Grub on usb stick?"
date: 2008-06-17
forum: General Help
---

### Post by kattman on 2008-06-17
I want install GRUB on a USB stick. If the USB stick is inserted the GRUB menu will appear, if not XP will boot automatically.
Is it possible.
Xp is installed on 1 drive, and Ubuntu is installed on the Slave drive.
So all I really need is to put Grub on the USB stick Right ?
My Bios supports boot from usb

---

### Post by Titan8990 on 2008-06-17
I couldn't say for sure I but I almost certain that in order for that to work your OS and grub both would have to be on the USB drive so you can boot entirely from it without interference from your HDD and it's M$ MBR.

---

### Post by kattman on 2008-06-17
This person gave me the idea, See link
[http://uadmin.blogspot.com/2005/11/grub-on-stick.html](http://uadmin.blogspot.com/2005/11/grub-on-stick.html)

---

### Post by bodhi.zazen on 2008-06-17
It is possible.

You need to first install grub to the USB, then set the boot order in your BIOS

1. Install grub to USB depends on your usb device. Easiest way to do this is when you install Ubutnu to USB.

Otherwise, boot a live CD and install grub (you need to know your Ubuntu partition and designation of the usb device)

See this link : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]


2. Every BIOS is different, but set you boot order so it boots first from CD, then USB (removable devices), then hard drive.

---

### Post by manfer on 2008-06-17
Why would you want to do that?

For that purpose it would be easier to do a good configuration of grub installed on your hard drive.

What you want is grub to run Windows by default and with no delay and only run linux when you want.

--------------------------------------------------

#example /boot/menu.lst
#you have to press ESC to show the menu when you want to run ubuntu.

default 0
timeout 0
hiddenmenu

title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c74a89ed-2790-4def-9454-8088f5413e39 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c74a89ed-2790-4def-9454-8088f5413e39 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

--------------------------------------------------

That would be enough. Of course with a configuration menu.lst for your system.

---

### Post by kattman on 2008-06-17
Quote " Why would you want to do that?"
 #1: If I reinstall XP are upgrade to windows Vista!
 #2: If one of the hard drives fail I have a back up drive xp are ubuntu .
 #3: I can set the Cmos password that will allow me only to change it.
 #4: Boot to last hard OP system on Restart!

---

### Post by cdtech on 2008-06-17
I did this on a 1G USB drive:

I formatted with ext3 using gparted - copied the boot folder from my hard drive onto the USB stick:

# grub
grub> find /boot/grub/stage1
 (hd2,0)
(hd2 is my USB stick, found using sudo fdisk -l)

grub> setup (hd2)

All I had to do afterward was to configure my menu.lst on the USB:

title           Hardy 8.04, 2.6.24-19-generic GUI
root            (hd2,0) ##### **changed this to reflect my grub install (hd2)**
kernel          /vmlinuz-2.6.24-19-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro quiet init 5 vga=792
initrd          /initrd.img-2.6.24-19-generic
quiet

Hope this helps.......

P.S.
**My kernel line is for my setup, you shouldn't change yours, only the root.**

---

