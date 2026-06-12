---
title: "Re: Can't boot cloned 14.04"
date: 2015-12-11
forum: General Help
---

### Post by Bucky Ball on 2015-12-11
Note: This has been through a few permutations, so to cut to the chase, have a quick read of the first post and then go directly to where I am currently [battling with the chainloader entry]("http://ubuntuforums.org/showthread.php?t=2306013&page=3&p=13406382&viewfull=1#post13406382") on the third page. Choosing the SSD install at boot loops me back to the kernel selection again. :|
_____

Hi all.

Spot of bother and posted in this section, although I suppose the problem could be seen as an install issue ... with a twist. Other staff please move if you see fit.
___

I run a tweaked Ubuntu minimal 14.04 install on a Toshiba Satellite Pro L510. Runs great, rock solid and customised to perfection. I figured the only thing that could make it any better was running it from an SSD. As I needed to grab another media server drive at the computer shop and had a little extra cash, I bought myself an early christmas present and got to work on it. The issue at hand.
___

* About six months ago I pulled the optical DVD drive out of my machine and replaced it with a hard drive bay and shoved an old 80Gb HDD in there. Worked fine. So I pulled that and replaced with the SSD, booted up, all good. Original hard drive sda, SSD = sdb. Created an EXT4 partition on it, changed permissions and mounted, copy just over a gig of data from sda to sdb1 in no time flat. Cool.

* I did my last fsarchiver backup of my data and OS partition a couple of nights ago so I simply restored the sda10 OS image to the sdb1 partition on the SSD. All good. Looks to be all there. Did a 'sudo update-grub' in my original install and it picked up the SSD and install (sdb1). Reboot, boot to the sdb1 ... boots to sda10 (the original install).

* I finally figure out that both sda10 and sdb1 have the same UUID (figures) which might be causing a problem so I change the UUID on the SSD with 'uuidgen' then change the /etc/fstab file in the SSD install to reflect this change. I then update grub again for the heck of it, reboot and same. Reboots into sda10. So I stick a boot flag on sdb1, reboot, boots to sda10. :-k

* Figuring the image restore might have been corrupted somehow (although it showed no errors at the end) I go again. I wipe sdb1, rewrite the partition table, create an EXT4 partition and fsarchiver restore the image again (no errors reported). Go through the steps above again and pretty much the same thing.

* Then I find [this page]("https://help.ubuntu.com/community/MovingLinuxPartition#Step_4:_Generate_and_update_UUID"). I open grub.cfg, as instructed, on the SSD install and edit all instances of 'hd0' to 'hd1' and change the sda10 UUID to the new UUID of the sdb1 install. Update grub, reboot, choose the sdb1 install, black screen. That's it. ctl+alt+F1 does nothing. The only option is to hard shutdown with the power button. (Ouch)

* I'd be happy to follow the rest of the instructions on the link I provided but stopped at the instructions about using the Disks utility. It advises to switch off 'Mount at startup' for the sda10 install and switch it on for the sdb1 install. This I don't like and am very reluctant to do. This is my workhorse, rock solid uni computer and it can't break! 

* At the moment I have the original sda10 install to fall back on when the sdb1 install falls over with my experiments. I have backups of everything important, not about that. If I change sda10 to not mount at boot, change the sdb1 install to mount at boot at the mountpoint / I am in deep poop if things go pear-shaped and I can't get back into sda10. I could be here til 6am attempting to fix it (because I would have no choice but to stick at it til it's fixed ... I have a lot to do). 
___

One last odd thing: Boot Repair refuses to run. I installed, it launches, starts searching, then the block that goes from left to right stops and BRepair hangs indefinitely. So I tried it from a USB. Exactly the same. I left it for about 40-45 minutes. Nothing. Stuck.

I'm hoping someone might have some suggestions here as, even though I can still work with the original install, I'm very keen to speed things up and start using the new SSD I've been craving! :D 

When I installed an SSD in my desktop about a year ago I cloned the OSs, took the original drive out, SSD in, cloned them to the SSD and it took about an hour or less. I've been at this for about eight and figure it is because both partitions are identical and in the same box and there is a conflict I'm missing because of that. 

Thanks in advance. Any further info required just ask (and yes, I'd like to see the Bootinfo, too, if I only could).

PS: Happy to start from scratch if I have bumbled something obvious to someone else along the way.

Just jumping through a few more hoops. [I did this]("https://help.ubuntu.com/community/MovingLinuxPartition#Step_5:_Update_grub_and_fstab") part of the guide, rebooted to the original sda10 install, and the SSD is nowhere to be seen. 'sudo blkid', gparted. Completely vanished. :|

I omitted this which perhaps should have been performed while I had the sdb1 grub.cfg file available, because it isn't now (going to boot from a live session and see if that finds the SSD):

```
sudo grub-install -d /media/<new partition uuid>/usr/lib/grub/[instance] /dev/sda

# Where [instance] is the version you want to make bootable
```

This happened when I did this last time through if I remember rightly. Stuck now ...

* Update: Booted to a live session, copied the sda10 grub.cfg to the sdb1 grub.cfg, overwriting the changes I'd made outlined in the 'Moving the install' link (I kept a copy with the changes for later), set the boot flag with Gparted, rebooted to the sda10 original install and sdb is back visible again. There's something. 

So, what next? :-k Cuppa tea I think ...

* If I physically swapped the drives over and sdb became sda would that make a difference I wonder???

I wiped the partition and used [this guide]("https://frankfzw.wordpress.com/2014/12/23/migrate-ubuntu-14-04-from-hdd-to-ssd/"). The ssd install appears in grub menu at boot, click it, boots to black screen with blinking cursor, then goes to normal boot to the hard drive, not the SSD install.

* Doh. Forgot to change the fstab on the ssd install. Correct the UUID, reboot, this time a black screen, no cursor. Hard shutdown. Stuck again. I think a fresh install is looming unfortunately as out of time for this (some hours ago ;)) ... :|

---

### Post by sudodus on 2015-12-12
> **Bucky Ball said:**
> Just jumping through a few more hoops.
...
So, what next? :-k Cuppa tea I think ...

* If I physically swapped the drives over and sdb became sda would that make a difference I wonder???

After the cup of tea: Yes, if sdb became sda ...

Are you running in UEFI mode or BIOS mode?

If GPT, have you checked with gdisk, that the partition table is good? Some standard repair action might be suggested for example if the backup of the partition table at the end is bad or in a bad position.

-o-

If the SSD is at least as big as the HDD, I would use Clonezilla. Otherwise I would make a partition table with the proper file systems, try a dry run with

```
sudo rsync -Havn source/ target
```

and then copy 'everything' with rsync (after removing the option n). If UEFI mode that might be enough. If BIOS mode I would install the bootloader.

Finally I would shutdown, remove the source drive, the HDD, and try to boot from the SSD with your new system.

Maybe this link will give you some useful tips:

