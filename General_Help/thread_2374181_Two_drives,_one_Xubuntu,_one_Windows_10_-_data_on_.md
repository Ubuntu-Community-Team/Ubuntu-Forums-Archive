---
title: "Two drives, one Xubuntu, one Windows 10 - data on second drive not mounted"
date: 2017-10-13
forum: General Help
---

### Post by makem2 on 2017-10-13
I had a working dual booted xubuntu and windows 10 but it became corrupted for some reason (probably my fault) and I lost the desktop and other facilities.

I have an SSD drive on which xubuntu is installed. The other drive (formatted NTFS) has windows 10 (Win10) together with two data partitions (WinData & Data).

I re-installed a fresh xubuntuon the SSD drive and the dual booting operates fine. The only problem is that the data partitions (WinData & Data) are grayed out in file manager after rebooting. The windows operating system named Win10 is also visible, not mounted but its contents show after clicking on it.

I can click on each of the three grayed out folder names and they mount, showing the contained data.

```

makem@SSDtosh:~$ sudo blkid
/dev/sda1: UUID="CCBC-12A0" TYPE="vfat" PARTUUID="0ca21933-62a8-4dbd-aa0e-d484ee6d028c"
/dev/sda2: UUID="eebedcff-70df-43ec-a319-03e468d92c35" TYPE="ext4" PARTUUID="69d7a9ce-68dc-4ccd-aeb8-fed18280e943"
/dev/sda3: UUID="d78428d2-66ad-474b-a7bc-8144945dd6a1" TYPE="ext4" PARTUUID="1f4ce6eb-f591-4bfc-9418-a11129872523"
/dev/sda4: UUID="68342eb5-6386-48f4-a2ef-e1683ff58be5" TYPE="swap" PARTUUID="909ad8de-771f-4fc3-9e5e-f8326810066d"
/dev/sda5: LABEL="Data" UUID="b15b5fdc-a6ee-4fd9-add9-1039d86dfee2" TYPE="ext4" PARTUUID="bbb3e9e7-0f4f-49e9-b56e-967c2b21798f"
/dev/sdb1: LABEL="WinRE" UUID="D8AC6421AC63F880" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="294fe5c5-7b1f-48fc-b9dd-c92842250842"
/dev/sdb2: LABEL="ESP" UUID="0A66-6E5B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="e5a1951b-f090-441d-92ce-dbe518417005"
/dev/sdb3: UUID="11A8-6C10" TYPE="vfat" PARTLABEL="Microsoft reserved partition" PARTUUID="35435f1b-40ab-4a92-a704-01f2aa69d2f4"
/dev/sdb4: LABEL="Win10" UUID="BC9A68789A683156" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1db6050f-d9c9-424a-b92f-0b4a61ccee46"
/dev/sdb5: UUID="9486D2F086D2D23A" TYPE="ntfs" PARTUUID="55c8e54b-7593-4dd8-817d-cb6764bce5a0"
/dev/sdb6: LABEL="WinData" UUID="D232DC8B32DC75C7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1d91cc7e-4481-4169-9117-c5b947315241"
/dev/sdb7: UUID="387E1FA37E1F5948" TYPE="ntfs" PARTUUID="699c6fd9-8fe5-43fa-925b-f1c20edc794d"
/dev/sdb8: LABEL="Recovery" UUID="8E5C69F15C69D50D" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9fefe4de-9237-44f0-85a2-829a76543f36"
makem@SSDtosh:~$

```

```


fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=eebedcff-70df-43ec-a319-03e468d92c35 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0       0


```

Can anyone tell me how to have these folders mounted at boot as I don't want to mess up this install.

---

### Post by Dennis N on 2017-10-13
Mounting a partition automatically at boot time is done by an line entry in /etc/fstab for each partition to be mounted. You don't appear to have such entries in your fstab for the two data partitions, so you need to create them manually by editing the fstab file. 

Information:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by makem2 on 2017-10-13
Thank you, I had realised that from previous installations and have done it :-)

---

### Post by oldfred on 2017-10-13
You show one ESP - efi system partition on sdb?

Ubuntu normally has to have ESP on sda to install grub, did you install Ubuntu in BIOS/MBR mode, not UEFI/gpt mode?
Usually better to have all systems UEFI and all drives gpt partitioned if you have UEFI hardware and particularly if Windows is UEFI install. But not required as you can directly boot into BIOS mode from UEFI boot menu.

---

