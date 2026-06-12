---
title: "GRUB failing to load kernel from 1st HDD when 2nd HDD changed"
date: 2023-06-19
forum: General Help
---

### Post by AR_Kozz on 2023-06-19
Old system:

1 TB Ubuntu 22.04
500GB Windows 10

swap out to 

1 TB Ubuntu 22.04
250GB Ubuntu 22.04

to do some quick backups. The 1TB is the default drive, 1st in computer's boot order.

Booting it brings up the usual GRUB menu, but selecting Ubuntu from there results in an error stating that the kernel fails to load. 

Why is this? The computer sees this drive as SATA3 in both cases. Only SATA0 has been changed. Naturally trying to boot Windows wouldn't work, but there's no apparent reason why grub should break for the primary drive. 

Ask 1) Since this is only a temporary drive swap, I'd rather not have to go reconfigure GRUB and then switch it back. Can I manually make it load the correct kernel and boot? 

2) I never use GRUB to boot from the 2nd drive anyhow; I do that from the computer's boot menu. Can I make GRUB on the 1st drive ignore the 2nd drive, and would that prevent this?

---

### Post by oldfred on 2023-06-19
Drive order is set by UEFI/BIOS.
I often have to manually edit my grub when I plug in a flash drive as sdc. But on reboot flash drive becomes sda & every other drive changes one. So I just edit my hdX up one as I boot.

Also drive order is often set by port order. So best to have your default boot drive plugged into SATA0 port. Did you plug temporary drive into lower port number that your preferred default drive?
I now find my NVMe drive is first in boot order, but listed last in most tools once booted.

I now often use labels.
See 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
Use labels and configfile to boot another install in 40_custom
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359) &
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)

---

### Post by AR_Kozz on 2023-06-19
Thanks for the reply. Yes, I've tried tweaking the order, both in UEFI and by manually switching the cables between the ports on the mobo. But the order isn't the problem, I can already manually select which drive to boot from. 

The problem is that whenever drive 2 is different from the original W10 drive, then drive 1, when selected to boot, reports that /boot/vmlinuz... is not found.

Because the swapped-in drive 2 has an older kernel version, and GRUB looks for the newer one, I can tell that's the grub on drive 1.

I have also run update-grub on both linux drives with no other drive present, to purge the memory of the windows drive, hoping that had something to do with its confusion. 

Just now I disconnected drive 2, and now drive 1 boots fine. The correct vmlinuz is right where it should be on the drive. So maybe something in the grub.cfg (e.g. references to hd1) is directed to the other drive if one is present. But... this doesn't happen when that other drive is the one with W10 on it.

My suspicion is that Grub2, being fancy and automated, sees two linux filesystems and picks the wrong one, even if the grub itself is on the right one.

---

### Post by oldfred on 2023-06-19
Mint while not an Ubuntu official flavor uses "Ubuntu" as its boot entry & folder in ESP - efi system partition.
So depending on whichsystem does a major update to grub, it will be default boot and update its grub menu, if os-prober is on. Grub now recommends os-prober be off in grub's settings.

So you can have an update in one system that becomes default boot, but refers to older boot files in the other install.
This is why I totally control booting with os-prober off and my other boot stanzas in 40_custom.

---

### Post by AR_Kozz on 2023-06-20
Thanks, I'll look into os-prober. But I still don't understand how this can happen when the grubs are on two separate hard drives. I've never updated either one with the other one installed. Neither could have been affected by an update to the other one. 

I've been encountering this for years - grub failing when I install two HDDS with bootable linux partitions, even if they have never interacted or been installed at the same time. In fact I can't recall ever getting either to boot. GRUB goes cross-eyed for some reason.

---

### Post by tea for one on 2023-06-20
> **AR_Kozz said:**
> Thanks, I'll look into os-prober. But I still don't understand how this can happen when the grubs are on two separate hard drives. I've never updated either one with the other one installed. Neither could have been affected by an update to the other one. 
Grub is updated automatically if new kernels have been installed (e.g. a security patch).

---

