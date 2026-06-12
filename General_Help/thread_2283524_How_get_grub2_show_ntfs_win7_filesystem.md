---
title: "How get grub2 show ntfs win7 filesystem?"
date: 2015-06-22
forum: General Help
---

### Post by einstein**-7 on 2015-06-22
Just recently cloned linux to a SSD and I can't seem to get the grub2 menu to show an option for my Win7 system which is installed on another drive.

Linux system is on sda and win7 is on sdb but all the suggestions out there about not being able to mound the ntfs drive and such because of labels etc. don't seems to be my particular problem .. I tried update-grub before and after mounting the ntfs partition and it doesn't show up.

This is what I get from "sudo fdisk -l"

crush@crush7:~$ sudo fdisk -l

```
Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e62cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   452478975   226238464   83  Linux
/dev/sda2       452478976   468860927     8190976   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x966bf9e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.
```

This is "sudo bklid"

```
crush@crush7:~$ sudo blkid
/dev/sda1: LABEL="Ubuntu 14.04SSD" UUID="2ad97668-c95c-439e-8b75-548845224788" TYPE="ext4" 
/dev/sda2: UUID="51d12ea7-f23d-4051-85e2-bca439a3afeb" TYPE="swap" 
/dev/sdb2: UUID="4C69-7DFA" TYPE="vfat" 
/dev/sdb3: LABEL="Win7" UUID="B46C159BE5F8BC93" TYPE="ntfs" 
/dev/sdc1: LABEL="Storage" UUID="5428F6C928F6A95E" TYPE="ntfs" 
/dev/sdd1: LABEL="Ubuntu 14.04 HDD" UUID="dfb51564-4d54-4cdc-82d6-f36f2d4885ae" TYPE="ext4" 
/dev/sdd5: UUID="68ed1a46-a567-42b3-b829-3bb67f464a3a" TYPE="swap" 
/dev/sde1: UUID="f63494fb-8d30-44e6-85d4-b5511b442d43" TYPE="swap" 
/dev/sde5: LABEL="Ubuntu 14.04 USB" UUID="7b30781b-1afb-4a66-b7a8-bf252b3d243d" TYPE="ext4" 


```

This is what I get after mounting the win7 drive and running "sudo os-prober" sdd is a linux HDD and sde is a USB..

```
crush@crush7:~$ sudo os-prober
/dev/sdd1:Ubuntu 14.04.2 LTS (14.04):Ubuntu:linux
/dev/sde5:Ubuntu 14.04.2 LTS (14.04):Ubuntu1:linux
```


```
crush@crush7:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdd1
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sde5
done
```

Any ideas ? I would really like this drive to be the boot drive and simply choose my system from there..

---

### Post by jamesisin on 2015-06-22
Was the Win7 partition present when you built the SSD?  In short did Grub ever know about Win7?

---

### Post by asusv2 on 2015-06-22
did you add windows to the grub menu

If not add to "/etc/grub.d/40_custom"
```
menuentry "Windows" {
    set root=(hd1,2)
    chainloader +1
}

```
(hd0,0 stands for the location of the windows os, first number is disk , second number partition)

then ```
sudo update-grub
```

---

### Post by oldfred on 2015-06-22
If sdb is a gpt partitioned drive, then Windows has to be installed in UEFI mode. Or was drive originally gpt and you installed Windows in BIOS with MBR, but Windows then does not correctly convert to MBR.

UEFI with gpt and BIOS with MBR are not compatible from a boot stand point. You can only switch from booting in one mode to the other from UEFI boot menu. Or you cannot use grub to boot sytem installed in a different boot mode. 

If drive not really gpt, then you need to remove the incorrect backup gpt partition table. If drive really is gpt, then you need to install Ubuntu in UEFI boot mode.

Post this as fdisk does not work on gpt partitioned drives.
sudo parted -l

---

### Post by einstein**-7 on 2015-06-23
> **jamesisin said:**
> Was the Win7 partition present when you built the SSD?  In short did Grub ever know about Win7?

Yes grub was installed with the windows drive plugged in but not sure if it was mounted in the usb system I was installing grub from.  

