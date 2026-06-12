---
title: "No boot device found - how to restore GRUB?"
date: 2023-06-09
forum: General Help
---

### Post by trifo75 on 2023-06-09
Hi,

I have an Ubuntu 22.04 server instance, installed az a VirtualBox guest. The original install to a virtual disk, partitioned into 3 pieces:
sda1 - 1MB (space to bootloader?)
sda2 - 18GB - LVM PV for all system FS-es
sda3 - 1GB - /boot FS

Later I added another virtual disk (sdb) which became a PV for another VG, holding www data.

At this point I wanted to experiment with disk migration. So I added a 3rd disk (sdc) with the intent to migrate the system from sda. For this I tried the following:
[LIST]
[*]created similar partition scheme:
[LIST]
[*]sdc1 - 1M
[*]sdc2 - 1GB - /boot
[*]sdc3 - 18GB - LVM PV for system FS-es
[/LIST]

[*]created the new /boot FS to sdc2 and copied content from the original /boot
[*]modified fstab to reflect the UUID of the new /boot FS
[*]migrated LVM data from sda2 to sdc3 with LVM tools
[*]dd the content of sda1 to sdc1
[*]run ```
grub-install --boot-directory=/boot /dev/sdc
``` - I suspect this is not enough
[/LIST]

At this point the system boot is working fine.

When I try to remove the original OS disk (sda) from the VirtualBox config, then I just get a "No bootable medium found" message. 

Tried to boot from live DVD then repair GRUB, but no luck. I think that there is no bootloader on the new disk, but I did not find any working way to install one. 
Having GPT partition table I do not even see a bootable flag. 

Partitions on the original disk:
```

root@ubuntu1:/mnt# sfdisk -d /dev/sda
label: gpt
label-id: DB52473B-4E82-4A97-8DDD-204C088F2B1B
device: /dev/sda
unit: sectors
first-lba: 34
last-lba: 42414718
sector-size: 512


/dev/sda1 : start=        2048, size=        2048, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=A17A06E9-596C-44A5-AA43-51736FA57753
/dev/sda2 : start=        4096, size=    37748736, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=7CE8D2AD-7961-4BD0-9A51-67DE07DA94CE
/dev/sda3 : start=    37752832, size=     2097152, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=D7FA75FD-DBA0-43F7-9958-936A53BAACDA



```

Partitions on the replacement disk:
```

root@ubuntu1:/mnt# sfdisk -d /dev/sdc
label: gpt
label-id: C14BFCAD-C4DD-41A8-87D5-5632D4058378
device: /dev/sdc
unit: sectors
first-lba: 34
last-lba: 42404379
sector-size: 512


/dev/sdc1 : start=        2048, size=        2048, type=21686148-6449-6E6F-744E-656564454649, uuid=4450ADA8-7D29-4C9C-B44C-F098209EB92B
/dev/sdc2 : start=        4096, size=     1949030, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=0CC68487-054B-470F-A7F2-C461ED83B1BE
/dev/sdc3 : start=     1953792, size=    40448000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=FF6B6C55-8AB3-4F0F-A479-CAB5DABC8AEE



```

The "Enable EFI" option in VirtualBox is not checked, thus I think that the partition type of the firtst partitions doesn't matter. Is it true?

Now I have 3 questions:
[LIST]
[*]how do I know which disk will be used as boot device? On MBR disks I can see the asterisk (*) on the boot partition. What should I see here?
[*]how to make my system bootable without the first disk?
[*]what should be the correct method to replace a disk in a similar situation?
[/LIST]

I am googling around for days but found nothing. I would really apperciate some help.

--Trifo

---

### Post by oldfred on 2023-06-09
With gpt a 1MB partition is typically the bios_grub partition for install of part of grub. BIOS boot on gpt uses protective MBR, bios_grub & files in install for grub to boot.

But with gpt, you should not use dd on a partition. Gpt has GUID in partition table, backup partition table & partition which all must be in sync. DDing a partition probably copied GUID so the GUIDs on sdc do not match. 

Better to have just used rsync and then edited fstab and any other entry using device & reinstalled grub.

I typically suggest new install and restore from backup when installing to new drive. That also confirms your backups work as intended while you still  have old drive to recover any missing data in backup.

Check for duplicate UUID from dd to sdc & duplicate GUIDs.
If you disconnect sdc, can you boot from sda?

---

### Post by trifo75 on 2023-06-09
Thanks for your reply!

Well, so grub_bios partition is just a placeholder to keep the place of old style MBR? bios_grub was a string that I'vs seen googling around, but I forgot it when I wrote my question. 

Since my LVM PV is residing on sdc3, I can not boot without sdc. The VG, which holds OS filesystems (is called vgos now) has only one PV.

Now I've found some interesting phenomena:
* running grub-install and  grub-mkconfig did not help
* booting with all 3 disks I can see vgos LVs, thus I can set root and most probably would be able to boot
* from live CD, without the original OS disk (hd0) I can not see LV-s from vgos, just the LV from the other data VG. It seems that the system can not see the VG descriptor, or so.  

What can this mean?

I am an AIX admin guy and AIX supports this kind of operation so smoothly...

So, the proplem still persist, I can not boot from the new OS disk.

---

### Post by yancek on 2023-06-10
> Well, so grub_bios partition is just a placeholder to keep the place of old style MBR 

This partition is used to store Grub boot code on a GPT drive which has an OS installed in Legacy mode rather than the standard EFI usually used of GPT drives.  Grub would have code in the MBR, the bios_grub partition and on the system partition.  Most Grub code is on the system partition.

Did you check the suggestions in the post above by oldfred and make those changes?

---

### Post by oldfred on 2023-06-10
I have preferred to have grub installed to same drive as OS.
With UEFI, Ubuntu default installs grub to ESP - efi system on first drive.
With BIOS, I still think it is better if grub fully installed to same drive as OS.
Do not use LVM, so do not know all the details, but grub may need extra modules loaded in boot stanza as .mod file.

When first converting from old BIOS only system to new UEFI system, I always added both  a bios_grub and an ESP - efi system partition to every new or changed drive and only used gpt. Now I just use an ESP for UEFI boot.

---

### Post by trifo75 on 2023-06-12
@oldfred - This system is using BIOS. At least "Enable UEFI" switch was turned off in VirtualBox, when I installed the OS. 

It seems that there are multiple problems whith my config:
* I suspect that on the new drive (sdc) there is no GRUB bootloader code on the beginning of the disk. - How can I check if there is?
* when I remove the original system disk - which is not part of the LVM config - grub do not see the system volume group at all. Tried to start grub shell booting from live DVD. After issuing **insmod lvm** I can clearly see the contents of my data VG, but not the system. Thus I do not have access to the root fs. When I put the original disk back, I can access my OS VG as well.

---

### Post by oldfred on 2023-06-12
I do not use LVM, so do not know details of grub's configuration for LVM.
You can still run Boot-Repair's report which will output grub's configuration files & lots of useful info.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If using Boot-Repair to install grub, you need to use its advanced mode to be able to choose an install and choose which drive has the boot loader. And make sure the LVM volumes are mounted.

---

