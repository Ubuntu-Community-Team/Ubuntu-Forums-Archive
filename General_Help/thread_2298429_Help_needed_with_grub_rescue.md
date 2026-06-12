---
title: "Help needed with grub rescue"
date: 2015-10-10
forum: General Help
---

### Post by BadNameHere12 on 2015-10-10
I use a Acer C720 chromebook with a ubuntu installed. I currently have an issue as when I attempted to reboot after a crash I got sent into grub rescue. I was following this guide to help me boot back up:[URL="https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/"]https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/  


[/URL]But then as I tried to follow the guide, when I type ```
insmod normal
``` it showed the same reason why I wasn't able to boot normally "error: attempt to read or write outside of partition." and it sends me straight back into the grub rescue. I then tried to carry on with it but when I type ```
normal
``` it stated normal wasn't a command that existed and when I try to type ```
insmod linux
``` it states I am out of memory. I have had my ubuntu installed directly into the internal hard disk. Please help me solve this issue.

---

### Post by oldfred on 2015-10-10
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Did system crash or did you do a hard shutdown, power down using power switch? Then file system may be corrupted and you may then need to run fsck to repair it.
       
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
To see partitions:
sudo parted -l
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by BadNameHere12 on 2015-10-11
I had preformed a hard shutdown using the power switch. I currently am following the boot info guide and I'm wondering if I could substitute a live-usb with an external hard drive. I have a Western 1TB HDD and I believe those can work on linux natively

---

### Post by oldfred on 2015-10-11
The normal live installer to a flash drive erases the entire flash drive and formats it to FAT32, copies/extracts ISO and installs BIOS boot loader. If UEFI you do not need BIOS boot loader. 

If system is UEFI, you can create FAT32 partition with boot flag and just extract ISO. It should then boot with UEFI.
I believe some of the installers will let you have a smaller partition on a hard drive, but do not know details. I always have grub installed to every drive, flash drive or DVD, so I use grub to directly boot ISO.

---