Didn't know about adding the windows entry I'm trying that now.
 
Here is the result of "sudo parted -l"

```
Model: ATA SanDisk SDSSDHII (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  232GB  232GB   primary  ext4            boot
 2      232GB   240GB  8388MB  primary  linux-swap(v1)


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  134MB  134MB                     msftres
 2      135MB   240MB  105MB  fat32              boot
 3      240MB   500GB  500GB  ntfs               msftdata
```

---

### Post by oldfred on 2015-06-23
You will not be able to boot Windows from grub. Ubuntu is installed in BIOS mode and Windows in UEFI boot mode. The modes are not compatible and you have to only boot from UEFI boot tab menu or perhaps a one time boot key like f10 or f12.

Or reinstall Ubuntu in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by VMC on 2015-06-23
Output "grub.cfg" here so we can have a look.

---

### Post by Geoffrey_Arndt on 2015-06-23
One option is a a full reinstall (not clone) on sda for linux  . . . this time installing Linux via UEFI mode versus ms-dos/mbr mode.   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jamesisin on 2015-06-23
Yeah, you can't mix UEFI and BIOS in the same bootloader.  You are stuck reinstalling something (either Win in BIOS or Ubu in UEFI).  On the bright side you should be able to clone your ~/ partition once you have done so.

---

### Post by einstein**-7 on 2015-06-23
> **oldfred said:**
> You will not be able to boot Windows from grub. Ubuntu is installed in BIOS mode and Windows in UEFI boot mode. The modes are not compatible and you have to only boot from UEFI boot tab menu or perhaps a one time boot key like f10 or f12.

Or reinstall Ubuntu in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

OK, found this about installing grub in EFI mode since I don't want a fresh install anyway... 

> First, you don't set the mount point in GParted; that's done manually (and temporarily) via the mount command or permanently by editing /etc/fstab. Thus, your concern over this issue is misplaced.

  Second, an EFI System Partition (ESP) is simply a FAT partition with a  particular type code (namely, C12A7328-F81F-11D2-BA4B-00A0C93EC93B on  GPT disks) set. Note that the mount point in /etc/fstab is not part of the ESP's definition; it's just conventional (but not required) in Linux to access the ESP by mounting it at /etc/fstab. How you set the type code varies from one program to another:
  
