---
title: "So i forgot to create a boot partition (gpt table)"
date: 2014-10-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-10-24
So i have a GPT partition table
i installed the mini iso like i would if it was a MBR table
well it installed but it can't boot, how do i go back an create this partition without a reinstall (slow 2.5" 5400rpm hdd and all)
i have the unallocated space ready for it

---

### Post by ajgreeny on 2014-10-24
I am not sure that you can do that but it may be worth trying using a live DVD or USB with gparted, though gparted gives you no option of making an EFI partition in its list, so you may have to simply reinstall.  Or is this not a UEFI installation even though you have GPT partitions?

But if you have not managed to boot yet why not just reinstall?

I did a similar thing two days ago, installing in UEFI mode, but totally forgetting to change the system to a GPT partition table.  The machine came with an unlicensed Win7 on it (for the manufacturer to test it before sending it to me) which was installed in BIOS mode.  I wanted to keep up to date and use UEFI mode which I already have on my desktop machine, but just did not think about having to make a new GPT partition table, so after reboot of Xubuntu 14.04 64bit the machine could not find a hard disk.  I quickly figured out why and reinstalled.

Now all works brilliantly.

---

### Post by pqwoerituytrueiwoq on 2014-10-24
reason is slow 2.5" 5400rpm hdd and all

---

### Post by oldfred on 2014-10-24
If booting in BIOS mode, it does not need a /boot partition but you must have a bios_grub partition.
The bios_grub partition is 1 or 2MB unformatted with the bios_grub flag in gparted. It can be anywhere on drive.

If booting in UEFI mode then you do need an efi partition. That is not a /boot partition. The efi partition is supposed to be first or near start of hard drive, but have seen some with it fairly far into drive. It must be FAT32 with the boot flag using gparted.

```
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32      msftdata
```

I have both so I can reconfigure flash drive to boot with either UEFI or BIOS.
You set the efi partition as the efi partition with the boot flag if using gparted.
If using gdisk the efi partition is ef00 and bios_grub is ef02.

---

### Post by pqwoerituytrueiwoq on 2014-10-24
gparted is not letting me manage the flags on a unformatted partition

idk what type of boot i am using uefi/bios, i just know all i need is that 1mb partition required to boot with gpt

---

### Post by oldfred on 2014-10-24
Did you partition with MBR(msdos)? Then you cannot create bios_grub. 

It should give you this if gpt.

I also see in Disk Utility (12.04) and Disks (14.04) settings. Disks has it hidden in added tools in icon in upper right corner.

---

### Post by pqwoerituytrueiwoq on 2014-10-25
ok i managed to get it working
either it did not work on the live usb or i forgot to apply the cleared partition to the drive before trying to add a flag in gparted
thanks, it now boots
*i formated it from my main install, i have hotswap bays in my desktop and a 2.5 -> 3.5 adapter to use with it

---

