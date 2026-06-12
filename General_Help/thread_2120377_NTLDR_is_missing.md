---
title: "NTLDR is missing"
date: 2013-02-26
forum: General Help
---

### Post by Steve Francis on 2013-02-26
I have a dual boot system Ubuntu 10.04 / Windows XP with four hard disks.

I attempted to disable three of these disks in Windows by removing their drive letters in Disk Management.

System rebooted with message NTLDR is missing. Press CTRL+ALT+DEL to reboot. However, when I reboot, the same message appears.

Booted up from the Windows XP CD and ran 'fixboot' but this has stopped the problem.
Have I corrupted grub file?

Any suggestions on how to fix, please?

Thanks

---

### Post by oldfred on 2013-02-26
With 4 drives you have 4 MBRs. I would have Windows in the MBR of the Windows drive and grub in the other drives even if you have Ubuntu on same drive as Windows. But better if each system is on a separate drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Steve Francis on 2013-02-26
> **oldfred said:**
> With 4 drives you have 4 MBRs. I would have Windows in the MBR of the Windows drive and grub in the other drives even if you have Ubuntu on same drive as Windows. But better if each system is on a separate drive.


Thanks oldfred. (I remember that you helped me out a year or two ago :))

I didn't even know that each disk had its own MBR, so my ignorance is an impediment to solving this. Just for information, XP is installed on its own separate drive (/dev/sda, I think) which is about 75GB. Ubuntu 10.04 is installed on /dev/sdc

       > **oldfred said:**
> Post the link to the BootInfo report that this creates.

The link is [http://paste.ubuntu.com/5568607/](http://paste.ubuntu.com/5568607/)

I used Ubuntu 12.04 live disk to create this link. The installed version of Ubuntu on my pc is 10.04

The link shows an error at line 650. Is this the problem?

I haven't pressed the button to repair the boot yet. Should I?

---

### Post by oldfred on 2013-02-26
The CD's are oversize now but still work. It seems the tools used see the CD is beyond the standard end and give the error. You can ignore that one.

Not sure why you are getting ntldr missing error. That usually is a PBR issue in Windows as you are trying to boot from a PBR - partition boot sector that is wrong or is not bootable and does not have the Window's ntldr.

Did you change boot order in BIOS. You should be booting from sdc, your 500GB drive.

Boot-Repair will not fix that Windows issue. It will only fix minor boot issues. You will need your XP disk and run chkdsk and fixBoot from it.

Boot-Repair also does not fix grub legacy. It suggests purging grub legacy and installing grub2 as that is the standard. If you still want grub legacy do not run Boot-Repair.

You still have 10.04 with grub legacy. When you upgrade you should change to grub2. You must have upgraded from older versions as grub2 was the standard with 9.10 and later versions.

You do have a lot of kernels. I might go into synaptic and uninstall all but the last couple.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
 In synaptic or software center search for linux-image to choose to purge old ones
 Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Steve Francis on 2013-02-26
> **oldfred said:**
> Did you change boot order in BIOS. You should be booting from sdc, your 500GB drive.

I ran boot-repair again and this time clicked on the 'Recommended repair' button. GRUB was installed on all disks (don't know if it was before this problem started).

Followed the instructions and the repair finished successfully.

I'm back in business! Can boot up either to XP or Ubuntu.

Thanks oldfred!

> **oldfred said:**
> You do have a lot of kernels. I might go into synaptic and uninstall all but the last couple.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
 In synaptic or software center search for linux-image to choose to purge old ones
 Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

When I click on Synaptic Package Manager, I get the following Error message
[FONT=Courier New]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/FONT]

I wonder if it was because I repaired a Ubuntu 10.04 installation using a 12.04 live CD? Will investigate further...

---

### Post by Steve Francis on 2013-02-26
> **Steve Francis said:**
> When I click on Synaptic Package Manager, I get the following Error message
[FONT=Courier New]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/FONT]

I wonder if it was because I repaired a Ubuntu 10.04 installation using a 12.04 live CD? Will investigate further...

Hmm

In terminal, entered
[FONT=Courier New]sudo rm /var/lib/dpkg/lock[/FONT]
then
[FONT=Courier New]sudo dpkg --configure -a[/FONT]
which gave
[FONT=Courier New]Setting up grub-pc (1.98-1ubuntu13) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc[/FONT]

I then tried
[FONT=Courier New]sudo apt-get update[/FONT]
which seemed to go ok.

I can now get into Synaptic Package Manager. Strange...

---

