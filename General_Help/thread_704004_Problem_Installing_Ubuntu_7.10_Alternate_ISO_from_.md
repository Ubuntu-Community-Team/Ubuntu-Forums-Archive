---
title: "Problem Installing Ubuntu 7.10 Alternate ISO from an USB Flash Drive"
date: 2008-02-21
forum: General Help
---

### Post by ASTURIAS on 2008-02-21
Hello:

I cannot install Ubuntu!!! - Please help...

I already have a laptop running with Ubuntu Feisty Fawn and I want to install Ubuntu on another laptop. I tried the Live CD like on the first computer, but it was running extremely slow and I downloaded the Ubuntu Alternate CD from the website. On the download link I saw Gutsy instead of Feisty, so, I believe that's the version I have on the Alternate Ubuntu ISO.

Now, My new laptop's CD-ROM does not work and I used the Live CD making a Bootable USB Flash drive of 1GB. I successfully create a Bootable USB Flash drive for Ubuntu 7.10 Alternate and I did the following to use the USB for Installing Ubuntu like I did with the Live CD that was running slow.

Note that I'm using Windows to do this...

Step 1 - I formatted a 1GB USB Flash Drive with FAT32 and I used Syslinux to make it Bootable, running it on Windows Command Promp like this:

syslinux -sma X: (X is the letter of the USB Flash)

Step 2 - I moved the ISO from my computer to the Flash Drive without modifying it.

Step 3 -  I downloaded these files from the archives: vmlinuz and initrd.gz and then moved both to the flash drive.

Step 4 - I created a new file and added this to it:

default vmlinuz
append  initrd=initrd.gz ramdisk_size=512000 root=/dev/ram rw

I also tried:

default vmlinuz
append acpi=force initrd=initrd.gz ramdisk_size=512000 root=/dev/ram rw

*NOTE THAT I ALSO TEST IT WITH: acpi=force *

and then save it as syslinux.cfg

Now I have these files on my formatted 1GB flash drive:

1) ubuntu-7.10-alternate-i386.iso
2) vmlinuz
3) initrd.gz
4) syslinux.cfg
5) ldlinux.sys

When I boot up the USB Flash, everything comes up without problems, This appears:

SYSLINUX 3.11 2005-09...

Loading vmlinuz ............................................................................
Loading initrd.gz ....................................................................................................................................

Ready.

AND IT STOPS THERE!!!

Please don't tell me that I need to check if my laptop is capable of Booting from an USB or if it boots since I already booted the Live CD and this is working because the files are being loaded.

I you know what's going on here or what can I change, plese tell me!!!

Thanks!:)

---

### Post by pointone on 2008-02-22
You'll need to unpack the files from the .iso. Simply copying all the files from the .iso onto the flash drive should work.

---

### Post by ASTURIAS on 2008-02-22
I read on many websites that I can place the ISO without unpacking it, and I'm finally on the Installation process. But another error occurred:

I choose a Keyboard, configured the network and when I choose a mirror and the files are being "downloaded" from the Ubuntu archive, this error appears:

An installation step failed. The failing step is : choose a mirror of the Ubuntu archive. "...Please go back to the Main menu and repeat this step."

But I go back and nothing fixed this problem...

I read [here]("https://bugs.launchpad.net/ubuntu/+source/choose-mirror/+bug/43822"), that it might be a bug, but how can I change something if I have all the files in a flash drive and currently running on windows...

Thanks!

---

