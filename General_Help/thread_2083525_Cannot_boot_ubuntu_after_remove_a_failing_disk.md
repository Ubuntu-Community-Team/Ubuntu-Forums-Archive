---
title: "Cannot boot ubuntu after remove a failing disk"
date: 2012-11-12
forum: General Help
---

### Post by luyiming on 2012-11-12
Our ubuntu server has four hard disks, but we didn't make them a RAID. Yesterday, one of the disk was reported to be failing, and this disk was /dev/sdb and was mounted as /data (was used to store data), but the server cannot boot up after we remove this disk. We tried umount it or deleted it in the 'Disk ultility', but didn't work. Is there any way to just remove this disk and avoid reinstall the ubuntu. Thank you very much!

---

### Post by ercherramon on 2012-11-12
This happened with the damaged disc that changed, I changed the GRUB, I think. just regenerate it using a Ubuntu LiveCD. you enter the option: Try Ubuntu and run:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
grub-install --recheck /dev/sda
```then from the new grub choose the option reconfigure grub or boot file.

---

### Post by oldfred on 2012-11-13
Do you have a liveCD or USB of the same version of Ubuntu as your server install. If so run this from that liveCD or download the full repairCD. Then post link to BootInfo report.

Were you booting from BIOS the sdb drive? Then grub maybe was installed to wrong drive? BootInfo report will give us those type of details.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