[Install Ubuntu in UEFI mode on second HDD without affecting first HDD](http://ubuntuforums.org/showthread.php?t=2305876)

*Dennis N's* tips helped *gamelife*, the OP of that thread.

---

### Post by Bashing-om on 2015-12-12
Bucky Ball; Ouch !

AS lot of hope, effort and little return. I feel for you.

When booted from a liveUSB, what does gdisk report for the partitioning ?
GPT ? Did you make a boot partition to support this partitioning scheme ?

An SSD .. did the manufacturer have in mind to support Windows' fast boot ? 
What have we for meta data on that SSD ?
```

sudo wipefs /dev/sdb

```
  "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets. <- No,(meta data was removed) my return for your peace of mind:
```

sysop@1404mini:~$ sudo wipefs /dev/sda
[sudo] password for sysop: 
wipefs: WARNING: /dev/sda: appears to contain 'dos' partition table
sysop@1404mini:~$ 

```

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-12-12
Ok, thanks for the input all. Working! In a way. But not with the solution any of us probably thought.

I followed [the guide I linked to earlier]("https://frankfzw.wordpress.com/2014/12/23/migrate-ubuntu-14-04-from-hdd-to-ssd/") to the letter. Everything seemed to go fine. As it happens, I may have had this working just fine fifteen hours ago, but I never would have known. Reason? Remember I mentioned that sdb was in a hard drive bay were the optical DVD drive used to be in the laptop??? Give you any clues???

That's correct, biscuit or doughnut if you guessed. I reboot, hit F12 to get the boot device options, I boot from CD/DVD option, boots to grub, choose sdb1 install, black screen with flashing cursor for a few seconds then up she pops! Straight into the sdb1 install, and it is IDENTICAL in every way to the sda install. Even my multiple shortcut keys and symlinks to the data partition work! 

(Yes, checked in Gparted and sdb1 is / and the /swap and /storage partitions on sda are both mounted and working fine. All installs on sda are not mounted ... and I hit the Libreoffice shortcut key and am at a new document instantaneously!)
____

So this is where I'm at:

- Boot as per normal to the hard drive, choose sdb1, loops me back to the grub list screen to choose a kernel. This doesn't resolve if I choose sdb1 a few times.
- Choose CD/DVD or FDD (floppy disk drive) as the boot device, choose sdb1 install from grub list, get flashing cursor for a few seconds then boots to the sdb1 install on the SSD and everything is faultless. 

So I can and have managed to boot the cloned 14.04, just can't boot it without some inconvenient hoop jumping. 
____

The only thing that could make this complete is not have to choose CD/DVD or FDD as the boot device when I want to boot to the SSD install. Any ideas what could be happening on that front?

If I set the BIOS to boot the CD/DVD or FDD first, oddly, it doesn't seem to make any difference. Only from the boot device options does it work. My BIOS doesn't give me the option of setting the SSD or the HDD individually. It lists them BOTH as the hard drive on the same line together (Toshiba HD/SSD). The ODD (optical disk drive) is listed as the SSD but if I set that it doesn't work either. 'ODD' doesn't appear on the boot device list. 

And sorry I didn't mention it earlier. Not UEFI install. My computer/BIOS doesn't do UEFI so that and Windows issues are null. :)

PS: I would happily provide bootinfo, but for some bizarre reason, Boot Repair will not run, it just hangs, on sda10, sdb1 install or the USB version. :-k

I have the bootinfoscript somewhere. I'll run that and post in a mo. Further info required, just ask.

Thar she blows ... sorry I didn't get this up earlier. Never thought of bootinfoscript. 

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda10 and looks at sector 164978352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 112 for .
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048    86,960,127    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3    *     86,966,270   602,276,849   515,310,580   5 Extended
/dev/sda5          86,966,272   116,260,863    29,294,592  83 Linux
/dev/sda6         179,317,593   511,399,935   332,082,343  83 Linux
/dev/sda7         594,067,698   602,276,849     8,209,152  82 Linux swap / Solaris
/dev/sda8         116,262,468   147,155,399    30,892,932  83 Linux
/dev/sda9         563,226,624   594,067,455    30,840,832   7 NTFS / exFAT / HPFS
/dev/sda10        147,159,040   179,316,735    32,157,696  83 Linux
/dev/sda11        511,401,984   542,644,223    31,242,240  83 Linux
/dev/sda4         602,284,032   625,141,759    22,857,728  17 Hidden NTFS / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    41,263,103    41,261,056  83 Linux
/dev/sdb2          41,263,104   212,031,487   170,768,384   5 Extended
/dev/sdb5          41,265,152    83,273,727    42,008,576  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E10BBBF10BB7C89                       ntfs       System
/dev/sda10       40c1d59b-20a7-4096-8cc4-fd65e0a1fb93   ext4       TrustyMini
/dev/sda11       865e6caa-b7bf-49b5-8d41-bf7e8d03be32   ext4       Mini
/dev/sda2        7060EA3E60EA0B24                       ntfs       S3A8406D004
/dev/sda4        8AD8245BD82447B1                       ntfs       HDDRECOVERY
/dev/sda5        93f00b46-2cf5-4b46-83be-f708cf831675   ext4       10.10
/dev/sda6        0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1   ext4       home
/dev/sda7        63d86782-bff4-41c1-924f-37d093fbe371   swap       
/dev/sda8        7343d254-e594-4593-8258-3ecebdb376ef   ext4       12.04
/dev/sda9        6B8E2F2A62CEE191                       ntfs       Misc
/dev/sdb1        26e4f38f-0e49-460a-9c7d-62db2c391ea3   ext4       
/dev/sdb5        6f9c6a63-ee83-4b6c-88d1-dd33d23b4f8e   ext4       Stuff

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /mnt/boot-sav/sda10      ext4       (rw)
/dev/sda11       /mnt/boot-sav/sda11      ext4       (rw)
/dev/sda1        /mnt/boot-sav/sda1       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /mnt/boot-sav/sda2       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4        /mnt/boot-sav/sda4       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /mnt/boot-sav/sda5       ext4       (rw)
/dev/sda6        /mnt/storage             ext4       (rw,errors=remount-ro)
/dev/sda8        /mnt/boot-sav/sda8       ext4       (rw)
/dev/sda9        /mnt/boot-sav/sda9       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /                        ext4       (rw,noatime,nodiratime,discard,errors=remount-ro)
/dev/sdb5        /mnt/boot-sav/sdb5       ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Xubuntu 12.04 Linux 3.2.0-57-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Ubuntu, with Linux 3.2.0-57-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Raring 3.9.0-030900-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7060EA3E60EA0B24
	chainloader +1
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt  quiet splash acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	echo	'Loading Linux 2.6.38-020638-generic ...'
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
### END /etc/grub.d/20_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_linux_xen ###
### END /etc/grub.d/30_linux_xen ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=93f00b46-2cf5-4b46-83be-f708cf831675	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/home	ext4	defaults	0	2
#Entry for /dev/sda4 :
#UUID=8AD8245BD82447B1	/media/HDDRECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda11 :
UUID=6B8E2F2A62CEE191	/media/Misc	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda2 :
#UUID=7060EA3E60EA0B24	/media/S3A8406D004	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda1 :
#UUID=3E10BBBF10BB7C89	/media/System	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1
insmod jpeg
if background_image /binky/Pictures/FromHPLappy/PICS/NRiversRiverhalf.jpg; then
  set color_normal=black/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-61-generic
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/31_linux_proxy ###
menuentry "Ubuntu, with Linux 3.2.0-59-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.2.0-59-generic ...'
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.2.0-58-generic ...'
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-58-generic
}
submenu "Previous Linux versions"{
menuentry "Ubuntu 10.10 Linux 2.6.38-020638-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Raring 3.9.0-030900-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.9.0-030900-generic ...'
	linux	/boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.9.0-030900-generic
}
}
### END /etc/grub.d/31_linux_proxy ###

### BEGIN /etc/grub.d/33_linux_xen ###
### END /etc/grub.d/33_linux_xen ###

### BEGIN /etc/grub.d/35_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/35_memtest86+ ###

### BEGIN /etc/grub.d/36_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/36_os-prober_proxy ###

### BEGIN /etc/grub.d/37_uefi-firmware ###
### END /etc/grub.d/37_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda8 :
UUID=7343d254-e594-4593-8258-3ecebdb376ef	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda10 :
UUID=6B8E2F2A62CEE191	/media/Misc	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/media/home	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0

# XPVbox /dev/sda10
# UUID=dbfd8a62-2d43-4a16-aa6c-f926004553e0       /media/XPVbox       ext4    errors=remount-ro       0       1

--------------------------------------------------------------------------------

====================== sda8/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sda8: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sda8: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================== sda10/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos10'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
else
  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E10BBBF10BB7C89' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E10BBBF10BB7C89
	else
	  search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos11'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	else
	  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	fi
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' $menuentry_id_option 'osprober-gnulinux-advanced-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-61-generic
	}
}

menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-7060EA3E60EA0B24' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  7060EA3E60EA0B24
	else
	  search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8AD8245BD82447B1' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  8AD8245BD82447B1
	else
	  search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Ubuntu 10.10 (10.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-93f00b46-2cf5-4b46-83be-f708cf831675' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
	else
	  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	fi
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
submenu 'Advanced options for Ubuntu 10.10 (10.10) (on /dev/sda5)' $menuentry_id_option 'osprober-gnulinux-advanced-93f00b46-2cf5-4b46-83be-f708cf831675' {
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic--93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic-root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt-93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7343d254-e594-4593-8258-3ecebdb376ef' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
	else
	  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	fi
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' $menuentry_id_option 'osprober-gnulinux-advanced-7343d254-e594-4593-8258-3ecebdb376ef' {
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
}

menuentry 'Ubuntu 14.04.3 LTS (14.04) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu 14.04.3 LTS (14.04) (on /dev/sdb1)' $menuentry_id_option 'osprober-gnulinux-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	menuentry 'Ubuntu (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-generic
	}
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

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda10 :
UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 / ext4 errors=remount-ro 0 1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/mnt/storage	ext4	errors=remount-ro	0	1
#Entry for /dev/sda9 :
UUID=6B8E2F2A62CEE191	/mnt/Misc	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda12 :
#UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32	/mnt/mini12.04	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0

#sdb1
#UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93       /       ext4    errors=remount-ro       0       1


#Entry for /dev/sdc1 :
#UUID=F0C48990C4895A2C	/mnt/2013BUP1	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sdb2 BUP2 external
#UUID=303f7548-cb7b-426d-80a1-a2e650aba95b	/mnt/BUP2	ext4	errors=remount-ro	0	1


/dev/disk/by-uuid/51b8d826-c245-46da-bd64-42234c80a02c / auto errors=remount-ro 0 0
/dev/disk/by-uuid/1fd9a713-1d62-4084-a2b3-972989d5da9d / ext4 errors=remount-ro,noauto 0 0
--------------------------------------------------------------------------------

====================== sda10/boot/extlinux/extlinux.conf: ======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)


================= sda10: Location of files loaded by Syslinux: =================

           GiB - GB             File                                 Fragment(s)


============== sda10: Version of COM32(R) files used by Syslinux: ==============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================== sda11/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos12)'
  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-85-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-85-generic ...'
	linux	/boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-85-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-64-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-64-generic ...'
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-61-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-61-generic ...'
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-61-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	chainloader +1
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Xubuntu 12.04 Linux 3.2.0-57-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Ubuntu, with Linux 3.2.0-57-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Raring 3.9.0-030900-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.9.0-030900-generic
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda12 :
UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
#UUID=8AD8245BD82447B1	/media/HDDRECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
# UUID=7060EA3E60EA0B24	/media/S3A8406D004	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
# UUID=3E10BBBF10BB7C89	/media/System	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda8 :
UUID=7343d254-e594-4593-8258-3ecebdb376ef	/mnt/12.04	ext4	errors=remount-ro	0	1
#Entry for /dev/sda9 :
UUID=6B8E2F2A62CEE191	/mnt/Misc	ntfs    defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/mnt/storage	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0
--------------------------------------------------------------------------------

====================== sda11/boot/extlinux/extlinux.conf: ======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)


================= sda11: Location of files loaded by Syslinux: =================

           GiB - GB             File                                 Fragment(s)


============== sda11: Version of COM32(R) files used by Syslinux: ==============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
else
  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E10BBBF10BB7C89' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E10BBBF10BB7C89
	else
	  search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Ubuntu 14.04.3 LTS (14.04) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu 14.04.3 LTS (14.04) (on /dev/sda10)' $menuentry_id_option 'osprober-gnulinux-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	menuentry 'Ubuntu (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos11'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	else
	  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	fi
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' $menuentry_id_option 'osprober-gnulinux-advanced-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-61-generic
	}
}

menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-7060EA3E60EA0B24' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  7060EA3E60EA0B24
	else
	  search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8AD8245BD82447B1' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  8AD8245BD82447B1
	else
	  search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Ubuntu 10.10 (10.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-93f00b46-2cf5-4b46-83be-f708cf831675' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
	else
	  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	fi
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
submenu 'Advanced options for Ubuntu 10.10 (10.10) (on /dev/sda5)' $menuentry_id_option 'osprober-gnulinux-advanced-93f00b46-2cf5-4b46-83be-f708cf831675' {
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic--93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic-root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt-93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7343d254-e594-4593-8258-3ecebdb376ef' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
	else
	  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	fi
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' $menuentry_id_option 'osprober-gnulinux-advanced-7343d254-e594-4593-8258-3ecebdb376ef' {
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
## /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc			/proc           proc    nodev,noexec,nosuid				0       0
#Entry for /dev/sdb1 :
UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 / ext4 discard,noatime,nodiratime,errors=remount-ro 0 1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1       /mnt/storage    ext4    errors=remount-ro       0       1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371       none    swap    sw      0       0

#Entry for /dev/sdb5
#UUID=6f9c6a63-ee83-4b6c-88d1-dd33d23b4f8e
--------------------------------------------------------------------------------

====================== sdb1/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-EWTE3LoX/Tmp_Log: No such file or directory


```

---

### Post by Bashing-om on 2015-12-12
Bucky Ball; Hummm ...

Just a thought;
> 
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
bk
/dev/sda5        93f00b46-2cf5-4b46-83be-f708cf831675   ext4       10.10

Do you really want release 10.10 to be the controlling authority to boot ?
Maybe a bit long in the tooth to support grub2 in these later releases on other partitions (??)

Are you embedding the boot code for :
> 
Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda10 and looks at sector 164978352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 112 for .

in the partition ? If so why not for the other additional installs ?
As you know, there can be but one controlling authority installed to the MBR , this one controls all the other booting installs .

Yeah, controlling grub in multi-boot situations is an art - in and of it's self .
Me-thinks we may gave grub all confused .

[INDENT][INDENT]recon ?
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-12-12
sda10 should be in charge of grub. At least I thought it was. I figured I could do 'sudo install-grub' from the ssd install and that would control grub, but I don't want that yet. I want the original install to have it. 10.10 is there because I'm a bad housekeeper. Ignore. ;)

Not sure what you mean by 'embedding the boot code', sorry. You mean in the partition and not the drive (sd*)? Probably a recommended repair using Boot Repair a couple of years ago? Not sure. Played around a lot with this box over the last five years. :)

* But yea:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
```

Looks in partition 112 for .? What's with that? :-k

---

### Post by sudodus on 2015-12-12
Is it important to have both the HDD and SSD connected at the same time? It will be rather complicated (but should work).

Have you tried to boot from the SSD when the HDD is disconnected? Maybe if you make it work this way, it can also work, when you connect the HDD afterward, at least if you have unique UUIDs for the partitions.

---

### Post by Bucky Ball on 2015-12-12
> **sudodus said:**
> Is it important to have both the HDD and SSD connected at the same time? It will be rather complicated (but should work).

Imperative. This is a laptop. The second drive (SSD) is in a hard drive bay which fits in place of the DVD drive bay. That's why I can successfully boot when I hit F12 and select FDD or CD/DVD then the ssd install at the grub list at boot but can't when I let it roll and boot from the hard drive ... at least that's what I'm figuring. Selecting ssd install booting from HDD takes me back to the grub list of kernels.

No external drives involved. Disconnecting not an option (although I did think earlier that swapping them over might work). I'm going to do a bit of house cleaning on the sda, but I still want to be able to boot some installs from it, so I'd have more problems if I swapped them now.

PS: Yep. Made sure the UUIDs were not the same and fstab(s) were correct.

---

### Post by sudodus on 2015-12-12
In this case you may have to look into the **grub.cfg** file and check that the menu entries point to the correct drive in all cases (the SSD and not the HDD).

---

### Post by Bucky Ball on 2015-12-12
The entries in grub.cfg on the ssd install point to hd1, the ssd, and to hd0 for all the others. You're saying change them all even though all other installs are  installed on hd0? 

It did make me think of something, though. Do the other entries need to be there at all? I only want to be able to boot sdb1 install from grub on sda. I don't need to be able to boot all the installs on sda from the grub on sdb. If you know what I mean. I could just remove those entries from the ssd grub.cfg? The only partitions the ssd install needs are /storage and /swap and they're up, accessible and running from boot.

---

### Post by Bashing-om on 2015-12-12
Bucky Ball; Nother thought.

Boot the SSD from grub ?
That is the point I always start my trouble shooting boot issues from .
As you may remember, I too have had my issues multi-booting . Learned a bunch making my system boot the way i want it to .

[INDENT][INDENT]a complex web
[INDENT][INDENT][INDENT]we weave for ourselves
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2015-12-12
> **Bucky Ball said:**
> The entries in grub.cfg on the ssd install point to hd1, the ssd, and to hd0 for all the others. You're saying change them all even though all other installs are  installed on hd0? 

I think hd0 is always the booted drive (so in this case /dev/sdb).
> 
It did make me think of something, though. Do the other entries need to be there at all? I only want to be able to boot sdb1 install from grub on sda. I don't need to be able to boot all the installs on sda from the grub on sdb. If you know what I mean. I could just remove those entries from the ssd grub.cfg? The only partitions the ssd install needs are /storage and /swap and they're up, accessible and running from boot.

You are right. If you do not want to boot from the SSD, it is enough to run ```
sudo update-grub
``` when booted from the HDD to get the SDD into the grub menu. But when you get new kernels in the SSD system, I think you have to update-grub in the HDD too, or use 40_custom.

It is also possible to add a chainloading entry into it via 40_custom in the HDD, as described in for example [FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading), but then you must have a working grub system in the SSD.

---

### Post by Bucky Ball on 2015-12-12
> **sudodus said:**
> I think hd0 is always the booted drive (so in this case /dev/sdb).

That's what I was thinking from the start. Might have something to do with it. Thanks for the info. sdb is hd1 though I think. :)

> **sudodus said:**
> ... when you get new kernels in the SSD system, I think you have to update-grub in the HDD too, or use 40_custom.

With you. I have three or four installs on sda so know the ropes there.

> **sudodus said:**
> It is also possible to add a chainloading entry into it via 40_custom in the HDD, as described in for example [FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading), but then you must have a working grub system in the SSD.

Well, I did 'sudo grub-install /dev/sdb' from the HDD and when booted in to the ssd so I thought I would have grub installed there, but no dice with the chainloading. (I have since run that command from the HDD to /dev/sda.) Gives me an entry in the HDD grub at boot (SSD (sdb1)), but when I click it, takes me to this:

```
error: /boot/grub/i386-pc/ext4.mod not found
error: hd1 cannot get C/H/S values
```

Currently trying to nut out what that means ... 

Thanks for the input. :)

---

### Post by Bashing-om on 2015-12-12
Bucky Ball; Hummm ...
> 
error: /boot/grub/i386-pc/ext4.mod not found


My report:
```

sysop@1404mini:~$ ls -al /boot/grub/i386-pc/ext4.mod
ls: cannot access /boot/grub/i386-pc/ext4.mod: No such file or directory
sysop@1404mini:~$ 

```

So what is attempting to make that call ? Are we back to grub1.99 not compatible with grub2 ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-12-13
Okay, oldfred gave me some tips on [another thread]("http://ubuntuforums.org/showthread.php?t=2306106"). Posting this for his benefit and might give someone else clues also. 

I ran 'sudo debconf-show grub-pc':

```
  grub-pc/install_devices_failed_upgrade: true
  grub2/kfreebsd_cmdline:
  grub-pc/postrm_purge_boot_grub: false
* grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
  grub-pc/hidden_timeout: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/partition_description:
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/install_devices_empty: false
  grub2/device_map_regenerated:
  grub-pc/mixed_legacy_and_grub2: true
* grub2/linux_cmdline_default: splash quiet
* grub-pc/install_devices: /dev/disk/by-id/ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W
  grub-pc/install_devices_disks_changed:
  grub-pc/timeout: 10
  grub-pc/disk_description:
```

Used this tool and marked sdb (the SSD):

```
sudo dpkg-reconfigure grub-pc 
```

The output of 'more /var/cache/debconf/config.dat | grep /dev/disk':

```
Value: /dev/disk/by-id/ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W
 RAW_CHOICES = /dev/disk/by-id/ata-TOSHIBA_MK3263GSX_20B3FD6US, /dev/disk/by-id/ata-TOSHIBA_MK3263GSX_20B3FD6US-part10, /dev/disk/by-id/ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W
```

The Samsung is sdb and the Toshiba is sda. And 'more /etc/initramfs-tools/conf.d/resume' give me:

```
RESUME=UUID=63d86782-bff4-41c1-924f-37d093fbe371
```

... which is the UUID of my /swap partition. (The /swap is on sda7, the HDD, and the SSD install boots it and is using it fine.)

Hope that gives someone further clues because I'm still stuck here when I try and boot SSD install:

```
error: /boot/grub/i386-pc/ext4.mod not found
error: hd1 cannot get C/H/S values
```

I also now have two 'SSD' entries in my grub selection list at boot. Choosing either gives me the above errors, choosing the entry for 'Ubuntu on sdb1' takes me back to the selection list.

Incidentally, this is what I now have in /etc/grub.d/40_custom of the HDD boot on sda:

```
menuentry "SSD (on hd1)" {
        insmod part_msdos
        insmod part_gpt
        insmod ext4
        set root='(hd1,0)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
```

*** Further update: I discovered that apparently this is wrong:

```
insmod ext4
```

Use ext2 instead. So I changed it and now only get the one error when I try to boot the 'SSD (hd1)' (I gave sdb1 before, the entry is not that but hd1):

```
error: hd1 cannot get C/H/S values
```

Update and bit more info. Booted in to the SSD install at the moment and so thought I'd check the bootinfoscript in there out of curiousity. Found a problem. A couple of examples, both regarding the sdb1 install on SSD:

```
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
else
  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
```

```
menuentry 'Ubuntu 14.04.3 LTS (14.04) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
```

See the issue? It's got the 'hd1' part right, but the partition is shown as 'msdos1'! The install is on sdb1 which should be 'hd0'. That is what I have in 40_custom in the chainloader script. Should I change all of these by hand? (Easy enough in Leafpad, just time consuming.)

---

### Post by oldfred on 2015-12-13
You used the old bootinfoscript. It is not maintained anymore. :(
       Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Boot-Repair now uses the fork as that has fixed with grub2 the partition 112 in MBR issue, so we know which partition is really used.

You show two boot flags. You can only have one. And it should only be on the Windows NTFS partition with bootmgr & BCD. You have those files in both sda1 & sda2 so can use either. 

Boot-Repair normally copies Windows boot files from sda1 to sda2 as many users to not know the 100MB Windows boot partition is essential as not shown in Windows normally and they delete it. Then with no boot files cannot boot Windows at all. Usually those same users are ones without a Windows backup so getting another copy of bootmgr is not easy.

Can you boot drive caddy? We have seen some systems that while drive works in drive DVD caddy it is not a bootable device. But those users usually had to have grub or a boot partition on sda.

With BIOS the drive you boot from is always hd0.
I booted from sdc, sdd & sde on my old system. And even more confusing I had skipped a SATA port and a flash drive that would be sdf, becomes sdb and ever drive changes. Good thing for UUIDs, but still have to be careful on commands using devices. Also in grub I would use my own 40_custom entries with devices for other drives/partitions and often had to manually edit as I booted to fix drive number.

It looks like the grub.cfg in sda5 (10.10?) is a copy of one of your newer installs. It shows kernels 3.13 from 14.04 or 12.04.5. But if that is the grub you use to boot, then no sudo update-grub will update it.

I see some proxy files, so in at least one install you ran grub customizer. It creates its own grub files. I prefer to just turn off os-prober and use my own entries. With more than a couple of installs it gets very confusing. I have to regularly run bootinfoscript and made it part of my rsync backup of /home. 

And I add my own 40_custom entries to boot other installs. I learned from Ranch Hand who was booting the daily download in his partition 13.


 gksudo gedit /etc/grub.d/40_custom
```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
```

But note drive order issue about which can create problems.

Cavsfan documented some of the details with some input from Ranch Hand.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by Bucky Ball on 2015-12-13
Here's the bootinfoscript for a start. Thanks for the updated version link. :) 

The grubs appear to be look in the right places and no, not using 10.10 for grub as far as I know. To my knowledge sda10 is overseeing that. I'm wanting to boot from sda only and chainload to the install on sdb. I figure that is the best, and possibly only, way. 

Now I'm going to experiment with my chainloader entry because it is absolutely nothing like the version you've supplied! Thanks for that and wish me luck! 

```
                  Boot Info Script 0.72      [29 July 2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos10)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (12.04.5 LTS)
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of 
                       sda10 and looks at sector 164978352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks for (,msdos10)/boot/grub. It also embeds 
                       following components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_msdos biosdisk
                       -------------------------------------------------------
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (12.04.5 LTS)
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048    86,960,127    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3    *     86,966,270   602,276,849   515,310,580   5 Extended
/dev/sda5          86,966,272   116,260,863    29,294,592  83 Linux
/dev/sda6         179,317,593   511,399,935   332,082,343  83 Linux
/dev/sda7         594,067,698   602,276,849     8,209,152  82 Linux swap / Solaris
/dev/sda8         116,262,468   147,155,399    30,892,932  83 Linux
/dev/sda9         563,226,624   594,067,455    30,840,832   7 NTFS / exFAT / HPFS
/dev/sda10        147,159,040   179,316,735    32,157,696  83 Linux
/dev/sda11        511,401,984   542,644,223    31,242,240  83 Linux
/dev/sda4         602,284,032   625,141,759    22,857,728  17 Hidden NTFS / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    41,263,103    41,261,056  83 Linux
/dev/sdb2          41,263,104   212,031,487   170,768,384   5 Extended
/dev/sdb5          41,265,152    83,273,727    42,008,576  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E10BBBF10BB7C89                       ntfs       System
/dev/sda10       40c1d59b-20a7-4096-8cc4-fd65e0a1fb93   ext4       TrustyMini
/dev/sda11       865e6caa-b7bf-49b5-8d41-bf7e8d03be32   ext4       Mini
/dev/sda2        7060EA3E60EA0B24                       ntfs       S3A8406D004
/dev/sda4        8AD8245BD82447B1                       ntfs       HDDRECOVERY
/dev/sda5        93f00b46-2cf5-4b46-83be-f708cf831675   ext4       10.10
/dev/sda6        0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1   ext4       home
/dev/sda7        63d86782-bff4-41c1-924f-37d093fbe371   swap       
/dev/sda8        7343d254-e594-4593-8258-3ecebdb376ef   ext4       12.04
/dev/sda9        6B8E2F2A62CEE191                       ntfs       Misc
/dev/sdb1        26e4f38f-0e49-460a-9c7d-62db2c391ea3   ext4       
/dev/sdb5        6f9c6a63-ee83-4b6c-88d1-dd33d23b4f8e   ext4       Stuff

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec 14 01:30 ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W -> ../../sdb
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-Samsung_SSD_850_EVO_120GB_S21SNXAG908523W-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Dec 14 01:30 ata-TOSHIBA_MK3263GSX_20B3FD6US-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Dec 14 01:30 wwn-0x500003925688264a -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Dec 14 01:30 wwn-0x500003925688264a-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Dec 14 01:30 wwn-0x500003925688264a-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x500003925688264a-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Dec 14 01:30 wwn-0x5002538d405b5ecf -> ../../sdb
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x5002538d405b5ecf-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x5002538d405b5ecf-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Dec 14 01:30 wwn-0x5002538d405b5ecf-part5 -> ../../sdb5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /mnt/storage             ext4       (rw,errors=remount-ro)
/dev/sdb1        /                        ext4       (rw,noatime,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Xubuntu 12.04 Linux 3.2.0-57-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Ubuntu, with Linux 3.2.0-57-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Raring 3.9.0-030900-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7060EA3E60EA0B24
	chainloader +1
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt  quiet splash acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	echo	'Loading Linux 2.6.38-020638-generic ...'
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
### END /etc/grub.d/20_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_linux_xen ###
### END /etc/grub.d/30_linux_xen ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=93f00b46-2cf5-4b46-83be-f708cf831675	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/home	ext4	defaults	0	2
#Entry for /dev/sda4 :
#UUID=8AD8245BD82447B1	/media/HDDRECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda11 :
UUID=6B8E2F2A62CEE191	/media/Misc	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda2 :
#UUID=7060EA3E60EA0B24	/media/S3A8406D004	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda1 :
#UUID=3E10BBBF10BB7C89	/media/System	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  46.543743134 = 49.975963648   boot/grub/grub.cfg                             2
  49.780414581 = 53.451313152   boot/grub/core.img                             1
  50.543025970 = 54.270160896   boot/vmlinuz-2.6.35.11dazimage                 1
  50.316539764 = 54.026973184   boot/vmlinuz-2.6.35-25-generic                 1
  50.374862671 = 54.089596928   boot/vmlinuz-2.6.35-27-generic                 1
  47.368469238 = 50.861506560   boot/vmlinuz-2.6.35-28-generic                 2
  51.154415131 = 54.926635008   boot/vmlinuz-2.6.35-30-generic                 1
  50.745323181 = 54.487375872   boot/vmlinuz-2.6.35-31-generic                 1
  50.756816864 = 54.499717120   boot/vmlinuz-2.6.35-32-generic                 1
  50.097896576 = 53.792206848   boot/vmlinuz-2.6.37-020637-generic             1
  50.727294922 = 54.468018176   boot/vmlinuz-2.6.38-020638-generic             1
  50.255943298 = 53.961908224   boot/vmlinuz-2.6.38-020638rc2-generic          1
  50.756816864 = 54.499717120   vmlinuz                                        1
  50.745323181 = 54.487375872   vmlinuz.old                                    1
  50.606262207 = 54.338060288   boot/initrd.img-2.6.35.11dazimage              1
  46.972850800 = 50.436714496   boot/initrd.img-2.6.35-25-generic              2
  47.003459930 = 50.469580800   boot/initrd.img-2.6.35-27-generic              2
  45.180061340 = 48.511721472   boot/initrd.img-2.6.35-28-generic              2
  52.374996185 = 56.237223936   boot/initrd.img-2.6.35-30-generic              2
  48.640621185 = 52.227469312   boot/initrd.img-2.6.35-31-generic              2
  50.796871185 = 54.542725120   boot/initrd.img-2.6.35-32-generic              2
  46.917037964 = 50.376785920   boot/initrd.img-2.6.37-020637-generic          2
  45.242183685 = 48.578424832   boot/initrd.img-2.6.38-020638-generic          3
  45.262779236 = 48.600539136   boot/initrd.img-2.6.38-020638rc2-generic       2
  50.796871185 = 54.542725120   initrd.img                                     2
  48.640621185 = 52.227469312   initrd.img.old                                 2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1
insmod jpeg
if background_image /binky/Pictures/FromHPLappy/PICS/NRiversRiverhalf.jpg; then
  set color_normal=black/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-85-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-64-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-61-generic
}
menuentry "Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-61-generic
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/31_linux_proxy ###
menuentry "Ubuntu, with Linux 3.2.0-59-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.2.0-59-generic ...'
	linux	/boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.2.0-58-generic ...'
	linux	/boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-58-generic
}
submenu "Previous Linux versions"{
menuentry "Ubuntu 10.10 Linux 2.6.38-020638-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Raring 3.9.0-030900-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux	/boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	echo	'Loading Linux 3.9.0-030900-generic ...'
	linux	/boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.9.0-030900-generic
}
}
### END /etc/grub.d/31_linux_proxy ###

### BEGIN /etc/grub.d/33_linux_xen ###
### END /etc/grub.d/33_linux_xen ###

### BEGIN /etc/grub.d/35_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/35_memtest86+ ###

### BEGIN /etc/grub.d/36_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/36_os-prober_proxy ###

### BEGIN /etc/grub.d/37_uefi-firmware ###
### END /etc/grub.d/37_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda8 :
UUID=7343d254-e594-4593-8258-3ecebdb376ef	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda10 :
UUID=6B8E2F2A62CEE191	/media/Misc	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/media/home	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0

# XPVbox /dev/sda10
# UUID=dbfd8a62-2d43-4a16-aa6c-f926004553e0       /media/XPVbox       ext4    errors=remount-ro       0       1

--------------------------------------------------------------------------------

====================== sda8/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  68.904485703 = 73.985628160   boot/grub/grub.cfg                             3
  62.404806137 = 67.006650368   boot/vmlinuz-3.2.0-58-generic                  3
  56.607080460 = 60.781389824   boot/vmlinuz-3.2.0-59-generic                 22
  58.299528122 = 62.598641664   boot/vmlinuz-3.2.0-85-generic                  5
  66.916036606 = 71.850547200   boot/vmlinuz-3.9.0-030900-generic              2
  56.607080460 = 60.781389824   vmlinuz                                       22
  62.404806137 = 67.006650368   vmlinuz.old                                    3
  61.224981308 = 65.739823104   boot/initrd.img-3.2.0-58-generic               2
  57.039354324 = 61.245540352   boot/initrd.img-3.2.0-59-generic              18
  64.680101395 = 69.449730048   boot/initrd.img-3.9.0-030900-generic          16

================= sda8: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  55.568258286 = 59.665963008   boot/extlinux/extlinux.conf                    1
  57.178606033 = 61.395060736   boot/extlinux/chain.c32                        1

============== sda8: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================== sda10/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos10'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
else
  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E10BBBF10BB7C89' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E10BBBF10BB7C89
	else
	  search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos11'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	else
	  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	fi
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' $menuentry_id_option 'osprober-gnulinux-advanced-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-61-generic
	}
}

menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-7060EA3E60EA0B24' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  7060EA3E60EA0B24
	else
	  search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8AD8245BD82447B1' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  8AD8245BD82447B1
	else
	  search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Ubuntu 10.10 (10.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-93f00b46-2cf5-4b46-83be-f708cf831675' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
	else
	  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	fi
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
submenu 'Advanced options for Ubuntu 10.10 (10.10) (on /dev/sda5)' $menuentry_id_option 'osprober-gnulinux-advanced-93f00b46-2cf5-4b46-83be-f708cf831675' {
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic--93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic-root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt-93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7343d254-e594-4593-8258-3ecebdb376ef' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
	else
	  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	fi
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' $menuentry_id_option 'osprober-gnulinux-advanced-7343d254-e594-4593-8258-3ecebdb376ef' {
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
}

menuentry 'Ubuntu 14.04.3 LTS (14.04) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu 14.04.3 LTS (14.04) (on /dev/sdb1)' $menuentry_id_option 'osprober-gnulinux-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	menuentry 'Ubuntu (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic--26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic-root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-generic
	}
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

menuentry "SSD (on hd1)" {
        insmod part_msdos
        insmod part_gpt
        insmod ext2
        set root='(hd1,msdos0)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.save ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "SSD (on hd1)" {
        insmod part_msdos
        insmod part_gpt
        insmod ext4
        set root='(hd1,0)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/40_custom.save ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda10 :
UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 / ext4 errors=remount-ro 0 1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/mnt/storage	ext4	errors=remount-ro	0	1
#Entry for /dev/sda9 :
UUID=6B8E2F2A62CEE191	/mnt/Misc	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda12 :
#UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32	/mnt/mini12.04	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0

#sdb1
#UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93       /       ext4    errors=remount-ro       0       1


#Entry for /dev/sdc1 :
#UUID=F0C48990C4895A2C	/mnt/2013BUP1	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sdb2 BUP2 external
#UUID=303f7548-cb7b-426d-80a1-a2e650aba95b	/mnt/BUP2	ext4	errors=remount-ro	0	1


/dev/disk/by-uuid/51b8d826-c245-46da-bd64-42234c80a02c / auto errors=remount-ro 0 0
/dev/disk/by-uuid/1fd9a713-1d62-4084-a2b3-972989d5da9d / ext4 errors=remount-ro,noauto 0 0
--------------------------------------------------------------------------------

====================== sda10/boot/extlinux/extlinux.conf: ======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

  74.851028442 = 80.370679808   boot/grub/grub.cfg                             2
  73.771133423 = 79.211151360   boot/grub/i386-pc/core.img                     1
  85.231006622 = 91.516096512   boot/vmlinuz-3.13.0-70-generic                 1
  84.668506622 = 90.912116736   boot/vmlinuz-3.13.0-70-lowlatency              2
  81.879444122 = 87.917383680   boot/vmlinuz-3.13.0-71-generic                 2
  82.160694122 = 88.219373568   boot/vmlinuz-3.13.0-71-lowlatency              1
  82.160694122 = 88.219373568   vmlinuz                                        1
  81.879444122 = 87.917383680   vmlinuz.old                                    2
  85.501422882 = 91.806453760   boot/initrd.img-3.13.0-70-generic              2
  85.450992584 = 91.752304640   boot/initrd.img-3.13.0-70-lowlatency           3
  83.688499451 = 89.859842048   boot/initrd.img-3.13.0-71-generic              3
  82.238761902 = 88.303198208   boot/initrd.img-3.13.0-71-lowlatency           3
  82.238761902 = 88.303198208   initrd.img                                     3
  83.688499451 = 89.859842048   initrd.img.old                                 3

================= sda10: Location of files loaded by Syslinux: =================

           GiB - GB             File                                 Fragment(s)

  80.300552368 = 86.222061568   boot/extlinux/extlinux.conf                    1
  73.430919647 = 78.845849600   boot/extlinux/chain.c32                        1

============== sda10: Version of COM32(R) files used by Syslinux: ==============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================== sda11/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos12)'
  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-85-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-85-generic ...'
	linux	/boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-85-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-64-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-64-generic ...'
	linux	/boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-61-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	echo	'Loading Linux 3.2.0-61-generic ...'
	linux	/boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-61-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	chainloader +1
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-54-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-54-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-53-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-53-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-53-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-44-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-44-generic
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Ubuntu, with Linux 3.13.0-6-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-6-lowlatency-recovery-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	linux /boot/vmlinuz-3.13.0-6-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
	initrd /boot/initrd.img-3.13.0-6-lowlatency
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-59-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-58-generic
}
menuentry "Xubuntu 12.04 Linux 3.2.0-57-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Ubuntu, with Linux 3.2.0-57-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.2.0-57-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-57-generic
}
menuentry "Raring 3.9.0-030900-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.9.0-030900-generic
}
menuentry "Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
	initrd /boot/initrd.img-3.9.0-030900-generic
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda12 :
UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
#UUID=8AD8245BD82447B1	/media/HDDRECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
# UUID=7060EA3E60EA0B24	/media/S3A8406D004	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
# UUID=3E10BBBF10BB7C89	/media/System	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda8 :
UUID=7343d254-e594-4593-8258-3ecebdb376ef	/mnt/12.04	ext4	errors=remount-ro	0	1
#Entry for /dev/sda9 :
UUID=6B8E2F2A62CEE191	/mnt/Misc	ntfs    defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/mnt/storage	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0
--------------------------------------------------------------------------------

====================== sda11/boot/extlinux/extlinux.conf: ======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 254.304267883 = 273.057128448  boot/grub/grub.cfg                             2
 255.112022400 = 273.924448256  boot/vmlinuz-3.2.0-61-generic                  4
 244.421382904 = 262.445461504  boot/vmlinuz-3.2.0-64-generic                  4
 251.816402435 = 270.385803264  boot/vmlinuz-3.2.0-85-generic                  2
 251.816402435 = 270.385803264  vmlinuz                                        2
 244.421382904 = 262.445461504  vmlinuz.old                                    4
 255.288410187 = 274.113843200  boot/initrd.img-3.2.0-61-generic              17
 253.218257904 = 271.891034112  boot/initrd.img-3.2.0-64-generic              12
 255.444755554 = 274.281717760  boot/initrd.img-3.2.0-85-generic              13

================= sda11: Location of files loaded by Syslinux: =================

           GiB - GB             File                                 Fragment(s)

 254.004848480 = 272.735629312  boot/extlinux/extlinux.conf                    1
 252.174434662 = 270.770237440  boot/extlinux/chain.c32                        1

============== sda11: Version of COM32(R) files used by Syslinux: ==============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
else
  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-71-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-generic-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-71-generic ...'
		linux	/boot/vmlinuz-3.13.0-71-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-lowlatency ...'
		linux	/boot/vmlinuz-3.13.0-70-lowlatency root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-advanced-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro  splash quiet $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-generic-recovery-26e4f38f-0e49-460a-9c7d-62db2c391ea3' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
		else
		  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
		fi
		echo	'Loading Linux 3.13.0-70-generic ...'
		linux	/boot/vmlinuz-3.13.0-70-generic root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-70-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26e4f38f-0e49-460a-9c7d-62db2c391ea3
	else
	  search --no-floppy --fs-uuid --set=root 26e4f38f-0e49-460a-9c7d-62db2c391ea3
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3E10BBBF10BB7C89' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3E10BBBF10BB7C89
	else
	  search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Ubuntu 14.04.3 LTS (14.04) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	else
	  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
	fi
	linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.13.0-71-lowlatency
}
submenu 'Advanced options for Ubuntu 14.04.3 LTS (14.04) (on /dev/sda10)' $menuentry_id_option 'osprober-gnulinux-advanced-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
	menuentry 'Ubuntu (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-lowlatency-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-71-generic-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-71-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-71-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-lowlatency-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-lowlatency
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic--40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.13.0-70-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-70-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-70-generic-root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset-40c1d59b-20a7-4096-8cc4-fd65e0a1fb93' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		else
		  search --no-floppy --fs-uuid --set=root 40c1d59b-20a7-4096-8cc4-fd65e0a1fb93
		fi
		linux /boot/vmlinuz-3.13.0-70-generic root=UUID=40c1d59b-20a7-4096-8cc4-fd65e0a1fb93 ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-70-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos11'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	else
	  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
	fi
	linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.2.0-85-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda11)' $menuentry_id_option 'osprober-gnulinux-advanced-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-85-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-85-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-64-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-64-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-64-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic--865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro splash quiet $vt_handoff
		initrd /boot/initrd.img-3.2.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-61-generic-root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset-865e6caa-b7bf-49b5-8d41-bf7e8d03be32' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		else
		  search --no-floppy --fs-uuid --set=root 865e6caa-b7bf-49b5-8d41-bf7e8d03be32
		fi
		linux /boot/vmlinuz-3.2.0-61-generic root=UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-61-generic
	}
}

menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-7060EA3E60EA0B24' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  7060EA3E60EA0B24
	else
	  search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8AD8245BD82447B1' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  8AD8245BD82447B1
	else
	  search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Ubuntu 10.10 (10.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-93f00b46-2cf5-4b46-83be-f708cf831675' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
	else
	  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	fi
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
submenu 'Advanced options for Ubuntu 10.10 (10.10) (on /dev/sda5)' $menuentry_id_option 'osprober-gnulinux-advanced-93f00b46-2cf5-4b46-83be-f708cf831675' {
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic--93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
	menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-020638-generic-root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt-93f00b46-2cf5-4b46-83be-f708cf831675' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  93f00b46-2cf5-4b46-83be-f708cf831675
		else
		  search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
		fi
		linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
		initrd /boot/initrd.img-2.6.38-020638-generic
	}
}

menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7343d254-e594-4593-8258-3ecebdb376ef' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
	else
	  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
	fi
	linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-59-generic
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/sda8)' $menuentry_id_option 'osprober-gnulinux-advanced-7343d254-e594-4593-8258-3ecebdb376ef' {
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-59-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-59-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-59-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-58-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.2.0-58-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-58-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic--7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
	menuentry 'Raring 3.9.0-030900-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.9.0-030900-generic-root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset-7343d254-e594-4593-8258-3ecebdb376ef' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  7343d254-e594-4593-8258-3ecebdb376ef
		else
		  search --no-floppy --fs-uuid --set=root 7343d254-e594-4593-8258-3ecebdb376ef
		fi
		linux /boot/vmlinuz-3.9.0-030900-generic root=UUID=7343d254-e594-4593-8258-3ecebdb376ef ro recovery nomodeset
		initrd /boot/initrd.img-3.9.0-030900-generic
	}
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
## /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdb1 :
UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 / ext4 noatime,errors=remount-ro 0 1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1       /mnt/storage    ext4    errors=remount-ro       0       1
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371       none    swap    sw      0       0

#Entry for /dev/sdb5
#UUID=6f9c6a63-ee83-4b6c-88d1-dd33d23b4f8e
--------------------------------------------------------------------------------

====================== sdb1/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.413486481 = 13.328879616   boot/grub/grub.cfg                             2
  12.409801483 = 13.324922880   boot/grub/i386-pc/core.img                     1
  12.149517059 = 13.045444608   boot/vmlinuz-3.13.0-70-generic                 1
  12.154941559 = 13.051269120   boot/vmlinuz-3.13.0-70-lowlatency              1
  12.193897247 = 13.093097472   boot/vmlinuz-3.13.0-71-generic                 1
  12.199321747 = 13.098921984   boot/vmlinuz-3.13.0-71-lowlatency              1
  12.199321747 = 13.098921984   vmlinuz                                        1
  12.193897247 = 13.093097472   vmlinuz.old                                    1
   0.149410248 = 0.160428032    boot/initrd.img-3.13.0-70-generic              2
   0.167396545 = 0.179740672    boot/initrd.img-3.13.0-70-lowlatency           1
   0.188472748 = 0.202371072    boot/initrd.img-3.13.0-71-generic              2
   0.204097748 = 0.219148288    boot/initrd.img-3.13.0-71-lowlatency           2
   0.204097748 = 0.219148288    initrd.img                                     2
   0.188472748 = 0.202371072    initrd.img.old                                 2

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  12.199325562 = 13.098926080   boot/extlinux/extlinux.conf                    1
  12.154964447 = 13.051293696   boot/extlinux/chain.c32                        1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

hexdump: u: bad byte count
./bootinfoscript: line 1756: [: -eq: unary operator expected


```

I know nothing about this part:

 ```
 modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
```

More info. I changed my chainloader entry to:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "SSD on sdb1" {
    set root=(hd1,0)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
```

... and there is some progress.

The entries I had at boot are still there, one amongst the kernels with 'Ubuntu Linux 14.04 ... (sdb1)' as per usual, then I have the two entries added at the end, which were 'SSD' but I have changed (via 40_custom) to 'SSD on sdb1'. No idea why I have two, but have changed it in 40_custom.save also, so perhaps that's a problem.

Now, rather than an error from the 'SSD on sdb1' entries, all three entries for sdb1 go to a blank screen as if it's going to boot, then loop back to the grub kernel list again.

---

### Post by oldfred on 2015-12-13
Grub2's partitions start at one, there is no more 0 (zero) as in grub legacy. But drives still start at 0, just to keep us confused.

set root=(hd1,1)

I have not seen the modules list either. Off to download another copy of bootinfoscript. I did not think the user with the fork was really maintaining it?

---

### Post by Bucky Ball on 2015-12-13
This is what I have now:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "SSD on sdb1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
```

No change. All three entries loop me back to the grub list to choose a kernel. Still no errors though, so that is promising I guess ...

Wondering if I need to add more info to 40_custom.

PS: I also tried 'hd1,msdos1'. No diff. :-k

Also, I could boot from the optical drive when there was one there. It won't boot from the hard drive caddy, though, if I set that first in BIOS in the boot order (CD/DVD option). If I select 'CD/DVD' from the F12 boot device options, though, it boots to the SSD menu, choose the 'Ubuntu Linux on ... (sdb1)' (NOT the 'SSD on sdb1' options) it boots directly to the SSD drive without issue (although the hard drive still seems to be rather warm).

---

### Post by oldfred on 2015-12-13
I have seen others that just could not boot caddy directly. Glad to hear that booting CD/DVD entry with one time key works, although CD boots are usually different than drive boots.

You could try using UUID. Some one posted this, have not used it.

```
 menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}


```

---

### Post by Bucky Ball on 2015-12-14
* Hold on!!! Got the syntax wrong. Will edit and report back. 
___

Thanks oldfred.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "SSD on sdb1" {
    set root=UUID-26e4f38f-0e49-460a-9c7d-62db2c391ea3
        linux /vmlinuz root=UUID-26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro quiet splash
        initrd /initrd.img
}
```

No change. 

Yes, odd, but this machine has always ignored whatever is set as first boot device in the BIOS and booted from the hard drive unless I hit F12 and choose a one time boot device. 

Might take a break, go for a bike ride in the 35C heat to the gym in the park and do chin-ups til I fall over instead of going mad. I figured this would take me an hour or two ... last Friday afternoon. It is currently Monday afternoon here! :| :D

Still, all the more satisfying when it works ... if ...

One question, though. If I choose the one time boot from F12 and boot to the SSD install (it flashes a white cursor for about 10 seconds then proceeds as normal) is this in any way detrimental to the machine or its operation? The hard drive still seems to spin up and stay up although I know for sure it is the SSD install.

If not, I guess I could accept that as a resolution rather than a solution to the current issue: How to boot sdb install from grub of sda ... :-k

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "SSD on sdb1" {
    set root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3
        linux /vmlinuz root=UUID=26e4f38f-0e49-460a-9c7d-62db2c391ea3 ro quiet splash
        initrd /initrd.img
}
```

No change from using any of the three menu entries at boot. Back to list.

---

### Post by sudodus on 2015-12-14
Maybe you should separate your task into two tasks.

1 - make the computer boot into the drive in the second drive bay

2 - put your favourite system into the second drive bay and make it bootable there

The first task could be made easy by installing a very standard and portable system, for example a live or persistent live or a basic installed xubuntu system into your SSD, and check that it works in some place in some computer. Then find out how to boot into it when in the second drive bay in this stubborn computer.

---

### Post by Bucky Ball on 2015-12-14
[QUOTE=Bucky Ball]One question, though. If I choose the one time boot from F12 and boot to the SSD install (it flashes a white cursor for about 10 seconds then proceeds as normal) is this in any way detrimental to the machine or its operation? ... I guess I could accept that as a resolution rather than a solution to the current issue: How to boot sdb install from grub of sda ... [/QUOTE]

@sudodus: If I hit F12 and choose the FDD entry it takes me to the grub list of kernels. If I then choose the 'Ubuntu Linux 14.04 etc. ... (sdb1)' it boots me into the SSD install without issue. So I have a dupicate install that I know works where it is. :D 

Posting from the SSD install now. Been able to boot to it for quite some time, just have to select FDD to do it. But the SSD install itself, when I get there, works faultlessly (and the machine is slightly cooler as well). :)

* Something else of interest. The result of 'update-grub' in the SSD (sdb1) install:

```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-71-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-71-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-70-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-70-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-70-generic
Found initrd image: /boot/initrd.img-3.13.0-70-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda10
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda11
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
Found Ubuntu 10.10 (10.10) on /dev/sda5
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda8
done

```

Finds all the installs on sda but doesn't find itself. But when I upgrade from sda install it finds sdb1. Shouldn't there be a line which reads, as there is when I update grub on sda:

```
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sdb1
```

---

### Post by sudodus on 2015-12-14
> **Bucky Ball said:**
> [QUOTE=Bucky Ball]One question, though. If I choose the one time boot from F12 and boot to the SSD install (it flashes a white cursor for about 10 seconds then proceeds as normal) is this in any way detrimental to the machine or its operation? ... I guess I could accept that as a resolution rather than a solution to the current issue: How to boot sdb install from grub of sda ... 

@sudodus: If I hit F12 and choose the FDD entry it takes me to the grub list of kernels. If I then choose the 'Ubuntu Linux 14.04 etc. ... (sdb1)' it boots me into the SSD install without issue. So I have a dupicate install that I know works where it is. :D 

Posting from the SSD install now. Been able to boot to it for quite some time, just have to select FDD to do it. But the SSD install itself, when I get there, works faultlessly (and the machine is slightly cooler as well). :)[/QUOTE]

I don't know how it could be detrimental. What is it doing during those 10 seconds? Reading furiously back and forth on a HDD? I guess it is not testing graphic modes furiously at such an early stage.

Maybe it is trying to boot from the floppy (if FDD means floppy disk drive). I think it should be OK. Maybe you could make it shorter or skip it with some boot option.

> **Bucky Ball said:**
> @sudodus: If I hit F12 and choose the FDD entry it takes me to the grub list of kernels. If I then choose the 'Ubuntu Linux 14.04 etc. ... (sdb1)' it boots me into the SSD install without issue. So I have a dupicate install that I know works where it is. :D 

Posting from the SSD install now. Been able to boot to it for quite some time, just have to select FDD to do it. But the SSD install itself, when I get there, works faultlessly (and the machine is slightly cooler as well). :)

