---
title: "mulitple btrfs devices fstab mount"
date: 2014-04-06
forum: General Help
---

### Post by marcuslvgrn on 2014-04-06
I am trying to mount a 4-disk btrfs array in fstab.
This is working with the following line:

UUID=2e905f8f-e525-4114-afa6-cce48f77b629 /mnt/data      btrfs    device=/dev/sda,device=/dev/sdb,device=/dev/sdd,device=/dev/sde 0 0

but how do I specify something other than the /dev/sd* name? (They change between boots)

blkid shows
/dev/sda: UUID="2e905f8f-e525-4114-afa6-cce48f77b629" UUID_SUB="33fef351-9d4d-4952-a759-d01aba34148b" TYPE="btrfs" 
/dev/sdb: UUID="2e905f8f-e525-4114-afa6-cce48f77b629" UUID_SUB="e919a62f-5f5d-4b67-acad-1d68bce88355" TYPE="btrfs" 
/dev/sdc1: UUID="24aa22c4-7732-489a-8023-98635722b370" TYPE="ext4" 
/dev/sdd: UUID="2e905f8f-e525-4114-afa6-cce48f77b629" UUID_SUB="b78482e6-6054-4867-9d68-7841cac91eba" TYPE="btrfs" 
/dev/sde: UUID="2e905f8f-e525-4114-afa6-cce48f77b629" UUID_SUB="335feff3-dffc-40e4-8543-f1be7f6def72" TYPE="btrfs" 

