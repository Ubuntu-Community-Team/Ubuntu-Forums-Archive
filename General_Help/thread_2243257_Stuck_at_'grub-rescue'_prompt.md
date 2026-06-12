---
title: "Stuck at 'grub-rescue' prompt"
date: 2014-09-07
forum: General Help
---

### Post by 2CV67 on 2014-09-07
I had 14.04.1 dual-booting with W7 on my Asus Eeepc Netbook.

Due to messy problems with samba, I decided to re-install 14.04.1 in place of the old 14.04.1 from a Live USB stick, which has worked OK several times previously.

The installation went OK but I was a bit surprised at the location proposed for the boot-loader.
I expected to see "sda" but was presented with something like "sda1 Windows boot loader" & failed to react...
I accepted (obviously that was a big mistake) & everything went OK, including a grub screen showing Ubuntu & Windows.

After a bit of working on Ubuntu, I remembered to check that Windows was still OK & predictably struck disaster.

When I selected the Windows item on Grub screen, it just looped back to the same screen.

I have had no-boot issues on previous occasions, so just booted SuperGrub2 DisK, which showed it's usual screen with something like "Detect any operating system", which I selected.
Surprisingly, it only found 2 instances of Windows:
Windows Vista (hd1,msdos2)
Windows Vista (hd1,msdos1)

No Ubuntu was found.

Option 1 took me to a screen with flashing cursor & no way out except Ctr/Alt/Del, which takes me to the BIOS page, from where I can only do a hard shutdown.
Option 2 got to a screen saying:
```
error: no such partition.
Entering rescue mode...
grub rescue>_
```
Again, I can only get out of there by Ctr/Alt/Del.

Now, when I try to boot without the SuperGrub disk, I just get the BIOS page then that same grub rescue prompt.

After a lot of browsing, I did try ```
grub-install /dev/sda
``` but that resulted in ```
Unknown command 'grub-install'

```
I can boot the Live Ubuntu stick & that sees the contents of Windows OK but doesn't see Real Ubuntu...

Suggestions welcome!

Thanks!

---

