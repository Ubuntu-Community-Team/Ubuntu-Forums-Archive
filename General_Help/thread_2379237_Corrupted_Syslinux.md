---
title: "Corrupted Syslinux?"
date: 2017-12-02
forum: General Help
---

### Post by jerome1232 on 2017-12-02
I reboot my computer because I suspected a SATA cable had wiggled lose (I have a problem with one of my SATA cables from time to time), got an fsck and then boot bombed out.

I've ran boot-repair, it claimed to repair the issue but no go.
Here is boot-repair output

[http://paste.ubuntu.com/26098997/]("http://paste.ubuntu.com/26098997/")

Looking that over I'm lead to believe I have an issue with Syslinux being corrupted perhaps

> sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32792 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

However I don't know how to continue troubleshooting this.

---

### Post by oldfred on 2017-12-02
That is your flash drive and syslinux is the BIOS boot loader and grub the UEFI boot loader for Ubuntu live installers with partitioned installs. Many installers now use the dd copy using the hybrid configuration which is not standard partitioning.
Standard installer is configured for the old BIOS type installer and newer UEFI type installer.

Does live installer boot ok?

With multiple drives, do not use Boot-Repair's autofix. That installs one grub to all MBRs. Often you want each MBR to have a different boot loader. And if similar speed drives Windows & Windows boot loader on one drive and Ubuntu & grub boot loader on other drive.

---

### Post by jerome1232 on 2017-12-03
ah, you are right, I should have caught that /dev/sdc1 is my usb drive!

Yes the live installer boots fine, I wrote the image to usb using rufus from windows (because the windows boot still works fine) it offered to burn it using the dd mode or iso mode and I choose iso mode.

That leaves me clueless as to why my Linux boot is failing.

---

### Post by yancek on 2017-12-03
Did you set sdb (220GB drive) to first boot priority in the BIOS as recommended by boot repair?  I would expect that to work as it has Grub in the MBR and the Grub boot files with correct boot entries for both Ubuntu and windows.  What's the empty Linux partition on sda?

---

### Post by jerome1232 on 2017-12-03
I get the same grub menu regardless of which drive I select as the boot drive. Currently /sdb is the selected as the first boot drive.

sda1 is Ubuntu's /home partition.

sda is a a HDD, sdb is a SSD. My / is on sdb5

Windows is fully on sda3

This is the screen boot bombs out on

[ATTACH=CONFIG]277726[/ATTACH]

---

### Post by jerome1232 on 2017-12-03
Ah ha!

I tried booting it with the upstart entry in grub, I got to a normal command line login shell (but not graphical interface), noticed it said that I had no home and $HOME was set to /

So I fscked /dev/sda1, found errors, fixed them, and everything boots again normally!

---

