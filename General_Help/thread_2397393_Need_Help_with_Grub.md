---
title: "Need Help with Grub"
date: 2018-07-28
forum: General Help
---

### Post by baklou on 2018-07-28
I'm new to Ubuntu so I'm a little unsure of how this works but...

I have two drives in my system, hd0 (sda), an SSD with my Windows 10 installation, and hd1 (sdb), an HDD with one partition for my files that I use with Windows, and another with my Kubuntu installation. Here's the problem: Whenever I boot up my computer, I am presented with a filesystem not found error, and I get a Grub Rescue terminal. Using the "ls" command, only hd0 appears. Now, when I run diskpart from Windows, it shows that my SSD is a bootable drive, while my HDD is not. And if I check in the bios, only the SSD is a boot option. Strangely, if I press f11 as the computer boots, which takes me to a boot drive selection screen, choosing any drive will allow me to pick and boot into either OS.

I believe the problem is that Grub is installed on the HDD, which isn't a boot drive, but messing with Grub Customizer and the terminal hasn't fixed the problem. I don't know what to try next.

---

### Post by TheFu on 2018-07-28
Welcome to the forums.

Please install boot-repair and have it generate the **boot-info**.  DO NOT attempt the repair.  Post the URL it generates back here and please post the exact make and model of the computer.  We need facts. Some vendors don't follow the EFI standards, so manual post-install steps are necessary or a mostly seamless boot.  On one of my systems, I have to manually move a file under /boot/efi/EFI/ to allow grub to work as expected.

---

### Post by baklou on 2018-07-28
Here is the URL:

[http://paste.ubuntu.com/p/YSYgJyrNMb/](http://paste.ubuntu.com/p/YSYgJyrNMb/)

The PC is custom built.

---

### Post by TheFu on 2018-07-28
Is it possible that Win10 is installed in EFI boot and Ubuntu is installed with legacy BIOS boot?  They should both be installed in the same boot mode.

---

### Post by baklou on 2018-07-29
I used this command on Linux:

#!/bin/bash
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

and it returned BIOS.

In Windows, it says "Legacy", which would indicate BIOS. My system uses a UEFI though when I need to access BIOS settings.

---

### Post by TheFu on 2018-07-29
Legacy boot is easier.

From inside the running Ubuntu, run these commands:
```
sudo grub-install /dev/sda
sudo update-grub
```

That will just refresh the grub stuff that you already have.  grub is already installed on both sda and sdb, but this won't make anything worse.  I don't know if it will solve it or not, but it might.  I don't think there is any harm in having grub installed on both disks. I do the same here to have a backup method to boot should the main disk, sda, die.

---

### Post by oldfred on 2018-07-29
Change TheFu suggestion of installing grub to sda to sdb and set BIOS to boot sdb as default.
And then with Boot-Repair or Windows repair disk install Windows boot loader to sda.

Newer Windows will not boot from grub if it needs chkdsk which may be caused by abnomal shutdown or if Windows is hibernated or fast start up is on. And Windows will turn fast start up back on with updates. Or when you have issues booting Windows from grub, just boot Windows directly from UEFI/BIOS and make repairs, then reset to boot grub by default again.

---

### Post by baklou on 2018-07-29
I have grub installed on both sda and sdb with boot-repair, and just yesterday I found an option to prioritize hd1 over hd0. It seems to be booting correctly now, but Grub Customizer doesn't work to change the appearance

---

### Post by oldfred on 2018-07-29
I am not a fan of grub customizer. it replaces grub2's files with its own versions.
What is it that you want to change?

General info:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) 
            Total Custom menu:
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827) 
   Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by TheFu on 2018-07-29
The systems I watch boot fast enough that anything shown during boot by grub doesn't matter.  For servers with lots of NICs and lots of storage, I generally don't watch those boot unless there is a problem ... that usually gets traced back to systemd not handling non-trivial networks correctly.

---

### Post by baklou on 2018-07-29
I'm just playing around with the background, etc..

---

### Post by baklou on 2018-07-29
Themes that I install from the internet work fine, but my custom one doesn't, even though I am only modifying the given settings.

---