### Post by 2CV67 on 2014-09-07
I can boot to GParted on a stick & that shows a big "Unallocated" where Ubuntu used to be...  :(

---

### Post by Bashing-om on 2014-09-07
2CV67; Yuk !

Does not bode well for the existence of ubuntu does it ?
We can look and see what the partitioning looks like:
From the liveDVD:
```

sudo fdisk -lu ##for MBR partitioning
sudo gdisk -l /dev/sda ##for GPT partitioning
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
ls -l /dev/sd*

```
and of course, a confirmation of what GParted sees (screen shot) would be nice as GParted will graphically show that unallocasted space.

If ubuntu does not exist, understandable that the boot code also does not exist.

[INDENT][INDENT]Won't hurt to look and prepare ourselves 
[INDENT][INDENT][INDENT]to (RE-)install once again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-07
Yuk indeed!!

I think this is everything you asked for.
If not - please ask again...

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29133921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   209717247   104857600    7  HPFS/NTFS/exFAT
/dev/sda2       209717248   241174527    15728640   1b  Hidden W95 FAT32
/dev/sda3       241176574   488355839   123589633    5  Extended
/dev/sda4       488355840   488397167       20664   ef  EFI (FAT-12/16/32)
/dev/sda5       484259840   488355839     2048000   82  Linux swap / Solaris

Disk /dev/sdb: 2008 MB, 2008023040 bytes
64 heads, 63 sectors/track, 972 cylinders, total 3921920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005369b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3919103     1959520+   b  W95 FAT32
ubuntu@ubuntu:~$
```

:::::::::::::::

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F1ECBB1F-F786-4AA3-842B-4D97912E5BF2
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 243087326 sectors (115.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       209717247   100.0 GiB   0700  Microsoft basic data
   2       209717248       241174527   15.0 GiB    0700  Microsoft basic data
   4       488355840       488397167   20.2 MiB    EF00  EFI System
   5       484259840       488355839   2.0 GiB     8200  Linux swap
ubuntu@ubuntu:~$ 
```

::::::::::::

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  107GB  107GB   primary   ntfs            boot
 2      107GB   123GB  16.1GB  primary   fat32           hidden
 3      123GB   250GB  127GB   extended
 5      248GB   250GB  2097MB  logical   linux-swap(v1)
 4      250GB   250GB  21.2MB  primary


Model: JetFlash Transcend 2GB (scsi)
Disk /dev/sdb: 2008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2007MB  2007MB  primary  fat32        boot


ubuntu@ubuntu:~$ 
```

:::::::::::::::

```
ubuntu@ubuntu:~$ sudo parted /dev/sda/ unit s print
Error: Could not stat device /dev/sda/ - Not a directory.                 
Retry/Cancel?   
```

:::::::::::::::::

```
ubuntu@ubuntu:~$ lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1              
&#9500;&#9472;sda2              
&#9500;&#9472;sda3              
&#9500;&#9472;sda4              
&#9492;&#9472;sda5              [SWAP]
sdb                 
&#9492;&#9472;sdb1              /cdrom
loop0               /rofs
ubuntu@ubuntu:~$ 
```

::::::::::::

```
ubuntu@ubuntu:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 Sep  7 20:09 /dev/sda
brw-rw---- 1 root disk 8,  1 Sep  7 20:02 /dev/sda1
brw-rw---- 1 root disk 8,  2 Sep  7 20:02 /dev/sda2
brw-rw---- 1 root disk 8,  3 Sep  7 20:02 /dev/sda3
brw-rw---- 1 root disk 8,  4 Sep  7 20:02 /dev/sda4
brw-rw---- 1 root disk 8,  5 Sep  7 20:02 /dev/sda5
brw-rw---- 1 root disk 8, 16 Sep  7 20:09 /dev/sdb
brw-rw---- 1 root disk 8, 17 Sep  7 20:02 /dev/sdb1
ubuntu@ubuntu:~$ 
```

::::::::::::::::

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/Screenshot_zps8c101291.png[/IMG]

---

### Post by 2CV67 on 2014-09-07
This is what it was before:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/e6e39477-98d1-4e0b-8ab9-99f0a6880748_zps8ae77822.jpg[/IMG]

---

### Post by Bashing-om on 2014-09-07
2CV67; Umphh !

I think we can safely say that ubuntu no longer exists. There is no hint of ubuntu operating system anywhere else than that of the the swap partition.

The only recourse I can see is to (RE-)install ubuntu.

[INDENT][INDENT]not good
[INDENT][INDENT][INDENT]just the way it is - looking for that silver lining -
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-07
Try to install Ubuntu in the unallocated partition with bootloader on sda?
And hope I still have W7?

Or reformat the whole thing & forget W7?

I am resigned to either, but am open to educated comments before I (again) dive in too deep!

Thanks for your help!

---

### Post by 2CV67 on 2014-09-07
> **Bashing-om said:**
> I think we can safely say that ubuntu no longer exists. There is no hint of ubuntu operating system anywhere else than that of the the swap partition.

Just for my education, is that all a result of putting the bootloader in the wrong place?
When Ubuntu has been running quite normally for several hours until I tried to boot W7?
EDIT - or is there something else lurking there???

---

### Post by Bashing-om on 2014-09-07
2CV67; Hey hey !
It's ubuntu, there is no diving in too deep, it is just a process of learning.

IF you are careful, in the (re-)install process your Windows partition will not be touched. Just take your time, and watch that nothing touches the partition (s) sda1, sda2.

Preferably you are connected to the internet with a 'wired' connection !

In the installer , choose the "something else" option. Click on that "unallocated space" and ->
I expect the install Wizard to accept to install onto that unallocated space - and will use the present swap partition. As to grub, yeah .. make sure it installs to the root of the hard drive 'sda' ; which it should by default. I also expect when grub installs that "os_30-prober" tool to pick up  Windows and chainload Windows onto the grub boot menu - automagically.

Be not to hasty to abandon that old friend Windows, there may yet be things to do that Ubuntu does not do in the manner you would prefer. Even though XP no longer has support, and is unsafe to be using on the 'net; takes time to wean off Windows and become comfortable with a different operating system.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-07
> **Bashing-om said:**
> In the installer , choose the "something else" option. Click on that "unallocated space" and ->
I expect the install Wizard to accept to install onto that unallocated space - and will use the present swap partition. As to grub, yeah .. make sure it installs to the root of the hard drive 'sda' ; which it should by default.

That's how I did it last time, except it didn't offer sda as default.
You can be sure I will never let that one through again!

I still need Windows for updating my TomTom GPS. (But I have W8.1 in the Desktop).
And it does scanning & printing better, but the difference is not worth bothering for most purposes.

OK - off we go again with the Live USB....

---

### Post by Bashing-om on 2014-09-07
2cv67: welp:

No idea as to what might have wiped out ubuntu on that partition ! .. never have I seen that like .
> 
OK - off we go again with the Live USB....


happy result, no luck to it. pay attention to those details and see ya up on the other side.

---

### Post by 2CV67 on 2014-09-07
This time, the proposed default for bootloader is /dev/sda, as expected.

I suspect that the last time, the selection may have been accidentally shifted while setting options for the target partition?

Maybe accidentally brushing the touchpad?

I don't feel like revisiting the scene of the crime to check...

---

### Post by 2CV67 on 2014-09-07
Installation (bare) finished.

So first thing is to see what boots.
Grub screen shows expected Ubuntu etc & Windows etc.

Booting to Ubuntu OK.
Booting to W7 brings up the same grub screen again!!!
Booting to W7 Recovery does go to the recovery system, but recovery loses all data, so I hesitated & chose 'Exit'.
Next attempted boot > "error: no such partition. Entering rescue mode... grub rescue>_".

So that seem to be the end of that one.

Tomorrow I can only try to install Ubuntu over the whole drive, I suppose?

---

### Post by Bashing-om on 2014-09-07
2CV67; Naw .. 

on a re-install of either of the operating systems, let's try and fix !
Seems to me that the Windows boot code is corrupted.
I would with Windows 'fixmbr' re-install Windows boot code ( wiping out ubuntu in that process ) and see if now Windows boots.

OK Windows' boot code restored and booting fine,
Now from the liveDVD once more installing ubuntu's boot code that will pick up Windows- at a later time -.
```

sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
With 'fdisk' make sure that ubuntu is on device 'sda6' ; adjust otherwise !
Now reboot into ubuntu:
and from ubuntu terminal:
```

sudo update-grub

```

Now I expect all to be
[INDENT][INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-08
> **Bashing-om said:**
> I would with Windows 'fixmbr' re-install Windows boot code 
I need more explanation there, even after a bit of browsing.

Last night, after my last post, I thought I might as well try the built-in recovery procedure, even if that wiped Windows data - nothing vital there which is not backed up.
With this Netbook, there is no CD/DVD reader & no recovery DVD.
Recovery is on-board & should be accessible by pressing F9 during boot.
But it doesn't work - I just get to the usual grub recovery prompt!

Then I remembered that I had once been into recovery, on a first attempt from the normal-looking grub screen after installing Ubuntu.

So I installed Ubuntu again (!) & rebooted, when I got a good grub screen & selected Windows Recovery.

Once inside, there was no option to just repair mbr, simply "Recovery".
So I tried that & it churned away for 10 minutes & stopped at a peaceful scene, so I assume had finished.
But attempted booting still only gives me the grub recovery prompt.

Hmmm...

At the moment, I am re-re-re-installing Ubuntu, since my notes say I do get one shot at booting it after an install...

I confirm that the original problem (bootloader on sda1 instead of sda) is only too easy to do.
The touchpad of the EeePC is way too sensitive (I disable touch-to-click in all OS's, but can't during install).
Then as you necessarily pass over the bootloader selection window going between setting up the partition & clicking "next", it often happens that a different bootloader place is accidentally set!!!!  Grrr...

---

### Post by 2CV67 on 2014-09-08
OK.

Ubuntu installed OK & first boot showed a correct-looking Grub screen.

Actually booted to a real working (bare essentials) Ubuntu.
Carefully avoided trying W7.

Tried a reboot to Ubuntu - and that works too.
And a full shutdown & reboot.

So now I need clues to resuscitate Windows, from inside Ubuntu...
Probably same/similar to your yesterday's suggestion, but it would be safer to spell things out from today's situation.

Thanks!

---

### Post by 2CV67 on 2014-09-08
Today's GParted:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/ffbb1d5b-0c14-4ccb-b004-b29a44422b95_zps439a8877.png[/IMG]

---

### Post by 2CV67 on 2014-09-08
Bootinfoscript:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         241,176,574   488,355,839   247,179,266   5 Extended
/dev/sda5         484,259,840   488,355,839     4,096,000  82 Linux swap / Solaris
/dev/sda6         241,176,576   484,259,839   243,083,264  83 Linux
/dev/sda4         488,355,840   488,397,167        41,328  ef EFI (FAT-12/16/32)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        720482300481F6FF                       ntfs       
/dev/sda2        86F4-D40A                              vfat       
/dev/sda5        fc4e1a58-00d6-42a0-b9a3-299f5504ebe4   swap       
/dev/sda6        a6af4232-18a9-46ca-936b-47d093eae2d0   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
else
  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6af4232-18a9-46ca-936b-47d093eae2d0' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
	else
	  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
	fi
	linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=a6af4232-18a9-46ca-936b-47d093eae2d0 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a6af4232-18a9-46ca-936b-47d093eae2d0' {
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-a6af4232-18a9-46ca-936b-47d093eae2d0' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
		else
		  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=a6af4232-18a9-46ca-936b-47d093eae2d0 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-a6af4232-18a9-46ca-936b-47d093eae2d0' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
		else
		  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=a6af4232-18a9-46ca-936b-47d093eae2d0 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
	else
	  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a6af4232-18a9-46ca-936b-47d093eae2d0
	else
	  search --no-floppy --fs-uuid --set=root a6af4232-18a9-46ca-936b-47d093eae2d0
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-720482300481F6FF' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  720482300481F6FF
	else
	  search --no-floppy --fs-uuid --set=root 720482300481F6FF
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-86F4-D40A' {
	insmod part_msdos
	insmod fat
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  86F4-D40A
	else
	  search --no-floppy --fs-uuid --set=root 86F4-D40A
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=a6af4232-18a9-46ca-936b-47d093eae2d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fc4e1a58-00d6-42a0-b9a3-299f5504ebe4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-fVy9ADw0/Tmp_Log: No such file or directory

```

---

### Post by 2CV67 on 2014-09-08
Well - bootinfoscript looked OK so I dared to boot to W7 - and it works now!

At least, I am in the middle of a long "setup" but that seems like a good place to be, never mind the negligible data loss.

I can only imagine that the Windows recovery did work, but don't know why the results were not there on first attempt.

---

### Post by 2CV67 on 2014-09-08
After that setup - W7 worked.
I tried booting to it again - OK.
Then I accidentally booted to W7 Recovery - immediately selected "Exit", but the damage was done.
All attempts at booting lead to grub recovery prompt.

I did manage to boot one time to W7 via SuperGrubDisk, but not any more.

GParted shows the Ubuntu partition "unallocated" again.

Ho hum...

---

### Post by Bashing-om on 2014-09-08
2CV67; Great !

Looking good ?? On all fronts ?

See boot-repair is smart, real smart !
On our own with out that Windows' utility disk would not have been able to fix Windows' boot code.

I am relieved that things are working out.

[INDENT][INDENT][INDENT]good things can happen
[/INDENT][/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-08
> **Bashing-om said:**
> 2CV67; Great !

Looking good ?? On all fronts ?

See boot-repair is smart, real smart !
On our own with out that Windows' utility disk would not have been able to fix Windows' boot code.


I think you have missed my post just before this one...

Things are not great at all!

By the way, Boot-Repair seems not to be available for 14.04.

I did download & use bootinfoscript alone.

---

### Post by Bashing-om on 2014-09-08
2CV67; Well !!

Bad Thing Can Happen too -

Things were working out.
Let's see if "W7 Recovery" did not once more take control of the hard drive and in repairing Windows back to it's own specification, just plain wipe out the partition table for ubuntu !
What now does GParted show for the partitioning ? once more "unallocated" ?

Now, up front I am no longer Windows literate, and have no desire to be, but if it were me I would copy that recovery partition off to DVD and delete that partition from off the hard drive so that this does not happen again. As to what it would take to make that "recovery DVD" bootable,- so it is usable - I do not know.

Then I bet we install ubuntu once more and chainload Windows onto it's boot menu.


[INDENT][INDENT]Windows messes me up once, Windows dang fool
[INDENT][INDENT][INDENT]Windows messes me up trice, ME dang fool
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-08
2CV67; Well !!

Bad Things Can Happen too -

Things were working out.
Let's see if "W7 Recovery" did not once more take control of the hard drive and in repairing Windows back to it's own specification, just plain wipe out the partition table for ubuntu !
What now does GParted show for the partitioning ? once more "unallocated" ?

Now, up front I am no longer Windows literate, and have no desire to be, but if it were me I would copy that recovery partition off to DVD and delete that partition from off the hard drive so that this does not happen again. As to what it would take to make that "recovery DVD" bootable,- so it is usable - I do not know.

Then I bet we install ubuntu once more and chainload Windows onto it's boot menu.


[INDENT][INDENT]Windows messes me up once, Windows dang fool
[INDENT][INDENT][INDENT]Windows messes me up trice, ME dang fool
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 2CV67 on 2014-09-08
I now have both Ubuntu & W7 working (no frills yet).

What I had to do to get there was:
1. Install Ubuntu to give me a full grub screen (at that stage I can reboot to Ubuntu anytime OK).
2. From that screen, boot to Windows Recovery (that eventually gives me W7 but I cannot reboot to anything at all afterwards, not even W7. Booting goes to grub recovery screen & GParted shows Ubuntu partition as unallocated).
3. Install Ubuntu again & NEVER boot to Windows Recovery.

I confirmed that twice.

Obviously that is far too dangerous to live with.

My first approach will be to use Grub Customizer to hide the Windows Recovery entry.

Then I will look at your suggestion of copying the partition off-unit somehow.
Maybe onto an External Hard Drive for storage until I get a big-enough USB Stick - there is no DVD drive for the Netbook.
I can see the contents OK in Nautilus...

I will sleep on that one though (probably a few times!).

---

### Post by Bashing-om on 2014-09-08
2CV67; Perseverance !

That's the ticket ! At least now is known what NOT to do .

I know of nothing else to be done presently. As such how about closing this thread solved as the original situation is handled.

Any other issues, feel free to open up new threads.There are those who do have the experience with a Windows Netbook who will advise on a procedure to backup that recovery partition. They will not see the need from this thread.
Opening a new thread will gain a wider audience.

[INDENT]pick urself up
[/INDENT][INDENT]dust off
[INDENT][INDENT][INDENT]and have at it again
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Michael_Cooley on 2015-02-02
The thread that most closely matches my problem has been closed., However, the title of this thread is apropo so here goes. (This is my first post 5 minutes after getting my passwords, so please, no flames if I've broken some convention here.) 

I have ubuntu and Win 7 installed. I had downloaded something while booted into windows. The next day I was able to boot but not login (it just kept whirring). I shut down again and chose with win rescue option. When it rebooted I got:

error: no such partition.
grub rescue>

I followed the direction found elsewhere in this forum. The 'ls' listed the four partitions. However, I could not do an 'ls' on any of them. They all reported "error: unknown file system." I tried every variation I could think of and tried to list any number of subdirs as instructed in the earlier thread.

I have no win install disk. I need to rescue what I have. I hate win and would be happy to dump it from this computer, but no linux app I've found will handle .docx files. Hmmm.... I guess *that's* really my problem. :-)

Any help appreciated.

---

### Post by Bashing-om on 2015-02-03
Michael_Cooley: Hi ! Welcome to the forum .

Posting in this thread - in this case - is just fine.

So something has wiped out the boot code, huh ?
We can fix that for ubuntu, and maybe, just maybe Windows will be OK.

You will need a liveDVD(USB) of the release that you have installed. When you advise you have this live medium on hand we will proceed.

It's 'buntu
[INDENT][INDENT]it is always fixable
[/INDENT][/INDENT]

---

