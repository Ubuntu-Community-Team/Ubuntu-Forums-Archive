---
title: "Not booting up from the boot repair"
date: 2019-05-22
forum: General Help
---

### Post by Chanikya_Desu on 2019-05-22
Hi my computer is not booting up even after I repaired the boot file.

[Http://Paste.ubuntu.com/p/9DsQZ8zXkW/](Http://Paste.ubuntu.com/p/9DsQZ8zXkW/)

Uploaded the summary of the boot-repair.

Any help?

---

### Post by yancek on 2019-05-22
Remove the Sandisk usb drive.  Reboot and enter the BIOS setup and set ubuntu to first boot in the BIOS boot options.  Accessing the BIOS varies from manufacturer to manufacturer so you will need to watch the screen on boot to see what key you need to use.

---

### Post by oldfred on 2019-05-22
You are showing this:
Ubuntu 14.04.5 LTS
But That is EOL - end of life as of April 2019.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

And Boot-Repair says sda2 is full.
/dev/sda2      ext4       901G  878G     0 100% /mnt/boot-sav/sda2

Not sure if housecleaning would let you boot, but you need to fully backup up and install a current version, probably 18.04LTS.

---

### Post by Chanikya_Desu on 2019-05-22
> **oldfred said:**
> You are showing this:
Ubuntu 14.04.5 LTS
But That is EOL - end of life as of April 2019.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

And Boot-Repair says sda2 is full.
/dev/sda2      ext4       901G  878G     0 100% /mnt/boot-sav/sda2

Not sure if housecleaning would let you boot, but you need to fully backup up and install a current version, probably 18.04LTS.

I understand mine is outdated version. But my home automation database which is ubiquiti mfi is programmed with that version. I have almost 70 switches in the house and this project is dead and I am just surviving with what I have.

Thanks

---

### Post by Chanikya_Desu on 2019-05-22
> **yancek said:**
> Remove the Sandisk usb drive.  Reboot and enter the BIOS setup and set ubuntu to first boot in the BIOS boot options.  Accessing the BIOS varies from manufacturer to manufacturer so you will need to watch the screen on boot to see what key you need to use.

I tried that too. I will see once again. But when I removed Sandisk USB drive the grub nenu is not available. Plus the boot options on boot menu I have two which are directing to the same hard drive and also third which is just pointing to the same hard drive but no description on that. I could not understand from day one how three booting options came out for one software.

---

### Post by oldfred on 2019-05-22
Ubuntu in UEFI boot mode has two boot options, one uses shimx64.efi for UEFI Secure Boot and the other grubx64.efi for standard UEFI. The shim file works for standand UEFI also, so not sure why still need grubx64.efi.
And it now adds the hard drive fallback boot entry which is default for external devices or /EFI/bootx64.efi. 
So if your UEFI has an UEFI hard drive boot entry which not all systems have by default, you then get 3 UEFI boot options in UEFI.

To get to a grub menu with UEFI you press escape key after UEFI screen but before grub menu. If you have UEFI fast start up on, it may be so quick you do not have time or much time to press escape key.

Then in grub menu can you boot recovery mode, under advanced options? And at least get to a terminal to perhaps do some housecleaning so it is not 100% full?

And if you have not done good backups, do that before anything else.

RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

Is it just java 8 that is the requirement for you special app?
[http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/)

---

### Post by Chanikya_Desu on 2019-05-23
> **oldfred said:**
> Ubuntu in UEFI boot mode has two boot options, one uses shimx64.efi for UEFI Secure Boot and the 
other grubx64.efi for standard UEFI. The shim file works for standand UEFI also, so not sure why still need grubx64.efi.
And it now adds the hard drive fallback boot entry which is default for external devices or /EFI/bootx64.efi. 
So if your UEFI has an UEFI hard drive boot entry which not all systems have by default, you then get 3 UEFI boot options in UEFI. 

Thanks for info.

> **oldfred said:**
> To get to a grub menu with UEFI you press escape key after UEFI screen but before grub menu. If you have UEFI fast start up on, it may be so quick you do not have time or much time to press escape key.

I will try this.

> **oldfred said:**
>  Then in grub menu can you boot recovery mode, under advanced options? And at least get to a terminal to perhaps do some housecleaning so it is not 100% full?

Today when I tried this I got the terminal up by pressing Ctrl+Alt+F1. And I checked lots of log files which are right protected and compressed by mongo database and mfi software. I could not delete them. Now to change them to read/write/execute option, how can do it? Or how can delete the files. I have installed webmin to do the log file rotation, but I missed this location somehow. Once I get into it I will do it now.

> **oldfred said:**
>  And if you have not done good backups, do that before anything else.

I will. But only thing is I do not know how to do a disk copy on Ubuntu. And retrieve from copy of the disk and copy all its contents and boot from there. I know how to to do on Windows, but not on Ubuntu.

> **oldfred said:**
> 

RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:


What you mean by manual install? Everything is done by apt-get.

> **oldfred said:**
>  Is it just java 8 that is the requirement for you special app?
[http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/)

It is not Java 8 but Have 6. It might work on Java 7. But upgrades were stopped after that. It is working flawlessly for me. Only issue is log files built up. And clean once in a while. It is a portable PC with 16 GB RAM and 1 TB drive.

Thanks for advices.

---

### Post by Chanikya_Desu on 2019-05-25
I have deleted lot many log files and cleared the memory but still not booting up.
One thing I found is I can get to terminal and deleted the log files. But Xubuntu not loading up. Any help?

---

### Post by oldfred on 2019-05-25
Are files deleted, but in trash, so still taking space?

---

### Post by Chanikya_Desu on 2019-05-27
> **oldfred said:**
> Are files deleted, but in trash, so still taking space?

In Trash I did not see any files. May be I will have a close look. I did not see any files as you said earlier, shimx64.efi , or grubx64.efi, or bootx64.efi. The interesting part is I did not see any files in /boot/efi/ directory it is empty. When I tried to boot with recovery option, and saw the OS says /boot/efi/ (292) terminated with a value 1. Not exactly what it means.

Thanks

Chanikya

---

### Post by oldfred on 2019-05-27
Your Boot-Repair report showed .efi files in the ESP. If that is now empty, you have to re-install grub from scratch, but with obsolete version that is difficult.
Did you delete files with sudo, they then may be in root's trash, best to check that also which also is difficult.

---

