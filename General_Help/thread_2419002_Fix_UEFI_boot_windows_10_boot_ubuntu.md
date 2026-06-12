---
title: "Fix UEFI boot windows 10 boot ubuntu"
date: 2019-05-15
forum: General Help
---

### Post by LMH1 on 2019-05-15
```

sudo fdisk -l

Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SAMSUNG MZHPV512
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
/dev/sda1  2138112   3115007    976896   477M EFI System
/dev/sda2   923648   1128447    204800   100M EFI System
/dev/sda3  1128448   1161215     32768    16M Microsoft reserved
/dev/sda4  1161216   2137778    976563 476,9M EFI System
/dev/sda5  3115008 488396799 485281792 231,4G Linux filesystem


```
windows 10 on /dev/sdb4
```

insmod part_gpt
insmod fat
set root='hd1,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1--hint-efi=hd1,gpt3 --hint-baremetal=ahci0,gpt1  2E38-2342
else
  search --no-floppy --fs-uuid --set=root 2E38-2342
fi
chainloader /efi/Microsoft/Boot/bootmgfw.efi


```

How to fix windows 10 boot grub2? I get can not find 
bootmgfw.efi files, need to rapair windows installation.

---

### Post by yancek on 2019-05-15
Your fdisk output does not show any partitions on device sdb where you say your windows system is.  Try running parted or gdisk and post the output.  The partial grub.cfg output you posted would seem to indicate that the file is on sdb1 but your output shows nothing of that partition.  You also have two EFI partitions on sda which is not correct.  You might try mounting then consecutively to see what you have there as that is where the bootmgfw.efi file usually reside.

Did you try running sudo update-grub?  What results?  What happened to your windows system?

---

### Post by LMH1 on 2019-05-15
> Number  Start   End     Size    Filsystem  Navn                          Flags
 2      473MB   578MB   105MB   fat32      EFI system partition          oppstart, esp
 3      578MB   595MB   16,8MB             Microsoft reserved partition  msftres
 4      595MB   1095MB  500MB   ntfs       Basic data partition          oppstart, esp
 1      1095MB  1595MB  500MB   fat32                                    oppstart, esp
 5      1595MB  250GB   248GB   ext4



> 
 Windows Boot Manager på /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Windows Boot Manager på /dev/sdb2@/efi/Microsoft/Boot/bootmgfw.efi


Its all i get.
Its look like sudo update-grub did not do anything its because it did not find any different so i must delete some of UEFI loader?

---

### Post by Rubi1200 on 2019-05-15
To help us understand what is going on please boot the computer from a liveCD/USB and post the boot info summary here (link in my signature). Note, please do NOT repair anything just let us see the summary results so we can advise on next steps.

Thanks.

---

### Post by oldfred on 2019-05-15
You are showing 3 ESP- efi system partitions. You can only have one per drive on the FAT32 partition for UEFI boot.
If Windows is BIOS, then boot flag is on partition with Windows boot files, but drive then must be MBR, not gpt. Since gpt then Windows must be UEFI boot.

Your sda2 looks like the typical size of a Windows ESP. That may be the only one that should have boot flag if FAT32.
Use gparted or Windows repair disk to remove boot flag/esp from other partitions.

Then run Boot-Repair & post link per Rubi1200's suggestion.

---

### Post by LMH1 on 2019-05-16
Hi how to add virtual disk mountet from iso to grub config.
So i did not need memory stick or DVD.

Because issue here i need to format memory stick from windows 10 to ubuntu, so its better to mount it as drives and boot it.
But i did not know how to add it to grub so i get one more "reinstall ubuntu or live DVD" item.

---