### Post by AR_Kozz on 2023-06-20
Thanks. Unfortuately, neither filesystem ever received any kind of update while the hard drive with the other filesystem was connected, so it doesn't explain why connecting one would affect the boot performance of the other.

---

### Post by oldfred on 2023-06-20
To see all the details of your configuration.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do not run any autofix. And it defaults to making first install it finds as new default boot. You have to use Boot-Repair's advanced mode & choose an install, if you want any other than what it thinks is default.

---

### Post by AR_Kozz on 2023-06-21
[https://pastebin.ubuntu.com/p/8jdmYKb8pt/](https://pastebin.ubuntu.com/p/8jdmYKb8pt/)

A couple minor errors in what I've reported above:

1) the older filesystem is 20.04, not 22.04
2) the older can boot under the current configuration, connected to SATA0. The newer as SATA3 cannot, and couldn't as SATA0 when I tried that in the past.

Still true that neither has been upgraded with the other present. 

Before running boot-repair from usb, I ran and saved a copy with just the 22.04 drive connected, to compare to the info with both connected. All the information for 22.04 alone is identical to what's in the paired report, except that

- boot-repair mounted it as sdb, and the 20.04 drive as sda.
- no "sdb5/etc/grub.d/35_fwupd" section. Might be from using different versions of boot-repair.

edit: ran it with the sata connections switched. Now 22.04 is sda and 20.04 is sdb. In both cases this app recommends putting the grub from /dev/sdb5 (not the same in each test) into the MBR on both discs. 

[https://pastebin.ubuntu.com/p/K3pMCRVWwz/](https://pastebin.ubuntu.com/p/K3pMCRVWwz/)

---

### Post by yancek on 2023-06-21
When looking at boot repair report, it appears one drive was cloned as the UUID for sda5 and sdb5 is identical.  Shown on lines 237, 203, 247 are the UUIDs in different locations for sda4.  THat same UUID is shown for sdb5 on lines  208, 314 and 324.  Did you remove the windows drive before running boot repair as there is no sign of windows in the report.  You also have an EFI capable machine but have both Ubuntu installs in Legacy mode and apparently windows is also Legacy as there is not UEFI entry on the motherboard output for windows.  You need to change the UUID of either sda5 or sdb5.  A simple google search to change UUID in Linux should provide many sites with an explanation of this process.

---

### Post by AR_Kozz on 2023-06-21
good catch on the UUID match. Correct that the newer drive started as a clone of the older. I was unaware that the cloning went so far as to make an outright impostor! These are supposed to be unique per device, no? 

Next time I do that, I'll try to clone just the filesystem. 

Thanks for the other info, but this seems to be what matters here. Could this be worked around easily by just editing the grub command?

---

### Post by oldfred on 2023-06-21
Cloning is more for copying system to a new drive & removing old drive.
If keeping old drive you have to change UUIDs, update fstab, reinstall grub and anyplace else UUID is used.

Often better just to do a new install & restore from backups. Becomes good test that backups include everything you need to fully restore system, when you still have old drive to add any missing data. Backup at minimum should include /home, all your hidden user configuration files, user data & list of installed apps. If server apps in / (root) like database or web, those also need to be backed up. If you edited system wide setting in /etc, back those up, but if new version, you may not want to just restore those as sometimes things change.

---

### Post by AR_Kozz on 2023-06-22
> it appears one drive was cloned as the UUID for sda5 and sdb5 is identical. Shown on lines 237, 203, 247 are the UUIDs in different locations for sda4. THat same UUID is shown for sdb5 on lines 208, 314 and 324. 

Good catch. Correct, the newer filesystem started as a clone of the older. I was unaware this would cause GRUB to be unable to tell the difference between them. 

Before changing the UUID's, I tried simply working around by editing the GRUB command. That eventually succeeded in booting the correct root partition, but then it reverted to the old home partition. Which interestingly still worked. 

I thought I might fix that by pointing fstab to the correct /dev/sdx, but went ahead and changed the UUIDs instead. 

I didn't change the UUID for swap. Unless someone jumps up within the next few hours saying I should, I'll mark as solved. Thanks for all the kind help.

---

