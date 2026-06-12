---
title: "Degraded RAID10 boot not working when &quot;install&quot; drive is missing (GRUB2/EFI)"
date: 2014-04-17
forum: General Help
---

### Post by troep on 2014-04-17
When installing ubuntu 13.10, I used the installer to configure my EFI-enabled system as follows:

Six ssds, all with the same GPT partitioning table:
partition 1:  250 vfat EFI partition
partition 2: ~95GB raid partition
Created an md RAID10 device using partition 2 from all 6 drives. The md device contains three logical LVM volumes: boot, swap and root.

The installer automatically filled the EFI partition sda1 with the grub EFI files & cfg. This is why I call sda the "install" drive. After installation, the system booted from /dev/sda without a problem.

My goal is to get the system to boot from any of the six drives, even when one of the drives (any of the drives) is missing. To accomplish that, I did the following:

- Set BOOT_DEGRADED to true
- Copied the EFI files from sda to the other 5 drives. After this, the bios automatically added the efi boot options for all drives, and there are now 6 'ubuntu' efi options in the system bios.

After that, the system boots perfectly from any of the six drives when no drives are missing 
Additionally, the system boots perfectly from any of the six drives when a single drive is missing, as long as the missing drive is NOT /dev/sda.

When I pull /dev/sda and try to boot, grub shows up fine, and booting (at first) seems identical to a 'normal' degraded boot: md tells me the RAID device has been degraded and successfully starts the raid in degraded mode. After that, booting stops with no errors shown ([screenshot]("http://imgur.com/SHqEaST")). If I power down, readd sda and reboot, the system boots fine again (albeit obviously with degraded raid). There are no logs from the failed boot attempt.

I went through all the grub configs to make sure sda is not referenced anywhere, and I cant find any mentions of sda, sda1 or sda2 (or their UIDs). However, I am not an expert and could have easily missed something. The only reference to sda is in /etc/fstab; sda1 is mounted (by uid) to /boot/efi. I dont know the significance of this line for booting the OS (it was my understanding the EFI files were only used to start grub, which starts fine from any of the other 5 drives). Is this likely the cause of the freeze? How do I change this so the system uses a different drive if sda is not available? Of course, I could be missing something completely different, so any other ideas are very much appreciated.

---

### Post by oldfred on 2014-04-17
I do not know details of RAID.
And I never understood exactly how grub in efi installs knew where to look for the rest of grub.
With BIOS boot, it has a core.img file that is in the sectors after the MBR that are loaded. That is customized so it can find the install.
But with UEFI, I do not see any files like that.

Some with RAID added config file to help grub find its install.
And the entry in fstab, is more for updates to grub to know that it is an efi install and to update entry in efi partition. Maybe there is a hidden core.img somewhere in the efi folder?

 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

### Post by troep on 2014-04-23
Thanks for your reply.

I think the grub EFI knows where the rest of grub is by looking at the grub.cfg on the efi partition. This grub.cfg tells grub where the boot partition is and where the 'real' grub.cfg lives.

Thanks for posting the links, however, I don't think they are relevant for me as all three links are about getting stuck at the grub CLI or rescue shell. My problems occurred later in the boot process.

I decided to simplify my configuration by not using LVM and by reducing the number of disks. I am now using a two disk RAID1 setup with two raid devices, one for swap and one for root. This setup works well in 13.10 and degraded boots work fine with either of the two disks missing. 

Funnily enough, when I tried to replicate the working setup on a new install of 14.04, it did not work as expected. Degraded boots would complete only once, any subsequent boots would throw a 'device or resource busy' error when mounting the root filesystem and drop an initramfs shell. I have decided to stay with my working 13.10 setup for now and not use 14.04.

---