* Something else of interest. The result of 'update-grub' in the SSD (sdb1) install:

```
Generating grub configuration file ...
[COLOR="#FF0000"]Found linux image: /boot/vmlinuz-3.13.0-71-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-71-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-70-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-70-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-70-generic
Found initrd image: /boot/initrd.img-3.13.0-70-generic
[/COLOR]Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda10
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda11
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
Found Ubuntu 10.10 (10.10) on /dev/sda5
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sda8
done

```

Finds all the installs on sda but doesn't find itself. But when I upgrade from sda install it finds sdb1. Shouldn't there be a line which reads, as there is when I update grub on sda:

```
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sdb1
```

What about the [COLOR="#FF0000"]red[/COLOR] lines? Are they pointing to the own system?

---

### Post by Bucky Ball on 2015-12-14
> **sudodus said:**
> What about the [COLOR="#FF0000"]red[/COLOR] lines? Are they pointing to the own system?

Doh. Guess so. When I choose 'FDD' it boots directly to the login screen of the SSD install so never get to see it's own grub menu list of kernels and OSs. 

Well, how to boot my sdb SSD from sda is not solved, but I can boot the SSD install by pressing F12 at boot and selecting 'FDD' and all is good, so I'm marking this as solved, but in reality 'resolved' to my satisfaction. 

