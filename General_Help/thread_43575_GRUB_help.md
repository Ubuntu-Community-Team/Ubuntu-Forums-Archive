---
title: "GRUB help"
date: 2005-06-22
forum: General Help
---

### Post by iamhiddensomewhere on 2005-06-22
After re-installing WinXPro, previously having Ubuntu and WinXPro living together happily within GRUB, now I cannot boot into Ubuntu.

I installed BootMagic, because GRUB was no longer loading at bootup, and hoped that I could boot into Ubuntu, but could not. I was greeted with the letter L and a cryptic series of 9s.

This is all I've done, and I don't quite know what to do that would fix this.

Any help is greatly appreciated.

---

### Post by Martin Witte on 2005-06-22
You have to reinstall grub. The way I do this is to boot with [http://www.sysresccd.org/](http://www.sysresccd.org/), but I think the Ubuntu live cd will do as well. Then you have to find your partition information, I use parted for this. For me this gives:
martin@ubuntu:~ $ sudo parted
Password:
GNU Parted 1.6.20 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hda
(parted) print
Disk geometry for /dev/hda: 0.000-152627.835 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  28615.781  primary   ntfs        boot
2      28615.781 152625.344  extended              lba
5      28615.812  57231.562  logical   ext3
6      57231.593  85847.343  logical   ext3        boot
7      85847.375 114463.125  logical   ext3
8     114463.156 152625.344  logical   fat32       lba
(parted)

On my system Windows is on partition 1, Ubuntu on partition 5. The remainder of this assumes it is the same for you - else you have to change the partiotn number, and eventually disk number

You now have to make a mountpoint for the Ubuntu partition, e.g. mkdir /dev/ubuntu, mount /dev/hda5 /dev/ubuntu. 

Now you can install grub, with your last configuration with: grub --config-file=/dev/ubuntu/boot/grub/menu.lst, you will get a grub prompt. here you type root (hd0,4) and then setup (hd0). Now grub is installed. The thing to notice iis that grub uses one less then the devicenumebr to identify the proper partition.

Hope this helps

---

