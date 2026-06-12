---
title: "booting error--boots only into memtest86"
date: 2015-07-30
forum: General Help
---

### Post by Elliot_Findley on 2015-07-30
I've been flailing around for sometime now trying to fix this issue. I updated my kernel the other day, but /boot was full, so I deleted some kernel files I thought were obselete. Apparently they weren't, because I can no longer boot into my OS. I'm typing this from a Live USB. 

Things I've already tried, without success: 
1. The recommendation at[COLOR=#000000][FONT=Courier New] [http://ubuntuforums.org/showthread.php?t=1679879](http://ubuntuforums.org/showthread.php?t=1679879)[/FONT][/COLOR]
2. I can apparently mount the drive (althought it is encrypted and is using an 'unknown file system LVM2_member'). I first do ```
[COLOR=#000000][FONT=Courier New]sudo cryptsetup -v luksOpen /dev/sda5 mydrive[/FONT][/COLOR]


```
and then mount it using this link: [http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html](http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html). I then tried ```
apt-get install --reinstall kernel-image
``` but it still boots to memtest every time. 

That said, I can't be too confident that I did any of things correctly since I'm fairly new to Ubuntu and, frankly, all of this seems over my head. I really need someone to take my hand and walk me through the fix if there's someone out there so inclined. 

Please help!!

---

### Post by oldfred on 2015-07-30
Have you tried Boot-Repair's full grub uninstall/reinstall? I believe that also installs newest kernel. If not while in the chroot to reinstall grub you can also install the newest kernel.

---

### Post by Elliot_Findley on 2015-07-31
Thanks for the suggestion. I successfully installed boot-repair, but when I tried to run it, it explodes: the screen fills with messages like the following, which was the last message displayed. 

```
 (glade2script:5579): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

/usr/share/boot-sav/gui-g2slaunch.sh: line 29:  5579 Segmentation fault      (core dumped) $G2S $1 -g ./$PACK_NAME.glade -s ./$APPNAME.sh --combobox="@@_combobox_format_partition@@col" --combobox="@@_combobox_bootflag@@col" --combobox="@@_combobox_ostoboot_bydefault@@col" --combobox="@@_combobox_purge_grub@@col" --combobox="@@_combobox_separateboot@@col" --combobox="@@_combobox_efi@@col" --combobox="@@_combobox_sepusr@@col" --combobox="@@_combobox_place_grub@@col" --combobox="@@_combobox_add_kernel_option@@col" --combobox="@@_combobox_restore_mbrof@@col" --combobox="@@_combobox_partition_booted_bymbr@@col"
```

You might want to know I followed the recommendation at [http://ubuntuforums.org/showthread.php?t=1679879](http://ubuntuforums.org/showthread.php?t=1679879)
to mount the appropriate directories. I hope I haven't made an irreparable mistake!! 

UPDATE: 
After some further forum-scouring I deduced that the problem above is attributable to my inability to open a display from within chroot. So I tried 
```
 export DISPLAY=:0.0
```
and when I reran 
```
sudo boot-repair
```
a window popped up inviting me to 'Create a BootInfo summary'. When I clicked this button, nothing happens, unfortunately.

---

### Post by oldfred on 2015-07-31
The summary report needs Internet to post to pastebin. Did you also configure Internet.
Often with chroot you need this:

 sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting

---

### Post by Elliot_Findley on 2015-08-01
I don't think internet connection is the problem. For instance, I can apt-get update without a problem. But anyway I did what you suggest, but with the same problem.

---

### Post by Elliot_Findley on 2015-08-01
I may have found another problem upstream. I mounted my drive by ```

[COLOR=#000000][FONT=Courier New]ubuntu@ubuntu:~$ sudo lvscan[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]  ACTIVE        [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]'/dev/ubuntu-gnome-vg/root' [115.11 GiB] inherit[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]  ACTIVE        [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]'/dev/ubuntu-gnome-vg/swap_1' [3.89 GiB] inherit[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New][COLOR=#000000][FONT=Courier New]ubuntu@ubuntu:~$ [/FONT][/COLOR]sudo mount /dev/ubuntu-gnome-vg/root /mnt/temp[/FONT][/COLOR]


```

and then accessed my /home directory through /mnt/temp. fdisk seems to indicate an error with this mounting: 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db81f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758   250068991   124783617    5  Extended
/dev/sda5   *      501760   250068991   124783616   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06d1cfa0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      206847      102400   ef  EFI (FAT-12/16/32)
/dev/sdb2   *      206848  1953520064   976656608+   c  W95 FAT32 (LBA)

Disk /dev/mapper/mydrive: 127.8 GB, 127776325632 bytes
255 heads, 63 sectors/track, 15534 cylinders, total 249563136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/mydrive doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-root: 123.6 GB, 123597750272 bytes
255 heads, 63 sectors/track, 15026 cylinders, total 241401856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-swap_1: 4177 MB, 4177526784 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8159232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-swap_1 doesn't contain a valid partition table

```

I'm bothered by 
```
Disk /dev/mapper/mydrive doesn't contain a valid partition table 
```

Is this a problem?

---

### Post by oldfred on 2015-08-01
I do not know LVM, but do not think fdisk is correct for LVM logical partitions. It only works with the MBR(msdos) physical partitions. Fdisk also does not work with gpt partitioned drives.

---

### Post by Elliot_Findley on 2015-08-02
Okay. I believe you. Now what should I do? I'm still stuck, and I'm hoping you can help me, oldfred.

---

### Post by oldfred on 2015-08-02
Can you get Boot-Repair to run & in its advance mode choose the full grub uninstall/reinstall & update newest kernel. Review tabs in advanced mode for things to tick. I have only reviewed those, never had to actually use them myself.

---

### Post by Elliot_Findley on 2015-08-07
oldfred, I finally got boot-repair to 'Create a BootInfo summary', and it output [http://paste2.org/yzDsMbHh](http://paste2.org/yzDsMbHh)

I tried the 'Recommended repair', but I got a window saying 'you may want to retry after decrypting your partitions'. This confused me; I thought I had already decrypted my partitions above in 

```
[COLOR=#000000][FONT=Courier New]sudo cryptsetup -v luksOpen /dev/sda5 mydrive[/FONT][/COLOR]

```So, I aborted boot-repair. What's next?

---

### Post by oldfred on 2015-08-07
I do not know LVM & encryption.
But thought when you mounted or Boot-Repair asked you to mount encrypted partition it then asked for the pass phrase and was mounted.

It looks like script included all the normal files in /boot which is not encrypted, but not any files like fstab in install inside encrypted partitions.

Try to boot Boot-Repair in BIOS mode, and when mounting encrypted partition give pass phrase to LVM is mounted also. Then you should be able to run repairs.

Separately.
Did you use a 1TB drive as installer? Normally you use a small flash drive.
You do not really want FAT32 partitions that are large & yours is the entire 1TB drive, except for ESP - efi system partition. FAT32 is ok for small devices or small partitions, but not for large partitions as it does not have journal and can be difficult to then repair.

You have UEFI hardware and booted Boot-Repair in UEFI mode. But your install in sda is CSM/BIOS/Legacy or what every your UEFI calls it. Better to always stay in same boot mode, or always BIOS or always UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by Elliot_Findley on 2015-08-08
Fred, how in the world do I "[COLOR=#000000]Try to boot Boot-Repair in BIOS mode"??? I really don't understand what you mean.  google-searching for 'boot-repair in BIOS mode' yields nothing apparently relevant. 

Please note that the live USB I am using does NOT have the same version of Ubuntu installed on it as the original installation. 


[/COLOR]

---

### Post by oldfred on 2015-08-08
Boot-Repair is either its own live install or can be installed into most Ubuntu flavors and maybe other Linux versions.
So can you boot anything?
If so install Boot-Repair and run the report?

Generally you should always have a working current version live installer or repair flash drive for every system you have installed.

---

### Post by Elliot_Findley on 2015-08-08
I can boot from my Live USB only. I did and ran boot-repair with the output at [COLOR=#1155CC][FONT=Courier New]_[http://paste.ubuntu.com/12032635]("http://paste.ubuntu.com/12032635/")_[/FONT][/COLOR] but the results may not be very different from when I ran boot-repair from within the /dev/sda5 partition above. [COLOR=#1155CC][FONT=Courier New][/FONT][/COLOR]Incidentally, I found someone with a similar problem here: [http://ubuntuforums.org/showthread.php?t=1319202](http://ubuntuforums.org/showthread.php?t=1319202), but as usual I can't implement their fix. 

For what it's worth, I have a theory: since /dev/sda5 is encrypted, the booting must happen from /dev/sda1. Mounting this drive, 
```

$ sudo mount /dev/sda1 /mnt
$ ls
grub lost+found memtest86+.bin memtest86+.elf memtest86+_multiboot.bin

```

Isn't this directory supposed to have a vmlinux or reference some linux kernel? 

My problems all started when I tried to update the kernel. Might I have deleted some files form this drive???

---

### Post by oldfred on 2015-08-08
It looks like you deleted all the kernels.
Yes, with LVM the /boot folder is in a separate un-encrypted partition. The rest of your install is inside the encryption.

I think one of the options in Boot-Repair is a full uninstall/reinstall of grub and you can tick installing the latest kernel.

---

### Post by Elliot_Findley on 2015-08-09
Okay. I have successfully mounted sda1 and /dev/ubuntu-gnome-vg/root (which is part of sda5 once this is decrypted). I'm running boot-repair with "Purge GRUB before reinstalling it" and "purge kernels then reinstall last kenel". Please note I also set "Place GRUB into:"='sda'. (options were mapper/no; sda; sdb). 

Hard to tell if things are working correctly. Boot-repair has been running for the last hour or more, with the same window displayed: "Purge kernels then reinstall last kernel mapper/ubuntu-gnome-vg-root (ins). This may require several mintues...

I'd say so! I'm doing this at starbucks, so I'm afraid I'm going to have to cut it short prematurely. Should I be worried? I expected it to be done by now.

Please note that it suggested that I unencrypt my other partitions, which I thought I had already done, so  I dismissed this and proceeded.

---

### Post by oldfred on 2015-08-09
What other partitions?
Most LVM have / & swap.
If you have other system folders as partitions, they may have to be mounted for it to work.
If just data partitions, it should not matter.
Network is working?

Once grub is uninstalled, until you get the new grub & kernel installed system will not work.
Then Boot-Repair or a full chroot from live installer is the only way to repair it.

---