[LIST]
[*]In gdisk, you set the type code to EF00. (gdisk  uses two-byte type codes that expand out to the real type codes on the  disk; "EF00" is just a mnemonic for  "C12A7328-F81F-11D2-BA4B-00A0C93EC93B".)
[*]In GParted or parted, you set the "boot flag." Note, however, that this works *only*  on GPT disks; you cannot set the ESP type code on MBR disks with these  programs. (This isn't normally a big deal, since EFI-based computers  usually boot from GPT disks.)
[/LIST]


This says you can't create an EFI partition on an MBR disk with the right type of flag which is what I just tried to do followed by a bootrepair grub reinstall onto that partion in UEFI mode which failed because flag is wrong so the partition is not visible to the bootrepair ---- anyone know how to create a EFI partition on a MBR formated drive? 

If no can I simply reformat the drive as GPT and then re-clone the system and then install grub in UEFI mode with the right EFI partion of course?

---

### Post by oldfred on 2015-06-23
You cannot clone from MBR to gpt, you can copy  all the data, if you can extract it.
MBR(msdos) and gpt have totally different structures.

I have seen users with MBR drives and Boot-Repair converted install to UEFI using the efi partition on another drive that was gpt. That is not recommended, better to have all drives gpt partitioned once you start to use UEFI.

---

### Post by einstein**-7 on 2015-06-24
> **oldfred said:**
> You cannot clone from MBR to gpt, you can copy  all the data, if you can extract it.
MBR(msdos) and gpt have totally different structures.

I have seen users with MBR drives and Boot-Repair converted install to UEFI using the efi partition on another drive that was gpt. That is not recommended, better to have all drives gpt partitioned once you start to use UEFI.
OK, so just wiped and repartitioned as gpt and created a 100mb fat32 with bootable flag and EFI label and then tried to install grub to it from a boot-repair usb booted in UEFI mode and it still refuses to show the partition only the one on the win7 drive?? Oddly though from a non UEFI boot, boot-repair shows the partition in the list of available efi's to install efi grub on but then fails because the running sys is not efi... 
Any ideas to get the partition to show up in the efi system?

---

### Post by oldfred on 2015-06-24
I have two drives with Ubuntu in UEFI mode on both. I was not able to get my install on sdb to use the efi partition on sdb, it only installs to sda.
I just copied the /EFI/ubuntu folder to sdb's efi partition which I had made in advance. And copied grub & shim into a /EFI/Boot folder and renamed grub to bootx64.efi.

The only way I got it to install to the efi on sdb, was to disconnect sda, so the hard drive was the only drive.

---

### Post by einstein**-7 on 2015-06-25
> **oldfred said:**
> I have two drives with Ubuntu in UEFI mode on both. I was not able to get my install on sdb to use the efi partition on sdb, it only installs to sda.
I just copied the /EFI/ubuntu folder to sdb's efi partition which I had made in advance. And copied grub & shim into a /EFI/Boot folder and renamed grub to bootx64.efi.

The only way I got it to install to the efi on sdb, was to disconnect sda, so the hard drive was the only drive.

Ok so in your case you just created an EFI folder on your "efi" partition if I am correct? then copied your existing grub from there..

I'm on a working UEFI system now finally and my "efi" folder is in /boot/efi/efi and then efi info sys folders in there. Not sure why its not simply /boot/efi?
Anyway I was trying to follow this [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi) and simply chroot into the new system from the efi boot-repair usb and then install grub manually that way.  Firstly I had to add the efi partition to the usb fstab because it would not mount it then I mounted the filesystem sda3 on /mnt and efi partition on /mnt/boot/efi and had to create the "efi" folder under /boot since it was not there.  
Short of it was it installed but didn't operate because I hadn't updated the fstab on the clone yet not realizing that when I chrooted into the clone It was mounting the original drive I cloned from which had no Efi partition lol. 
After sorting out the fstab files and booting back to the boot-repair usb I found mount points in mnt/boot-sav/sda2/efi and the boot-repair utility then found the sda2 and I installed uefi grub from there!
Not sure exactly how the mount points got there?  either from adding the sda2 to the fstab or simply having the sda2/efi and sda3/boot/efi folders present?

Last question is I installed grub in secure boot mode because I couldn't find any way to disable it in the BIOS without deleting the keys and win7 is set to secure boot with those keys..  If I install grub without secure boot and the win7 drive unplugged and secure-boot off in BIOS which I assume would work --  would the resulting grub be able to then boot win7 later if it was still in secure mode?

---

### Post by oldfred on 2015-06-25
Windows 7 does not have secure boot as far as I know, only Windows 8 or later. But Windows 7 and even some versions of Vista can boot in UEFI mode.

How you boot installer, UEFI or BIOS is how it installs. And with Ubuntu if secure boot is on, then it installs the signed versions of grub (actually then shim) and kernels. You can turn off secure boot and still use signed versions to boot in standard UEFI mode.

The working efi partition is mounted by fstab to /boot/efi. And the partition has folders inside it as EFI/ubuntu. So working install's efi will be seen as /boot/efi/EFI/ubuntu.
Other efi partitions then would just be mounted somewhere /media/$USER, /mnt/EFI/ubuntu or where ever you mount it. But internally it is just these paths and then the files inside those folders:
       /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu
/EFI/refind/refind_x64.efi

All the boot-sav folders are from Boot-Repair and its backup of things.

Microsoft has up until Windows 10 required vendors to configure systems that user can turn off UEFI secure boot. Not sure about new systems with pre-installed Windows 10 as Microsoft is saying now that it will be up to the vendor.
A few systems have 32 bit UEFI with 64 bit systems and those typically are more locked down and do not even have the CSM chip for BIOS boot. When there is no CSM mode, those are class 3 UEFI. I would expect once BIOS is not used much vendors will make all systems class 3.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

