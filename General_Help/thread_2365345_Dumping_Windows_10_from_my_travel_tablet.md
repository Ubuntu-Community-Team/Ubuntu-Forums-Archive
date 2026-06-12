---
title: "Dumping Windows 10 from my travel tablet"
date: 2017-07-05
forum: General Help
---

### Post by makem2 on 2017-07-05
I have a tablet running Windows 10 and Xubuntu and have decided to go Linux solely with a Virtualbox Windows 10 for those very infrequent times when I must use Internet Explorer.

I have given up on the idea of using a Bluetooth keyboard to choose OS at boot.

I ask for advice on which partitions related to windows that I can safely remove in a running Xubuntu instance. Or, using a live USB Xubuntu if necessary.

My partitions are such:

sda1 Basic Data partition ntfs label Recovery Size 450 MiB

sda2 EFI System partition fat32 Mount Point /boot/efi size 99 MiB

sda3 Microsoft Reserved partition 16 MiB

sda4 Basic Data partition ntfs size 73.15 GiB flag msftdata

sda5 ext4 Mount Point / size 27.94 GiB used 5.88 GiB

sda6 ext4 Mount Point /home size 27.94 GiB used 1.62 GiB

sda7 linux-swap size 1.86 GiB used 0.0 MiB

sda8 ntfs label data size 101.44 GiB used 4.84 GiB

I would like to end up with a  separate /home partition, no swap as the HD is an SSD and a data partition formatted ntfs available to Linux and the Virtualbox Windows 10. 

I assume the VB would need to be installed in the /home partition therefore that partition would need to be of sufficient size.

I don't game, only use the machine for organising DIY travel arrangements as and when travelling.

I could lose all data in a complete re-install if this is really necessary but would prefer not to.

It seems to me that I could whilst running Xubuntu, remove all related Windows partition using gparted.

sda1; sda3, sda4 and sda7. I am not sure about sda2.

If those were removed, would it be possible to enlarge the /home partition if necessary and expand sda8 to include the sda4 space without losing data? I am able to copy all data to a remote SSD as backup.

I appreciate the 'sdax's' would change. I forget why sda5 and sda6 are identical size.

TIA.

---

### Post by yancek on 2017-07-05
sda2 is your EFI partition which you will need if you have windows/Xubuntu installed using UEFI.  You can find that out by mounting sda2 and checking to see if you have an Xubuntu directory.  It will probably be name ubuntu but I don't use Xubuntu so I'm not sure.  You could also check by booting Xubuntu and running this command:

> [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

If it shows EFI boot and you delete that partition, your computer will be unbootable.

If you are using UEFI and GPT partitioning your partition numbers should not change as they are all primary.  If you had been using logical partition within an Extended partition, any partition numbered 5 and higher would be logical and if you delete a partition, any partition with a higher number will drop down one.  For example, deleting sda5 would change sda6 to sda5.  The info you posted would indicate that you have GPT but you haven't posted the full output of fdisk or gdisk which would be more accurate.

To expand a partition (enlarge it) it would need to have contiguous space to which it could expand and in your situation, that is not the case as you have your system partition (sda5) between your windows partition (sda8) and sda4.  You don't really have any space you could use to enlarge /home (sda6) except for swap (sda7) so the same problem here. 

You cannot change any partitions while they are mounted which would definitely include sda5-7.

---

### Post by makem2 on 2017-07-05
From what you say I gather that the simplest way to achieve what I want would be to start from scratch and install a fresh Xubuntu.

That being the case do I have to take account of the EFI? I seem to remember that the latest isos take that into account and are straight forward to install.

EDIT: I realise now that I do not need to make an UEFI install as I am only installing Linux. However if I install Windows 10 in Virtualbox will it need it?

---

