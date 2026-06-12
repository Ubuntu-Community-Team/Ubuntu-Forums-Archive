---
title: "GRUB and rEFInd no longer loading on Yosemite/14.04 dual boot"
date: 2014-12-26
forum: General Help
---

### Post by connor15 on 2014-12-26
I've been battling this off and on for some time now. A friend installed Ubuntu on his laptop so we could do some programming together. I figured the closer our development environments, the better, so I installed 14.04 on my late 2013 MBP retina using rEFInd and it worked just fine. The installer did tell me it couldn't find an existing OS on the HDD, so I went in and manually partitioned it. A few days later, it didn't load rEFInd and booted straight to Ubuntu, which I didn't mind and thought I could fix later. The next day, it booted to a black screen with only a blinking command cursor. 

Things I have tried:
  - held 'X' at startup. Received a 'No bootable device -- insert boot disk and press any key'
  - held 'Option/Alt' at startup. Took me a screen where it shows an HDD with 'Windows' under it and an arrow button. I've never installed Windows on the laptop and clicking the button takes me to the black screen with blinking cursor. I also have the option to connect to a wireless network.
  - reinstall Ubuntu. I've tried it several times but ever since it started booting to the black screen, a fresh install does nothing to help.

All I can do with it now is run Ubuntu live from a USB, which I'm sure is enough to get me somewhere, but I don't have the Ubuntu know-how to know where to start. My only idea at this point is go into the Ubuntu installer, to the partitioning tool, wipe the partition with Ubuntu on it and see where that takes me. But I'm nervous that will break something else horribly. Any and all help will be greatly appreciated.

---

### Post by yancek on 2014-12-26
Boot the Ubuntu medium and go to the site below and either download it to the Live Ubuntu or put it on a flash drive.  Explanation at the site.  Once you have done that, run it and select the option to create a boot info summary which you can post here for help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by connor15 on 2014-12-27
Thanks for the link. Here's the summary I received. [http://paste.ubuntu.com/9631161/](http://paste.ubuntu.com/9631161/)

---

### Post by yancek on 2014-12-27
Your bootinfoscript output shows Grub installed to the master boot record of sda, the first drive.  The first partition, sda1 is the vfat partition used for the efi files and the Ubuntu efi files are there.  Ubuntu is on sda2 and swap is on sda3.  If you use EFI, you don't put the Grub boot code in the master boot record.  That's one problem.  There are numerous references to sda and its partitions and sdd which I expect is your Ubuntu flash drive.  The ls -l output shows some references to Apple and one to sdb which is an SD card.

At the end of the script there is a suggested repair and it indicates you did not select that.  I'm not sure what it would do as I don't use EFI so you will need to wait for someone familiar with it to suggest something.  If you had some Apple system on this computer, I don't see any sign of it now.

---

