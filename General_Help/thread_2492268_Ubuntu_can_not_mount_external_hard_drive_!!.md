---
title: "Ubuntu can not mount external hard drive !!"
date: 2023-11-05
forum: General Help
---

### Post by fairbird on 2023-11-05
[COLOR=#000000][FONT=Verdana]I have 1T external hard disk with (exfat) extension and I using ubuntu 23.10 ..[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The hard disk was worked just fine before I try to open it on windows 11.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]But Windows could not find it, so I changed lbale through the softmanage without formation.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]But also Windows can not open it and ubuntu can not mount it !!
[/FONT][/COLOR]```
[COLOR=#000000]raed@fairbird:~$ sudo mount /dev/sdc1 /mnt[/COLOR]
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error. [COLOR=#000000]       dmesg(1) may have more information after failed mount system call.[/COLOR]
```

[COLOR=#000000][FONT=Verdana]I do not want to format the hard disk so as not to lose the data on it ..[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]This out put (lsblk)
```
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]raed@fairbird:~$  lsblk[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0 135.6M  1 loop /snap/ark/46
loop1    7:1    0 105.8M  1 loop /snap/core/16091
loop2    7:2    0     4K  1 loop /snap/bare/5
loop3    7:3    0 249.1M  1 loop /snap/audacity/1051
loop4    7:4    0 135.6M  1 loop /snap/ark/44
loop5    7:5    0 105.8M  1 loop /snap/core/16202
loop6    7:6    0  55.7M  1 loop /snap/core18/2790
loop7    7:7    0  63.5M  1 loop /snap/core20/2015
loop8    7:8    0  55.7M  1 loop /snap/core18/2796
loop9    7:9    0    73M  1 loop /snap/core22/607
loop10   7:10   0 240.3M  1 loop /snap/firefox/3289
loop11   7:11   0  73.9M  1 loop /snap/core22/864
loop12   7:12   0 240.3M  1 loop /snap/firefox/3290
loop13   7:13   0  11.2M  1 loop /snap/firmware-updater/109
loop14   7:14   0 521.4M  1 loop /snap/gimp/393
loop15   7:15   0 520.9M  1 loop /snap/gimp/405
loop16   7:16   0 164.8M  1 loop /snap/gnome-3-28-1804/198
loop17   7:17   0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop18   7:18   0 496.9M  1 loop /snap/gnome-42-2204/132
loop19   7:19   0   497M  1 loop /snap/gnome-42-2204/141
loop20   7:20   0  91.7M  1 loop /snap/gtk-common-themes/1535
loop21   7:21   0 116.5M  1 loop /snap/jdownloader2/17
loop22   7:22   0   140K  1 loop /snap/gtk2-common-themes/13
loop23   7:23   0 450.2M  1 loop /snap/kf5-5-108-qt-5-15-10-core22/5
loop24   7:24   0 438.3M  1 loop /snap/kf5-5-110-qt-5-15-11-core22/3
loop25   7:25   0   266M  1 loop /snap/kompare/87
loop26   7:26   0 268.4M  1 loop /snap/kompare/93
loop27   7:27   0 101.5M  1 loop /snap/p7zip-desktop/220
loop28   7:28   0   618M  1 loop /snap/pycharm-community/352
loop29   7:29   0 617.9M  1 loop /snap/pycharm-community/350
loop30   7:30   0 175.9M  1 loop /snap/skype/306
loop31   7:31   0   176M  1 loop /snap/skype/309
loop32   7:32   0  10.5M  1 loop /snap/snap-store/1046
loop33   7:33   0  12.3M  1 loop /snap/snap-store/959
loop34   7:34   0  40.8M  1 loop /snap/snapd/20092
loop35   7:35   0  40.9M  1 loop /snap/snapd/20290
loop36   7:36   0   452K  1 loop /snap/snapd-desktop-integration/83
loop37   7:37   0 320.4M  1 loop /snap/vlc/3078
loop38   7:38   0 321.1M  1 loop /snap/vlc/3721
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   487M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 651.9G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                /
&#9500;&#9472;sda3   8:3    0   9.3G  0 part 
&#9500;&#9472;sda4   8:4    0  92.6G  0 part 
&#9500;&#9472;sda5   8:5    0   517M  0 part 
&#9492;&#9472;sda6   8:6    0 176.7G  0 part 
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part 
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part 
sr0     11:0    1  1024M  0 rom

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
```[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This out put (parted -l)
```
[/FONT][/COLOR][COLOR=#000000]Model: ATA WDC WD10EZEX-00W (scsi)[/COLOR]
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   fat32                 boot, esp
 2      512MB   701GB   700GB   ext4
 3      701GB   711GB   10.0GB  linux-swap(v1)        swap
 4      711GB   810GB   99.5GB  ntfs                  msftdata
 5      810GB   811GB   542MB   ntfs                  hidden, diag
 6      811GB   1000GB  190GB   ntfs                  msftdata


Model: ATA TOSHIBA MQ04ABF1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary


Model: WD Elements 2621 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags [COLOR=#000000] 1      1049kB  1000GB  1000GB  primary[/COLOR][COLOR=#000000][FONT=Verdana]
```

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]This out put (blkid)
```
[/FONT][/COLOR][COLOR=#000000]/dev/sda2: UUID="d63725f4-87aa-4561-b1f6-b3bb28231ec4" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="eea62fa3-e27e-474f-bac2-69cc32b0b8b5"[/COLOR]
/dev/loop1: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop29: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop19: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop37: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop27: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop17: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop8: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop35: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop25: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/sdb1: LABEL="PS4_Games_4" UUID="71AA-8B5B" BLOCK_SIZE="512" TYPE="exfat" PARTUUID="a1ea8996-01"
/dev/loop15: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop6: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop33: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop23: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop13: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop4: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop31: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop21: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop11: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop2: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop38: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop0: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop28: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop18: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop9: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop36: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop26: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/sdc1: PARTUUID="42551609-01"
/dev/loop16: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop7: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop34: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop24: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/sda4: BLOCK_SIZE="512" UUID="28FA50D8FA50A3BA" TYPE="ntfs" PARTUUID="a51399f2-8599-4f94-88d5-0dfd28fa65d8"
/dev/sda5: BLOCK_SIZE="512" UUID="28E8A75FE8A72A50" TYPE="ntfs" PARTUUID="34ecda01-684d-430f-96ec-a06b160e28eb"
/dev/sda3: UUID="a3afd51c-c885-4487-a26b-905da75b51b8" TYPE="swap" PARTUUID="c39caf04-c427-4361-8c6d-77022da4325c"
/dev/sda1: UUID="DF00-0E4E" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="504b764f-20cf-4183-aa15-a1ce55be1e59"
/dev/sda6: BLOCK_SIZE="512" UUID="922CD0C32CD0A38F" TYPE="ntfs" PARTUUID="ecdbb8bf-5de3-45e6-ac9b-34ce54a1704b"
/dev/loop14: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop5: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop32: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop22: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop12: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop3: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop30: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop20: BLOCK_SIZE="131072" TYPE="squashfs" [COLOR=#000000]/dev/loop10: BLOCK_SIZE="131072" TYPE="squashfs"[/COLOR][COLOR=#000000][FONT=Verdana]
```

```
[/FONT][/COLOR][COLOR=#000000]raed@fairbird:~$ sudo apt install exfat-fuse[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
exfat-fuse is already the newest version (1.4.0-2).
The following package was automatically installed and is no longer required:
  linux-tools-common
Use 'sudo apt autoremove' to remove it. [COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR][COLOR=#000000][FONT=Verdana]
```

```
[/FONT][/COLOR][COLOR=#000000]raed@fairbird:~$ sudo mount -t exfat /dev/sdc1 /mnt[/COLOR]
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error. [COLOR=#000000]       dmesg(1) may have more information after failed mount system call.[/COLOR][COLOR=#000000][FONT=Verdana]
```

> [/FONT][/COLOR][COLOR=#000000]raed@fairbird:~$ sudo mount -t vfat /dev/sdc1 /mnt[/COLOR]
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error. [COLOR=#000000]       dmesg(1) may have more information after failed mount system call.[/COLOR][COLOR=#000000][FONT=Verdana]

The hard disk extension changed to fat16 ... I do not know how ?!!
[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293009&stc=1[/IMG][COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-11-05
Please post the output of this, posted within CODE Tags:
```

apt list exfat* --installed
lsmod | grep exfat
find /lib/modules -name exfat

```

---

### Post by fairbird on 2023-11-06
```
raed@fairbird:~$ apt list exfat* --installedListing... Done
exfat-fuse/mantic,now 1.4.0-2 amd64 [installed]
exfatprogs/mantic,now 1.2.1-2 amd64 [installed]
raed@fairbird:~$ lsmod | grep exfat
exfat                 102400  0
raed@fairbird:~$ find /lib/modules -name exfat
/lib/modules/6.5.0-10-generic/kernel/fs/exfat
/lib/modules/6.2.0-36-generic/kernel/fs/exfat
raed@fairbird:~$
```

---

### Post by MAFoElffen on 2023-11-06
And which is your current running kernel version?
```

uname -r

```

---

### Post by fairbird on 2023-11-06
```
6.5.0-10-generic
```

I have use testdisk and copy all data to another hard disk.
And I think better to format hard disk and return again the data to disk !!

---