According to the btrfs wiki [https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices#Registration_in_.2Fetc.2Ffstab](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices#Registration_in_.2Fetc.2Ffstab), I should use the PARTUUID, like 

UUID=2e905f8f-e525-4114-afa6-cce48f77b629 /mnt/data      btrfs    device=PARTUUID=335feff3-dffc-40e4-8543-f1be7f6def72,device=PARTUUID=b78482e6-6054-4867-9d68-7841cac91eba,device=PARTUUID=e919a62f-5f5d-4b67-acad-1d68bce88355,device=PARTUUID=33fef351-9d4d-4952-a759-d01aba34148b 0 0

but my btrfs devices are not partitions - the whole /dev/sda is one device, so this doesn't work.
I tried using the UUID_SUB instead, like

UUID=2e905f8f-e525-4114-afa6-cce48f77b629 /mnt/data      btrfs    device=UUID_SUB=335feff3-dffc-40e4-8543-f1be7f6def72,device=UUID_SUB=b78482e6-6054-4867-9d68-7841cac91eba,device=UUID_SUB=e919a62f-5f5d-4b67-acad-1d68bce88355,device=UUID_SUB=33fef351-9d4d-4952-a759-d01aba34148b 0 0

but no luck. What is the correct way to do this?

---

### Post by Rich.T. on 2014-06-14
> **marcuslvgrn said:**
> 

...but my btrfs devices are not partitions - the whole /dev/sda is one device, so this doesn't work.
I tried using the UUID_SUB instead, like

UUID=2e905f8f-e525-4114-afa6-cce48f77b629 /mnt/data      btrfs    device=UUID_SUB=335feff3-dffc-40e4-8543-f1be7f6def72,device=UUID_SUB=b78482e6-6054-4867-9d68-7841cac91eba,device=UUID_SUB=e919a62f-5f5d-4b67-acad-1d68bce88355,device=UUID_SUB=33fef351-9d4d-4952-a759-d01aba34148b 0 0

but no luck. What is the correct way to do this?

I just spent the last couple of days trying to get my head around this and came close to giving up. I spent ages thinking that the reason my btrfs RAID5 array wouldn't automount was to do with it taking too long an thus timing out, so i wasted a lot of time looking into mount options like *bootwait*, *nobootwait* and *nofail*. I actually tried UUID_SUB thing too, without success. ](*,)

I eventually had a brainwave after looking at the /dev/disk/... folders:

```
~$ ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-HGST_HDS724040ALE640_PK1334PBG3GYHS -> ../../sda
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-HGST_HDS724040ALE640_PK1334PBG3HPRS -> ../../sdb
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-HGST_HDS724040ALE640_PK1334PBG3K6YP -> ../../sdc
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-HGST_HDS724040ALE640_PK1381PAKAZ1GS -> ../../sdd
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-Hitachi_HDS724040ALE640_PK1310PAG0VMBJ -> ../../sde
lrwxrwxrwx 1 root root  9 Jun 14 11:24 ata-QEMU_DVD-ROM_QM00004 -> ../../sr0
lrwxrwxrwx 1 root root 10 Jun 14 11:24 dm-name-FileServer--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jun 14 11:24 dm-name-FileServer--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Jun 14 11:24 dm-uuid-LVM-72lObTI2CDOfRRTXconZ6uhLrPTXDDgVJdKARpaNiHAc49tF6wWJ4hrUCH7tsLsP -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jun 14 11:24 dm-uuid-LVM-72lObTI2CDOfRRTXconZ6uhLrPTXDDgVuj2fuFNAOVyaBS0hIni6j8hH4TG7I5Jm -> ../../dm-1
lrwxrwxrwx 1 root root  9 Jun 14 11:24 wwn-0x5000cca22bc063f2 -> ../../sde
lrwxrwxrwx 1 root root  9 Jun 14 11:24 wwn-0x5000cca22bef4304 -> ../../sdd
lrwxrwxrwx 1 root root  9 Jun 14 11:24 wwn-0x5000cca23dc1953d -> ../../sda
lrwxrwxrwx 1 root root  9 Jun 14 11:24 wwn-0x5000cca23dc1980d -> ../../sdb
lrwxrwxrwx 1 root root  9 Jun 14 11:24 wwn-0x5000cca23dc19dc5 -> ../../sdc
```

I realised that if the *device=* option would accept /dev/sda etc. then it might accept other /dev/ subfolders...

So here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/FileServer--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/xvda1 during installation
UUID=c27cedc6-3f29-4e1a-91cd-35bf87295fd8 /boot           ext2    defaults        0       2
/dev/mapper/FileServer--vg-swap_1 none            swap    sw              0       0
# BTRFS RAID5 Volume "Movies"
UUID=13507314-e4d5-44dd-991a-0933507780d6       /home/richard/Movies    btrfs   auto,noatime,nodiratime,device=/dev/disk/by-id/ata-HGST_HDS724040ALE640_PK1334PBG3GYHS,device=/dev/disk/by-id/ata-HGST_HDS724040ALE640_PK1334PBG3HPRS,device=/dev/disk/by-id/ata-HGST_HDS724040ALE640_PK1334PBG3K6YP,device=/dev/disk/by-id/ata-HGST_HDS724040ALE640_PK1381PAKAZ1GS,device=/dev/disk/by-id/ata-Hitachi_HDS724040ALE640_PK1310PAG0VMBJ   0       0
```

And it works! \\:D/\\:D/\\:D/\\:D/\\:D/

---

### Post by yonkiman on 2014-06-17
I just asked a similar question over at [AskUbuntu]("http://askubuntu.com/questions/484291/how-to-use-uuids-in-fstab-for-configuring-btrfs-raid1").  

What ended up working for me was relying on the "Scanning for btrfs filesystems" that happens at boot and keeping fstab pointing to the UUID for the "complete" RAID array:
```
UUID=3d12bc7b-61b1-4dea-b78b-ef9a44a6b698 /media/btr0 btrfs defaults 0 0
```  The earlier "scanning" seems to have found the two disks comprising my RAID1 array and figured out how to mount them as btrfs RAID1 without any help from me.

However my btrfs RAID is made up of partitions (sdf1 and sdg1), not volumes.  In fact I didn't know using volumes was an option.  Is there anywhere that explains the advantages/disadvantages of partitions vs whole drives?  Is it possible that "Scanning for btrfs filesystems" only detects btrfs if it's in partitions and not volumes?

OP mentioned that this:> UUID=2e905f8f-e525-4114-afa6-cce48f77b629 /mnt/data btrfs device=PARTUUID=335feff3-dffc-40e4-8543-f1be7f6def72,device=PARTUUID=b78482e6-6054-4867-9d68-7841cac91eba,device=PARTUUID=e919a62f-5f5d-4b67-acad-1d68bce88355,device=PARTUUID=33fef351-9d4d-4952-a759-d01aba34148b 0 0didn't work because he's using whole disks and not partitions. Maybe it might work if you subsitituted "UUID" for "PARTUUID"?  

I've googled the heck out of this and still feel like I'm flying blind...

---

