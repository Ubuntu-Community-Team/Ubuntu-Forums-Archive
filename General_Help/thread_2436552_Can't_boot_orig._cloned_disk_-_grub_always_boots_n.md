---
title: "Can't boot orig. cloned disk - grub always boots new partition, not old one"
date: 2020-02-08
forum: General Help
---

### Post by palex1919 on 2020-02-08
Here's the deal... cloned a partition (sda3) to another drive's partition on same machine (sdb2). Even though
grub lists both at boot time as sda3 and sdb2 it only boots the new one (sdb2) regardless of what I chose. Gave sda3 a new UUID because they
had the same after cloning but grub STILL only boots the new one.
PS I ran boot-repair from a live USB version. Problem exists.

---

### Post by GhX6GZMB on 2020-02-08
Take a look in /etc/fstab, that's where the device names and corresponding UUIDs are defined.

---

### Post by palex1919 on 2020-02-08
so I adjusted the /etc/fstab. here this blkid listing. the thing is (and I really am not a grub expert by any means) grub.cfg still has the old (UUID ) in it>?! what to do? it says do not edit the file and mkconfig just recreates the same nonsense...

peter@Elementary:~$ blkid
/dev/nvme0n1p2: UUID="C2767DC4767DBA2D" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e04bff41-4cfa-496a-8e24-e6625f7ace90"
/dev/sda1: UUID="8299-8E76" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="5808261c-384a-4b3a-aea3-677e599383ba"
/dev/sda2: LABEL="ExtraWinSpace" UUID="F2E0AC37E0AC03C7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="ba132f06-e3aa-4b6e-a9e0-25f08014b3d0"
**/dev/sda3: UUID="861dbe97-67c3-4fca-95ad-27e8e4b1f33e" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="4365bb5a-b4ca-4ec2-acbe-b52b0d86115a"**
/dev/sda4: LABEL="Mint" UUID="3fc22aa2-572e-4916-9073-2ada6407e1e2" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="b3368149-43b3-4ea5-a545-460f3aab4345"
/dev/sda5: UUID="3e41c544-5cd9-4041-8d66-45ec52dadcff" TYPE="swap" PARTUUID="92271d5d-8fcd-4ad6-99cc-4972d9970388"
/dev/sda6: LABEL="Manjaro" UUID="2086-EE19" TYPE="exfat" PARTLABEL="Basic data partition" PARTUUID="5eb3ce28-7cbc-4d55-9325-250d02a1e970"
/dev/sdb1: UUID="8299-8E76" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="5dad54c4-692c-4fa3-aa03-bb8743dc3bda"
**/dev/sdb2: UUID="e29f4d1f-0996-4fa9-b70a-0f2a368270e4" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="df39badb-a43f-45b1-b865-9a8e30381fe1"**
/dev/sdb3: UUID="762926f6-bf08-40cd-aaa0-87ab0e46f765" TYPE="ext4" PARTLABEL="ext4Extra" PARTUUID="2333ffa0-07c0-4441-9321-c8db3c9b0b10"

---

### Post by palex1919 on 2020-02-08
the section in question in the grub.cfg file on /sda - the UUID is clearly the SAME as /sdb2 although i fixed the fstab file>?!

menuentry "elementary OS 5.1 Hera (5.1) (on /dev/sda3)" --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e29f4d1f-0996-4fa9-b70a-0f2a368270e4' {            
            insmod part_gpt            
            insmod ext2            
            set root='hd0,gpt3'            
            if [ x$feature_platform_search_hint = xy ]; then            
              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e29f4d1f-0996-4fa9-b70a-0f2a368270e4            
            else            
              search --no-floppy --fs-uuid --set=root e29f4d1f-0996-4fa9-b70a-0f2a368270e4            
            fi            
            linux /boot/vmlinuz-5.3.0-28-generic root=UUID=e29f4d1f-0996-4fa9-b70a-0f2a368270e4 ro quiet splash $vt_handoff            
            initrd /boot/initrd.img-5.3.0-28-generic

---

### Post by yancek on 2020-02-08
The menuentry for Elementary in the grub.cfg file you posted shows the UUID for sdb2 which you posted earlier:  **/dev/sdb2: UUID="e29f4d1f-0996-4fa9-b70a-0f2a368270e4".  You need to change that to the UUID for sda3.  Are you booting from sda?**

---

### Post by palex1919 on 2020-02-08
Yes, but how to change that in the boot.cfg file? Just do it with nano as there is a big warning NOT to edit the file :) There are several entries when grub comes up... not sure from where it is actually coming from.

---

### Post by oldfred on 2020-02-08
There are times to violate rules.
Issue normally is if you manually edit grub.cfg, it is lost on next update of grub, kernel, or anything that re-runs 'sudo update-grub'. 
If editing it allows you to boot, do it. You only need to edit the one line you are using to boot. Then from within install run the updates.

But generally you cannot use dd or any method to copy a gpt partition, you can copy a gpt drive, but cannot have both drives connected when you reboot. Issue is with gpt partitioning, it has GUID in primary partition table, partition and in backup partition table.

Post this for each drive and see if issues.
sudo gdisk -l /dev/sdX where X is each drive sda, sdb, sdc etc or nvme0n1 or mmcblk0

---

### Post by GhX6GZMB on 2020-02-09
you've forgotten to run sudo update-grub.

---

