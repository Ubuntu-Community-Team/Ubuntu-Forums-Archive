---
title: "Need Help With Grub"
date: 2008-05-11
forum: General Help
---

### Post by agonoruci on 2008-05-11
Ok last night I was half asleep and while I was going to delete my music partition and I accidentally deleted my ubuntu partition, on another partition I had windows vista. Now when I boot my computer all I get is this message.

GRUB _

Currently I do not have an ubuntu cd/dvd and I actually do not have any dvd/cd of any OS. All I have are whatever I can put in a flash drive, is there anything I can do with a flash drive(up to 4GB) to get back to my vista partition at least.

Thx for the help guys.

---

### Post by pro003 on 2008-05-11
ok. put your install cd of vista and boot it... go for repair your system startup... it will be solved for vista... and ubuntu - hmmm you'll have to install it all over again...

---

### Post by agonoruci on 2008-05-12
Thats the problem, i dont have my vista dvd or my ubuntu dvd, all I have is one computer connected to the internet, and a usb(4gb). Is there anything else I could do other than totally reinstalling.

---

### Post by pro003 on 2008-05-13
you need to get in somehow... I have no idea how could you possibly do that without OS installation disk?!:confused:

There is way to put some live OS on USB and boot from it, but I can't tell you which one could do the best job for you... Do some research. 

The best solution would be to have installation disks. Find them, download them... It's a crappy situation...

---

### Post by Herman on 2008-05-13
See lswest's and bodhi.zazen's thread, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")
lswest links you to a site where you can download your very own Windows Vista Recovery CD if you don't have one, (providing your Windows system is genuine and validated), and gives you the commands for setting your hard disk's MBR to boot Windows and restore the Windows boot sector too, for Vista and XP.

Edit: You could use Super Grub Disk for USB, [super_grub_disk_english_usb_0.9716.tar.gz]("http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/usb/super_grub_disk_english_usb_0.9716.tar.gz").

---

### Post by agonoruci on 2008-05-13
How would I use Super Grub Disk, just extract and copy onto usb, then boot into the usb?(BTW, I have just found out my cd/dvd(on both computers) drive does not work, so that kinda narrows it down to the USB)

---

### Post by Herman on 2008-05-14
Assuming your other computer has Ubuntu or at least some Linux distribution in it, here is a link that should help you, [How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk").
You need to extract the directory called 'boot', and copy it to your USB disk.
Then you will need some other GRUB, (GRUB from your other computer maybe), to [install the USB disk's GRUB to MBR]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#install_GRUB_to_MBR") in the USB disk.

---

### Post by agonoruci on 2008-05-14
thank you, but unfortunately i have parents(and when they get used to something they do not like to switch a.k.a. windows). So on this computer I do not have the ability of going into ubuntu and getting those files that i need or use the terminal, could anyone upload the file that I need.

---

### Post by sanjeevpunj on 2008-05-15
Just try to use a friend's computer and download Ubuntu 8.04 again, and re-install!

---