Feel free, though, if anyone has anything come to mind and thanks much all for the input. :)

---

### Post by oldfred on 2015-12-14
When booting I get the underscore in upper left corner. But with SSD it is very short, its only when I boot HDD that I see it for a noticeable time.
If I remove quiet splash then it is just the normal boot process. You can do the at grub menu with the e before selecting which kernel or system to boot.

---

### Post by Bucky Ball on 2015-12-14
Will give that a whirl next time I reboot. Happily grinding away on the SSD install at the moment and trying to catch up on what I should have been doing instead of tweaking with this! :) 

Quieter, slightly cooler, faster. The hard drive was getting very hot and is five years old so had to be done sooner or later. Better sooner. 

Thanks again, oldfred.

---

### Post by Bucky Ball on 2015-12-15
Reply to your suggestion oldfred. I don't see the cursor at all on the HDD install boot, only a delay on the SSD boot with the cursor. 

So, choose FDD from the F12 device menu, choose sdb1 install from the list and 'e' to edit, remove 'quiet splash' and no, there doesn't seem to be the cursor prior to the text scrolling, which is expected with 'quiet splash' removed. 

I've just edited 'quiet splash' out of /etc/default/grub and updated grub so will reboot and see what happens. Cheers. :)

* Update: Removed 'quiet splash' from /etc/default/grub, update grub, reboot, choose FDD, select sdb1 entry from menu ... exactly the same. Cursor delay for around fives or ten seconds, then boots to SSD fine. So no idea why the cursor's coming up after selecting the kernel. No biggie, but another mystery to go with the misbehaving chainloader.

---

### Post by oldfred on 2015-12-15
If grub before boot starts, do not know.
If part of boot, then you can review boot logs.
       gksudo gedit /var/log/dmesg

Long difference in time stamps are potentially an issue. Or outright errors & warnings.

---

### Post by Bucky Ball on 2015-12-15
Well, nothing drastic, but wonder about the first:

[```
[    0.246517] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.318043] ACPI: SSDT 00000000bf690c18 0003A6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
```

```
[    0.414901] Trying to unpack rootfs image as initramfs...
[    0.791900] Freeing initrd memory: 18856K (ffff880035b1c000 - ffff880036d86000)
[    0.791907] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.791910] software IO TLB [mem 0xbb680000-0xbf680000] (64MB) mapped at [ffff8800bb680000-ffff8800bf67ffff]
[    0.791956] Simple Boot Flag at 0x44 set to 0x1
```

---

### Post by oldfred on 2015-12-15
All the ACPI issue have confused me. But I believe there are many on going issues with ACPI as either it is changing or not well documented.

Some systems need boot parameters for ACPI to boot at all. But I would not make any of these permanent unless it seems to work better. But you have to then edit grub manually and see how system works.

See list by ubfan1:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Or one of these:
      
 # Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

