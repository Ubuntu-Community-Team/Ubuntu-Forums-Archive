---
title: "Dual boot - Kernel panic"
date: 2007-03-04
forum: General Help
---

### Post by mikelaw on 2007-03-04
Hi,

 First, I'm a total n00b when it comes to Linux. I tried it for a short time back in 97, but it so thoroughly kicked my butt that I gave up. Anyway, after 10 years I decided to give it another go. I set up a Dell Inspiron 1100 to dual boot both WinXP and Freespire. Everything went smoothly and I had little trouble. Then today I finally decided to give M$ the final heave ho, so I formatted the WinXP partition as ext3 and installed Ubuntu 6.10. I used the alternate installation CD. because I wanted to specify where to put Grub as I didn't want it on the MBR. My partitions are as follows, hdc1 is a small fat 16 Dell utility partition, hdc2 is ext3 Ubuntu, hdc3 is reiserfs Freespire and hdc4 is a linux swap partition. I originally had grub setup on the Freespire partition and it worked fine to allow me to dual boot between Windoze and Freespire. After I killed Bill I setup Ubuntu on hdc2. During the installation I set grub to the root of this partition. It detected that I had another Linux partition and set it as Debian 3.1. Anyway, after unsuccessfully trying to get the wireless adapter (USRobotics' USR5411) to work in, I decided to reboot into Freespire to check the adapter (The adapter worked flawlessly out of the box in Freespire) When I got to grub, I chose the Debian 3.1 and it started to boot, but soon stopped with a Kernel panic error "kernel panic - not syncing: vfs:unable to mount root fs on unknown-block(22,3)" I checked the menu.lst and everything seems OK. Since it started to boot I doubt it would have anything to do with grub, or woould it? I'm able to access the partition in Ubuntu. Ubuntu even mounts it automatically when I ligin and puts an icon on the desktop. 
would there be some files I might need to tweak in the Freespire installation to get it up and running again? Thanks.

---

### Post by mikelaw on 2007-03-05
Well, I finally got it fixed so I thought I'd post it here for anyone else having Freespire (FS) hijacking the boot partition. It seems I was wrong and it WAS the menu.lst entry, not just the one in Ubuntu, but the one in FS as well. Anyway, this was my path to dual booting Ubuntu and Freespire. 

In Ubuntu I opened Terminal and typed gksudo gedit /boot/grub/menu.lst 

Under the last section, 
I changed the following:

title Debian Gnu/Linux 3.1 
root (hd0,2)
kernel /boot/vmlinuz-2.6.14-gratis root=/dev/hdc3
savedefault
boot

to:

title Freespire Ver. 1.0.13
root (hd0,2)
makeactive
chainloader +1 

 After I saved the file I rebooted, chose Freespire from the Grub menu and it took me to the Freespire grub where I was able to boot into FS. (The lights on my wireless card came on during the boot and I had wireless access once KDE loaded. - yeah.) However, when I rebooted, it would only take me to the FS Grub menu. Oops. So I booted up to my SystemRescue CD, ran Gparted and could see that the Freespire partition was set to boot. So I changed it so the Ubuntu partition was boot, restarted and was presented with the Ubuntu grub menu. 

 Once I was into Ubuntu I changed  "makeactive" to "savedefault" and tried again. This time when I rebooted, I got the Ubuntu Grub menu, selected Freespire, booted up to the login and click Restart. The laptop rebooted, but again, no Ubuntu Grub, just the Freespire Grub screen. DOH! OK, a little googling later and trying various things like adding an initrd entry for Freespire in menu.lst I finally found something that looked like a winner so I edited menu.lst once more and changed the Freespire entry to:

title        Freespire Ver. 1.0.13
savedefault
configfile   (hd0,2)/boot/grub/menu.lst 

 Now when I rebooted and selected Freespire from the Ubuntu Grub menu it started to boot FS, but for some reason couldn't find the bootsplash image. However, it gave me the option to continue and I was presented with an ugly green Grub menu with blue letter. I selected Freespire and once at the desktop I checked menu-normal.lst (menu.lst simply points to this file. WTF?) which I opened to see why it kept changing the partition flags to make itself the active boot partition. I noticed that each entry had "jiffymount=noatime". I did a search an read through some threads and found that others have noticed that Freespire likes to have it's partition as the active boot partitioni and this has something to do with  Jiffyboot. So I tried a suggestion I found that worked for someone else. 

 While still in FS I opened a terminal and at the bash prompt I typed sudo cd /sbin and once there I typed chmod a-x jiffy*. I then rebooted to the System Rescue CD,  ran Gparted and set the flag for the Ubuntu partition back to "boot". After that I rebooted again and chose Freespire from the Ubuntu Grub menu, then chose Freespire again when presented with the FS grub menu, this time with no bootsplash errors and a nice black menu with white letters and the selection in gray since I commented out the splashimage line and changed the colors to white/black gray/black in FS's menu-normal.list.

 Now to see if chmod a-x jiffy* would actually stop FS from making it's own partition boot. Another reboot and voila! I was presented with the Ubuntu Grub menu. Yes! Yes! Yes! I set up two linux partitions so I could compare Freespire and Ubuntu side by side, and also to learn some more about Linux, but IMHO this has been a real P.I.T.A. The moral of the story is that Freespire doesn't want to play nice with Ubuntu unless it's beaten into submission. I wonder if this will change when Freespire switches from Debian to Ubuntu.  Anyway, I'm off to see why wireless isn't working even though I followed the instructions exactly. I guess I have to hunt down those "hidden" instructions.....

---

### Post by mikelaw on 2007-03-05
BTW, has anyone successfully set up a USRobotics MAXg PC Card wireless adapter (USR5411) in Ubuntu? I couldn't get ndis to take the USR drivers, but it did accept the generic Broadcom drivers. Unfortunately, even though it recognizes the drivers and sees the hardware the lights never light on the adapter as they do during a boot of Freespire and I just can't get it to work in Ubuntu.

---

