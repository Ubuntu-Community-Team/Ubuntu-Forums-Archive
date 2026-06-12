---
title: "Neither Ubuntu nor Windows boots"
date: 2014-08-04
forum: General Help
---

### Post by Dan_Harel on 2014-08-04
So this morning my girlfriend decided to install Ubuntu on her laptop. It took her a while due to various installation issues, but she finally got it to install alongside Windows 7 using Wubi. Unfortunately, it was found that she was unable to boot back into Windows. GRUB would give her the option to boot into Ubuntu, but NOT Windows 7.

She tried ```
sudo update-grub
```. Didn't work.

She tried ```
sudo os-prober
```. Windows 7 didn't come up.

She tried the following, but this also didn't work:
```
[FONT=Ubuntu Mono]sudo add-apt-repository ppa:yannubuntu/boot-repair &&sudo apt-get update &&sudo apt-get install -y boot-repair &&[/FONT]
```

Finally she tried the solution at the bottom of this page: [http://ubuntuforums.org/showthread.php?t=1887845](http://ubuntuforums.org/showthread.php?t=1887845)
That also didn't work.
Actually, that made things worse. She now can't even access the normal GUI version of GRUB, only the BASH-like version.

So we took a look at this page here: [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
She got to step 3 -- loading the modules -- but the module "loopback" was not found. She can clearly see it on the list of modules, but the system refuses to acknowledge it when she tries running ```
insmod loopback
```.

Finally, I suggested that she reinstall Ubuntu from the disk she used to install it in the first place. The problem is, she can no longer boot anything from disk for some reason. She made sure that the disk drive is on top of the boot priority list, but the disk never gets read, regardless of what its contents are.

So now she's stuck at a bash-like GRUB screen with no idea how to fix it, and an inability to boot into Ubuntu or Windows.

Any help would be greatly appreciated. Her laptop has essentially been rendered useless until we can at least get her back into Ubuntu. And even then, she still can't find a way onto Windows where all of her files are.

**Edit:** We managed to get it to boot from disk again. However, when she tried running the Ubuntu installation disk, it shows the loading screen for a few seconds, then the screen goes black and nothing happens.

**Edit 2:** We managed to get past the black screen by selecting "NOMODESET" in the options. However, when she selects "Try Ubuntu without installing", it begins to load, but then the graphics become distorted and the screen goes black. She cannot get back into Ubuntu right now.

**Edit 3:** I'm not sure how, but she managed to get past the black screen using the installation disk! We tried some things to get GRUB back to normal, and seem to have purged it with no way to reinstall it... We're now working on trying to find a way into Windows again, and if possible, we'd also like to recover GRUB. But as long as we have a working Linux CD, getting back into Ubuntu is not an issue. Getting into Windows is the priority.

---

### Post by n41076jem-2 on 2014-08-04
how about boot off a thumb drive, mount the disk. Copy off her data.  Then reload windows 7, and try again

---

### Post by Bucky Ball on 2014-08-04
Bad news is that Wubi is no longer supported and there are very few gurus here that might be able to help. But I hope someone pops up with some suggestions. All I can offer is this, sorry:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Wubi does not install 'alongside' Windows, it installs inside, like any other Windows program. A dual-boot (alongside) sounds like it was the intention, but that can not be done from inside Windows.

PS: Booting Ubuntu from a USB stick to attempt a fix is another viable option.

---

### Post by Jesse_Campton on 2014-08-04
Can you turn off the HDD (Disable it completely) in the *bios* so that only the disk drive is bootable and try booting the live CD?

---

### Post by Dan_Harel on 2014-08-04
Wait! I'm not certain that she used Wubi. She says that Wubi is on the disk, but she installed Ubuntu by burning Ubuntu and running the disk. I'm not sure if this means that Wubi was run or not. I'm sorry for our ignorance. We're both very very new to Ubuntu...

---

### Post by QIII on 2014-08-04
Stop using the computer -- you may have installed over Windows.

Don't panic.  We've all done it.

On my cell right now so can't help very well.  But others will.

Just wanted to say stop using the machine so you don't make matters worse.

---

### Post by oldfred on 2014-08-04
What brand & model computer?
And do you know cpu, RAM, & video chip? Model should tell us most of that.

If you can boot live installer, run BootInfo report from Boot-Repair. Do not attempt any fixes until someone reviews report. While auto fix usually works in some cases it can make it worse.

If you get black screen you may have video issues.
Is system newer and UEFI and BIOS? Usually Windows 7 was installed in BIOS Mode, even if hardware was UEFI capabile. And different boot options may be required.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Dan_Harel on 2014-08-04
Lenovo Y580

She managed to get past the black screen using NOMODESET. But when she picks "Try Ubuntu without installing", the screen graphics get distorted then goes black. She has no way of getting back into Ubuntu.

---

### Post by yancek on 2014-08-04
To get some detailed information on the install, whether it is wubi or not as well as detailed information on drives/partitions and boot files, use the Boot Info report from Boot Repair if you have that or just go to the site below and download and run the script, post the output which is a results.txt file.  Instructions are in a link in the Description box and it can be run from the Live medium booted to the desktop, that is if the internet connection works.  Post the results.txt file here.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by whitesmith on 2014-08-04
Check out this PCWorld review of Parted Magic. The developers say this of the product: "Edit and create partitions, copy files off, test your memory and more with this free Linux-based partitioning utility/boot disc." All true, except that recently a small copying fee of $5 is charged to  download the .iso. I was having a serious problem with a hard drive several days ago and Parted Magic resurrected it. It certainly can't do any harm because your system seems totally borked, so $5 buys you a chance to spin the wheel and see if Parted Magic helps you as much as it did me. I offer this with a modicum of sarcasm and a mountain of sincerity: Next time tell your (cough) girlfriend to back up her system before installing a new OS. Regards.

---

### Post by Dan_Harel on 2014-08-04
yancek, you mentioned "the site below", but you didn't post a link. Was this an error?

---

### Post by oldfred on 2014-08-04
Pretty sure yancek was refering to Boot-Repair which I posted link to in post #7.

It looks like Lenovo 580 has dual video. So nomodeset will be correct if booting with nVidia chip in use, but most boot with Intel and other boot parameters needed with Intel video. LInk avbove also has other boot parameters( Post by ubfan1).

Similar models of Lenovo. Even if not exactly the same the UEFI is usually very simuliar. Some difference if AMD or Intel.

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System™ – for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

### Post by yancek on 2014-08-05
> yancek, you mentioned "the site below", but you didn't post a link. Was this an error? 		

Yes, and not my first.  Added the link in the previous post.  From what I have seen, the Boot Repair contains the bootinfoscript plus more, the ability to repair, etc.  The bootinfoscript just gives information and I usually recommend it so that people arent' tempted by options in the Boot Repair they don't understand and end up making things worse but they're both good sources.

---

### Post by SeijiSensei on 2014-08-05
My daughter's Lenovo comes with a physical switch that enables you to select which graphics adapter to use.  If your machine has one of these, make sure it is set to use the Intel adapter during installation.  You can deal with the NVIDIA adapter after you get up and running.

---

### Post by stalkingwolf on 2014-08-05
My first step would be to boot gparted either disc or usb and see if the windows partition is still there or if it was over written.  The answer to that question will give direction to the next step.

---

### Post by Dan_Harel on 2014-08-05
> **stalkingwolf said:**
> My first step would be to boot gparted either disc or usb and see if the windows partition is still there or if it was over written.  The answer to that question will give direction to the next step.

So we just woke up, but we tried some things last night. One of which involved looking on Diskpart.exe from the Windows repair disk. Our original plan was to use the disk to restore the system, but apparently the disk is too small now, despite the fact that it was the same disk she used to make the Windows backup image in the first place. Whatever. Not the point. The point is, when using Diskpart, she was able to  examine the disks and information on these disks. One of the things it said was that Windows is on drive C:, just like it should've. Is this enough information? Or should we proceed with GParted anyway?

Also, I apologize to anyone I may have confused last night. We were both incredibly stressed out by the idea that the laptop may be unrepairable. I think last night's rest was very helpful, and I'm now ready to properly provide anyone with the necessary information to continue.

Also, to anyone else reading this, would it be better for us to run Boot Info Script first, or Boot Repair completely? I am aware of what yancek has said about making things worse, but from scouring the internet for solutions, many people have suggested that Boot Repair is the best solution. If you guys recommend 
against that as the next step, then we will wait.

I'd also like to thank everyone who has helped so far. It's greatly appreciated.

**Also we made it back into Linux using the installation disk!** Now we're trying to get back into Windows. That's our priority.

---

### Post by Dan_Harel on 2014-08-05
Sorry for double posting, but I felt that this should receive its own post, because of how vastly different this is from the previous post.

She ran Boot Info Script. This is what came up:

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb3 has 
                       40550399 sectors, but according to the info from 
                       fdisk, it has 40963823 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd


sdb4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1    62,533,295    62,533,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624    45,963,263    44,912,640 Data partition (Linux)
/dev/sda3      45,963,264    62,531,583    16,568,320 Swap partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               1,979 1,268,127,743 1,268,125,765  12 Compaq diagnostics
/dev/sdb2       1,372,985,344 1,424,185,343    51,200,000   7 NTFS / exFAT / HPFS
/dev/sdb3       1,424,185,344 1,465,149,167    40,963,824  12 Compaq diagnostics
/dev/sdb4       1,268,129,790 1,372,985,343   104,855,554   5 Extended
/dev/sdb5       1,348,130,816 1,372,985,343    24,854,528  82 Linux swap / Solaris
/dev/sdb6       1,268,129,792 1,348,130,815    80,001,024  83 Linux




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        C195-A61D                              vfat       
/dev/sda2        3581271c-9a1d-489a-afd6-6c82dd5c35ef   ext4       
/dev/sda3        d772fb2e-2a6e-4162-b18b-0be85df08449   swap       
/dev/sdb2        96703B71703B56E9                       ntfs       LENOVO
/dev/sdb3        D886394E86392E7E                       ntfs       LENOVO_PART
/dev/sdb5        878b602c-4609-4d87-ba4c-3a899b083dfb   swap       
/dev/sdb6        c598d926-5242-484c-b6ac-692573d08e5e   ext4       
/dev/sr0                                                iso9660    Ubuntu 14.04.1 LTS amd64


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=C195-A61D  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=d772fb2e-2a6e-4162-b18b-0be85df08449 none            swap    sw              0       0
UUID=C195-A61D	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=========================== sdb6/boot/grub/grub.cfg: ===========================


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
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  c598d926-5242-484c-b6ac-692573d08e5e
else
  search --no-floppy --fs-uuid --set=root c598d926-5242-484c-b6ac-692573d08e5e
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
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c598d926-5242-484c-b6ac-692573d08e5e' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  c598d926-5242-484c-b6ac-692573d08e5e
	else
	  search --no-floppy --fs-uuid --set=root c598d926-5242-484c-b6ac-692573d08e5e
	fi
	linux	/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=c598d926-5242-484c-b6ac-692573d08e5e ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c598d926-5242-484c-b6ac-692573d08e5e' {
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-c598d926-5242-484c-b6ac-692573d08e5e' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  c598d926-5242-484c-b6ac-692573d08e5e
		else
		  search --no-floppy --fs-uuid --set=root c598d926-5242-484c-b6ac-692573d08e5e
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=c598d926-5242-484c-b6ac-692573d08e5e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-c598d926-5242-484c-b6ac-692573d08e5e' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  c598d926-5242-484c-b6ac-692573d08e5e
		else
		  search --no-floppy --fs-uuid --set=root c598d926-5242-484c-b6ac-692573d08e5e
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=c598d926-5242-484c-b6ac-692573d08e5e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 14.04.1 LTS (14.04) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-3581271c-9a1d-489a-afd6-6c82dd5c35ef' {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  3581271c-9a1d-489a-afd6-6c82dd5c35ef
	else
	  search --no-floppy --fs-uuid --set=root 3581271c-9a1d-489a-afd6-6c82dd5c35ef
	fi
	linux /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu 14.04.1 LTS (14.04) (on /dev/sda2)' $menuentry_id_option 'osprober-gnulinux-advanced-3581271c-9a1d-489a-afd6-6c82dd5c35ef' {
	menuentry 'Ubuntu (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-32-generic.efi.signed--3581271c-9a1d-489a-afd6-6c82dd5c35ef' {
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  3581271c-9a1d-489a-afd6-6c82dd5c35ef
		else
		  search --no-floppy --fs-uuid --set=root 3581271c-9a1d-489a-afd6-6c82dd5c35ef
		fi
		linux /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-32-generic.efi.signed--3581271c-9a1d-489a-afd6-6c82dd5c35ef' {
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  3581271c-9a1d-489a-afd6-6c82dd5c35ef
		else
		  search --no-floppy --fs-uuid --set=root 3581271c-9a1d-489a-afd6-6c82dd5c35ef
		fi
		linux /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-32-generic.efi.signed-root=UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef ro recovery nomodeset-3581271c-9a1d-489a-afd6-6c82dd5c35ef' {
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  3581271c-9a1d-489a-afd6-6c82dd5c35ef
		else
		  search --no-floppy --fs-uuid --set=root 3581271c-9a1d-489a-afd6-6c82dd5c35ef
		fi
		linux /boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=3581271c-9a1d-489a-afd6-6c82dd5c35ef ro recovery nomodeset
		initrd /boot/initrd.img-3.13.0-32-generic
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


=============================== sdb6/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=c598d926-5242-484c-b6ac-692573d08e5e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=878b602c-4609-4d87-ba4c-3a899b083dfb none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-25zYcVvt/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-25zYcVvt/Tmp_Log: No such file or directory
  No volume groups found



```

Where should we go from here?

---

### Post by yancek on 2014-08-05
> One of the things it said was that Windows is on drive C:, just like it  should've. Is this enough information? Or should we proceed with GParted  anyway?


Then it looks like your windows is still there.  The problem with using the windows tool is that it won't show anything about the Linux/Ubuntu partition as it doesn't recognize Linux filesystems.  I'd boot the Ubuntu DVD, open a terminal by holding down the Ctrl+Alt+t keys simultaneously, then running the following:  sudo fdisk -l(Lower Case Letter L in the command)  This will output drive/partition information which you can post here for help.  It will not change anything on the computer, it's just to get information.  You could also open the terminal and run:  sudo gparted and get the same information from it.

It's your choice about either running the bootfinfoscript or Boot Repair.  I've never had the need to run Boot Repair as I do these things manually.  The bootinfoscript is a bash script which gathers detailed information on drives/partitions, boot files and other pertinent information and does not make any changes.  As far as I can tell from Boot Repair postings I have seen, it runs the same script but also has various options to try to repair. 

> **Also we made it back into Linux using the installation disk!** 

Does the line above mean your are now able to boot Ubuntu on the hard drive?  If so, running sudo update-grub should show a windows entry.  If not, I would then run the bootinfoscript so people who understand can advise you on what needs to be done.

---

### Post by Dan_Harel on 2014-08-05
> **yancek said:**
> Then it looks like your windows is still there.  The problem with using the windows tool is that it won't show anything about the Linux/Ubuntu partition as it doesn't recognize Linux filesystems.  I'd boot the Ubuntu DVD, open a terminal by holding down the Ctrl+Alt+t keys simultaneously, then running the following:  sudo fdisk -l(Lower Case Letter L in the command)  This will output drive/partition information which you can post here for help.  It will not change anything on the computer, it's just to get information.  You could also open the terminal and run:  sudo gparted and get the same information from it.

It's your choice about either running the bootfinfoscript or Boot Repair.  I've never had the need to run Boot Repair as I do these things manually.  The bootinfoscript is a bash script which gathers detailed information on drives/partitions, boot files and other pertinent information and does not make any changes.  As far as I can tell from Boot Repair postings I have seen, it runs the same script but also has various options to try to repair.

This is the result of sudo fdisk -l:

```
[COLOR=#3E454C][FONT=Helvetica]ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    62533295    31266647+  ee  GPT

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc08cff0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1979  1268127743   634062882+  12  Compaq diagnostics
Partition 1 does not start on physical sector boundary.
/dev/sdb2      1372985344  1424185343    25600000    7  HPFS/NTFS/exFAT
/dev/sdb3      1424185344  1465149167    20481912   12  Compaq diagnostics
/dev/sdb4      1268129790  1372985343    52427777    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sdb5      1348130816  1372985343    12427264   82  Linux swap / Solaris
/dev/sdb6      1268129792  1348130815    40000512   83  Linux

Partition table entries are not in disk order[/FONT][/COLOR]
```

> **yancek said:**
> Does the line above mean your are now able to boot Ubuntu on the hard drive?  If so, running sudo update-grub should show a windows entry.  If not, I would then run the bootinfoscript so people who understand can advise you on what needs to be done.

I'm not sure. I know that she ran the Ubuntu installation disk then chose "Try Ubuntu without installing it." I think this is called a "live session"? I'm not sure, but I have heard this term been used in conjuncture with the installation disk.

Also, I posted the results of bootinfoscript in the post above yours.

Thanks for the help! :D

**Edit:**&#8203; This is the result of "sudo update-grub": ```
[COLOR=#3E454C][FONT=Helvetica]/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.[/FONT][/COLOR]
```

---

### Post by oldfred on 2014-08-05
The only place you can have Windows is sdb2 and it shows no Windows boot files. It does say Lenovo as its label. Can you see typical Windows folders & files in that partition?
You show a recovery/diagnostics partition in sdb3 that has just its boot files.

You have what looks like a full UEFI install with gpt partitioning in the sda or 32GB drive.
And a full BIOS install in the sdb drive with MBR(msdos) partitioning.

Fdisk does not work with gpt partitioned drives and gpt has a protective MBR with one entry so fdisk at least warns you that drive is already partitioned.

If you turn UEFI on in UEFI/BIOS can you boot the 32GB drive?
And with a Windows boot loader in the MBR of the 750GB drive, and not Windows boot files that will not work, you should be able to use Boot-Repairs advanced options in BIOS mode to add a grub boot loader to that drive.
But then you have two Ubuntu installs one UEFI and one BIOS??

And we are not sure if sdb2 has any of your original Windows.

---

### Post by Dan_Harel on 2014-08-05
> **oldfred said:**
> The only place you can have Windows is sdb2 and it shows no Windows boot files. It does say Lenovo as its label. Can you see typical Windows folders & files in that partition?
You show a recovery/diagnostics partition in sdb3 that has just its boot files.

You have what looks like a full UEFI install with gpt partitioning in the sda or 32GB drive.
And a full BIOS install in the sdb drive with MBR(msdos) partitioning.

Fdisk does not work with gpt partitioned drives and gpt has a protective MBR with one entry so fdisk at least warns you that drive is already partitioned.

If you turn UEFI on in UEFI/BIOS can you boot the 32GB drive?
And with a Windows boot loader in the MBR of the 750GB drive, and not Windows boot files that will not work, you should be able to use Boot-Repairs advanced options in BIOS mode to add a grub boot loader to that drive.
But then you have two Ubuntu installs one UEFI and one BIOS??

And we are not sure if sdb2 has any of your original Windows.

We don't know how to access any of the files or folders in that partition.

We also don't understand what anything else you posted means. I'm sorry. We're very new to this stuff, and we've only completed only a year of college each. I'm sorry that we can't cooperate in the way that you'd expect us to.

Is there any way you can give us an explicit next step or series of steps to follow in order to give you the information you need, or to fix the problem?

---

### Post by oldfred on 2014-08-05
You have installed twice, once to each drive and once in BIOS boot mode and once in UEFI boot mode.
BIOS is the very old way we have booted computers for years and UEFI is the relatively new replacement for BIOS.
New hardware works either way and installers now will install either way based on how you boot.

From your live installer, go into file brower or Nautilus and click on sdb2 partition. Look and see what is in it. Is it your Windows files & folders?

Installing an operating sytem should not be something you just jump in and do. It does require some review and understanding of computer terms. Example where many get into issues is the Microsoft use of drive like c: drive, d: drive etc. But that is not necessarily a physical drive, it may be two partitions on one hard drive or one partition each on two hard drives. In Linux then sda is one hard drive and sdb a second drive. And sda1 the first partition and sda2 the second partiition.

Lots of details on installing.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using
      [/URL]
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

    [URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]

[/URL]

---

### Post by Dan_Harel on 2014-08-05
> **oldfred said:**
> You have installed twice, once to each drive and once in BIOS boot mode and once in UEFI boot mode.
BIOS is the very old way we have booted computers for years and UEFI is the relatively new replacement for BIOS.
New hardware works either way and installers now will install either way based on how you boot.

From your live installer, go into file brower or Nautilus and click on sdb2 partition. Look and see what is in it. Is it your Windows files & folders?

Installing an operating sytem should not be something you just jump in and do. It does require some review and understanding of computer terms. Example where many get into issues is the Microsoft use of drive like c: drive, d: drive etc. But that is not necessarily a physical drive, it may be two partitions on one hard drive or one partition each on two hard drives. In Linux then sda is one hard drive and sdb a second drive. And sda1 the first partition and sda2 the second partiition.

Lots of details on installing.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using
      [/URL]
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

    [URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]

[/URL]

She looked through sdb2. There are a bunch of Lenovo-specific files, folders, and applications, but it doesn't look like any of her Windows files or folders can be found there. Does this mean Windows has been wiped out? I don't know much about this stuff, but it seems unlikely since bootinfoscript says that there is a Windows partition there. But then again, I don't know much about this stuff....

You help is greatly appreciated, by the way. Thank you so much for taking your time to help us out.

---

### Post by oldfred on 2014-08-05
Did you look in sdb2, not sdb1 or sdb3 which are diagnostic folders.

If sdb2 is not your Windows files then you must have overwritten it.

Did you make good backups before installing Ubuntu?
If not with extreme amounts of work (I have done it) you can recover some data. 

You can try testdisk to see if deeper search shows anything, but probably photorec which just scans drive for anything that looks like a file. Photorec does not recover full filename just extension based on what it thinks file is.

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)


       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)


 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Some also suggest these:

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)

---

### Post by Dan_Harel on 2014-08-05
> **oldfred said:**
> Did you look in sdb2, not sdb1 or sdb3 which are diagnostic folders.

If sdb2 is not your Windows files then you must have overwritten it.

Did you make good backups before installing Ubuntu?
If not with extreme amounts of work (I have done it) you can recover some data. 

You can try testdisk to see if deeper search shows anything, but probably photorec which just scans drive for anything that looks like a file. Photorec does not recover full filename just extension based on what it thinks file is.

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)


       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)


 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Some also suggest these:

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)

Yes, she looked in sdb2. She also checked sbd3, but nothing showed up either.

I don't think we're capable of handling that type of recovery. Although she did make a Windows system backup, and backed up all of her files and documents, so we might try a clean installation of Windows followed by a system restore using said backup.

However, before we proceed, I'd like to ask: is there any change that Boot Repair could rescue us? Are there any specific settings we should try with Boot Repait that may work? Or should we just try the Recommended Settings and hope for the best?

---

### Post by oldfred on 2014-08-05
When you have mulitple drives I do not like to run any auto fix with Boot-Repair as it just installs grub everywhere.
Plus you have one install in UEFI mode that may boot from sda, if you turn on UEFI mode and boot the ubuntu entry.
To boot BIOS entry you could use Boot-Repair booted in BIOS mode and in advanced options choose Ubuntu on sdb and install grub just to sdb. That may boot that Ubuntu in BIOS mode from UEFI/BIOS.

You may have to turn on or off UEFI or BIOS mode in each case to match install.

You need to decide which drive is Ubuntu and which is Windows. 
Is/Was this an Ultrabook and the small drive is a mSata or drive to make Windows boot quicker?

---

### Post by Dan_Harel on 2014-08-05
> **oldfred said:**
> When you have mulitple drives I do not like to run any auto fix with Boot-Repair as it just installs grub everywhere.
Plus you have one install in UEFI mode that may boot from sda, if you turn on UEFI mode and boot the ubuntu entry.
To boot BIOS entry you could use Boot-Repair booted in BIOS mode and in advanced options choose Ubuntu on sdb and install grub just to sdb. That may boot that Ubuntu in BIOS mode from UEFI/BIOS.

You may have to turn on or off UEFI or BIOS mode in each case to match install.

You need to decide which drive is Ubuntu and which is Windows. 
Is/Was this an Ultrabook and the small drive is a mSata or drive to make Windows boot quicker?

It is an Ultrabook, yes. Lenovo Y580. The small drive is an SSD

---

### Post by Dan_Harel on 2014-08-05
My girlfriend couldn't get any solutions to work. She ended up deleting all partitions and reinstalling Windows. She made backups, so she should be able to restore everything with that. 

Thanks for everyone's help. I'm sorry that you've all wasted your efforts. At least we managed to learn some lessons and get a working system.

---

### Post by oldfred on 2014-08-05
That is why good backups are vital.

Is Windows installed in BIOS or UEFI boot mode? If you will try installing Ubuntu again the instructions are different for each mode. And how you boot install media, is how it installs. You would want Ubuntu in the same boot mode as Windows. Lots of UEFI links in the link in my signature.

And we can suggestion many BIOS links if desired.
Some that just want to experiment or try Ubuntu use an external hard drive or even a larger flash drive. If you install to that you can test and learn without modifying working internal drives. But you do have to use Something Else to be able to choose to install grub boot loader to external drive.

This is a flash drive, but could be a hard drive. And does not have to be configured for both.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

