---
title: "Ubuntu  dual boot installation on HP pavilion dv7."
date: 2012-11-13
forum: General Help
---

### Post by InQontroll on 2012-11-13
I installed ubuntu in dualboot with windows7.

[COLOR="Red"]Look at last post.
[/COLOR]
Not sure if I'm in the correct section so sorry if i am!
Using the wubi program.

In first boot to ubuntu anything works perfect.
But as soon as i restart my computer the ubuntu blocks.
At its purple startup screen. It shows nothing.

Only thing i can do then is start windows 7 again reinstall ubuntu in wubi.
Then it runs again but as soon as i restart, it has the same problem.

What can i do about this problem cuz it really gets annoying using ubuntu that way.

Thanks in advance, greetings InQontroll.

---

### Post by bcbc on 2012-11-13
Boot with nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

There are some wubi specific steps in post #8 of that thread for the 'first boot' when installing Wubi - after that see the first post (even though it says not for wubi).

Also, until you install a closed source graphics driver you need to keep overriding with nomodeset. To do this, you need to edit the grub menu and it doesn't show by default on Wubi installs, so press the SHIFT key after selecting Ubuntu (this only applies after the first boot i.e. after installing).

---

### Post by InQontroll on 2012-11-13
> **bcbc said:**
> Boot with nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

There are some wubi specific steps in post #8 of that thread for the 'first boot' when installing Wubi - after that see the first post (even though it says not for wubi).

Also, until you install a closed source graphics driver you need to keep overriding with nomodeset. To do this, you need to edit the grub menu and it doesn't show by default on Wubi installs, so press the SHIFT key after selecting Ubuntu (this only applies after the first boot i.e. after installing).

Thank you vm! I was really waiting on the forums untill someone replied to that! :)
thnx and damn hell linux is way better then windows :o sorry for the curses ;)

---

### Post by InQontroll on 2012-11-14
Well actually it didnt work.
Tried all the things they told me at that thread.

I guess i'm cuiting wubi and about to use a liveusb or cd.

Thing is if i install it using one of those will it be able to save my files then?

---

### Post by bcbc on 2012-11-14
Installling from an Ubuntu USB/CD is different from running a live environment from the USB/CD. When you boot from the Ubuntu USB you can select "Try Ubuntu" (the live environment). In this case there is some option to persist settings and data only with the USB (not the CD), and only if you've created a persistence file.

But if you install from the Ubuntu USB/CD then it will repartition your drive, install the grub bootloader, and then all your changes will be saved.

I should point out that your problems may not be related to Wubi, so installing a normal dual boot, may not work differently. But it's difficult to say for sure since we don't know what your problem is yet.

When you install the first time (with Wubi) how are you doing it? (From cd, standalone wubi.exe etc.)? When it boots the first time do you get to login and use it, run updates, make changes - or does it just complete the install and reboot? Can you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results after installing? Also, post or search on your full machines specs (model, gpu etc.) to see if there are any known issues.

It is better to do a normal dual boot than Wubi (so I'm not suggesting otherwise) - just stating that there might still be problems with the normal dual boot. Also, if you do that, it's a good idea to refresh databackups before hand, and create a windows repair disk - it's not generally required, but I always make sure I have a working repair disk before it's needed.

---

### Post by Mark Phelps on 2012-11-14
Two important points ...

First, if Ubuntu fails to run after a Wubi install, it is unlikely that it will then run after installing in its own partition.  Wubi is only an INSTALLATION METHOD, not a different version of Ubuntu.  What you end up running is the same thing -- whether or not it is its own partition.

Also, the hardware is the same, regardless of the installation method.  IF Ubuntu can't see your video device after a Wubi installation, that will be the same problem after a different installation.

Best approach is to boot from a LiveCD and find out what is needed to get Ubuntu to run on your PC without problems.  Any changes you make for that are going to have to be repeated when you do the install.

Second, do NOT use the Ubuntu installer to shrink down your Win7 setup using the Slider.  That can corrupt the Win7 OS and render it unbootable.

If you really want to press ahead with dual-booting with Win7, then read the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by InQontroll on 2012-11-14
Ubuntu runs smootly when rebooted.
But as soon as i do the second boot it wont even go to login screen It stays stuck at the purple/orange empty screen.

I did this from my windows not from cd.

I will post the bootinfoscript as soon as i have the time to run true this all again.

Full machine specifications:
hp pavilion dv7 notebook.

[img]http://img29.imageshack.us/img29/9161/compdm.png[/img]

Thanks in advance InQontroll.

If you need more info please ask!

---

### Post by InQontroll on 2012-11-14
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   917,229,567   916,819,968   7 NTFS / exFAT / HPFS
/dev/sda3         917,229,568   968,450,047    51,220,480   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,071     8,321,024   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       3cb144dc-ce0f-4105-a1ad-8d33dae4f795   ext4       
/dev/sda1        EA887B6F887B3961                       ntfs       SYSTEM
/dev/sda2        22002ACB002AA62F                       ntfs       
/dev/sda3        F0226DAD226D798C                       ntfs       Recovery
/dev/sda4        7AF8-5F0B                              vfat       HP_TOOLS
/dev/sr0                                                udf        Recovery13

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sr0         /media/inqontroll/Recovery13 udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  22002ACB002AA62F
else
  search --no-floppy --fs-uuid --set=root 22002ACB002AA62F
fi
loopback loop2 /ubuntu/disks/root.disk
set root=(loop2)
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
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3cb144dc-ce0f-4105-a1ad-8d33dae4f795' {
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  22002ACB002AA62F
    else
      search --no-floppy --fs-uuid --set=root 22002ACB002AA62F
    fi
    loopback loop2 /ubuntu/disks/root.disk
    set root=(loop2)
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=22002ACB002AA62F loop=/ubuntu/disks/root.disk ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3cb144dc-ce0f-4105-a1ad-8d33dae4f795' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-3cb144dc-ce0f-4105-a1ad-8d33dae4f795' {
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod ntfs
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  22002ACB002AA62F
        else
          search --no-floppy --fs-uuid --set=root 22002ACB002AA62F
        fi
        loopback loop2 /ubuntu/disks/root.disk
        set root=(loop2)
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=22002ACB002AA62F loop=/ubuntu/disks/root.disk ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-3cb144dc-ce0f-4105-a1ad-8d33dae4f795' {
        insmod gzio
        insmod ntfs
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  22002ACB002AA62F
        else
          search --no-floppy --fs-uuid --set=root 22002ACB002AA62F
        fi
        loopback loop2 /ubuntu/disks/root.disk
        set root=(loop2)
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=22002ACB002AA62F loop=/ubuntu/disks/root.disk ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             2
               =                boot/initrd.img-3.5.0-17-generic               2
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by bcbc on 2012-11-14
Great, can you boot your computer, select Ubuntu and then immediately hold down the left SHIFT key until the grub menu appears.

Then down arrow enter for Advanced options. Then down arrow and enter for Recovery mode. If that boots to the recovery menu, select Resume normal boot.

---

### Post by InQontroll on 2012-11-14
> **bcbc said:**
> Great, can you boot your computer, select Ubuntu and then immediately hold down the left SHIFT key until the grub menu appears.

Then down arrow enter for Advanced options. Then down arrow and enter for Recovery mode. If that boots to the recovery menu, select Resume normal boot.

Wil do after my epic trap song finishes playing xp..

---

### Post by InQontroll on 2012-11-14
when i resumed normal boot:

Crashed.. Well i thought ive gotten it all.
Anyways what happond: my screen started drawing lines evrywhere in the linux colors randomly like a tv that hase the noisy screen..

when i schose the other (not the recovery one) second time.
It started but did not save graphic stuff only the stuff i did before for example visit these forums..

---

### Post by bcbc on 2012-11-14
Okay I'm seeing some issues with the graphics card.

Try this:
Select Ubuntu, hit SHIFT key to pop menu, press 'e' on the first entry to edit:

Delete the line:
gfxmode $linux_gfx_mode

Edit the line starting: linux  /boot/vmlinuz....
Remove: quiet splash $vt_handoff
Add in its place: nomodeset
So it looks like: 
```
linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=22002ACB002AA62F loop=/ubuntu/disks/root.disk ro nomodeset

```Now hit Ctrl+X to boot. Report back.

---

### Post by InQontroll on 2012-11-14
The same screen apeared.
but this time i wasnt abel to start ubuntu anymore.
so i'm back on windows now..

---

### Post by bcbc on 2012-11-14
> **InQontroll said:**
> The same screen apeared.
but this time i wasnt abel to start ubuntu anymore.
so i'm back on windows now..

I can understand it not booting, but it's not normal for it to work sometimes and sometimes not. Are you shutting down normally or doing a hard power off?

---

### Post by InQontroll on 2012-11-14
shutting down normally.
The thing is. when i changed that file it only gives me the noisy screen.

Strange thing is.. In first boot nothings wrong.
but as soon as i reboot in linux i get that noisy screen or i get to login but the graphics disapear.

Its up to what i chose at start. i can only run linux if i select the advanced menu and then select the first option.

but as i said it wont save any graphical stuff..

---

### Post by bcbc on 2012-11-14
mmm I've never encountered something like this. I'll just stand aside and let others help because it's not making a lot of sense to me (either).

---

### Post by InQontroll on 2012-11-15
ouch pff.
hate it when things won't work out!
Oh does it help if i say this is in my comp: quad core and radeon dual graphics?

I also found out about someone else having trouble whit a dual graphics.

```
I have the A6-3400m APU (integrated 6520G, discrete 6470M) and my experience until now is:

The Ubuntu built-in "radeon" driver does NOT support "dual graphics". To get the radeon driver without dual graphics work properly, the discrete graphics card should be switched off in the BIOS (less power consumption, ...)

AMD provides a proprietary driver called "fglrx". This driver can be installed via the system settings "additional drivers" or the latest version directly downloaded from AMD. https://help.ubuntu.com/community/BinaryDriverHowto/ATI My experience: The Ubuntu fglrx version is much toooo old: I had a lot of problems with wine and the activated discrete graphics card because that driver recognised a wrong graphics card (7400m series instead of 64oom series). With the latest AMD driver (Catalyst 12.10): working.

The fglrx drivers for Linux/Ubuntu are provided with a graphical configuration application called Catalyst Control Center and can also be configured via command line via amdconfig. With both configuration tools it is possible to switch between the discrete und the integrated graphics engine. This is called PowerXpress. With Windows this switch can be done without reboot but X needs a restart. Therefore the powersaving feature called PowerPlay does not use PowerXpress under Linux but just other features like dynamic clock rate change, .... BUT: PowerXpress is NOT "dual graphics".

"dual graphics" means: Both graphics engine act like a single one using the CrossFireX-Technology. This is provided for Windows 7 DirectX 10+ but NOT for Windows XP or Linux! For more information compare the AMD dual graphics FAQ: http://www.amd.com/us/products/technologies/dual-graphics/pages/dual-graphics.aspx#4

If there is any newer information about dual graphics and Linux: Please let me know!
```

but since he does not use the exact simular card to mine i won't try what he did.
Safety reasons for my machine don't want to break things xp.

Greetings InQontroll and thanks in advance.

---

### Post by InQontroll on 2012-11-15
also read post above.

I found this usefull information,
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
But for me its in a unreadable language.
Would someone care to explain a few steps so i could finally install the radeon driver for ubuntu and get it to work.

Its a really hard issue, not so common as most luucky people have :).

---

### Post by InQontroll on 2012-11-15
At my school (graduate network administrator) my teachers couldnt resolve the problem either..

I don't take a not possible as answer. I will succeed there should be someone who had the same problem and was able to run ubuntu smooth.

I really need help to this matter, I'm nearly there cuz i found this is a known issue. Its ofcource something to do whit my drivers for radeon dual graphics.

I have a post whit the answer posted above.
The thing is its hard for me to understand what they mean. 

English is not my native sorry for that!

---

### Post by InQontroll on 2012-11-15
Please someone?? :/
I'm really trying anything out here!
need help, damn if i knew a linux installation would take so mutch trouble...

---

### Post by bcbc on 2012-11-15
> **InQontroll said:**
> ouch pff.
hate it when things won't work out!
Oh does it help if i say this is in my comp: quad core and radeon dual graphics?

I also found out about someone else having trouble whit a dual graphics.

> I have the A6-3400m APU (integrated 6520G, discrete 6470M) and my experience until now is:

The Ubuntu built-in "radeon" driver does NOT support "dual graphics". To get the radeon driver without dual graphics work properly, the discrete graphics card should be switched off in the BIOS (less power consumption, ...)

AMD provides a proprietary driver called "fglrx". This driver can be installed via the system settings "additional drivers" or the latest version directly downloaded from AMD. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) My experience: The Ubuntu fglrx version is much toooo old: I had a lot of problems with wine and the activated discrete graphics card because that driver recognised a wrong graphics card (7400m series instead of 64oom series). With the latest AMD driver (Catalyst 12.10): working.

The fglrx drivers for Linux/Ubuntu are provided with a graphical configuration application called Catalyst Control Center and can also be configured via command line via amdconfig. With both configuration tools it is possible to switch between the discrete und the integrated graphics engine. This is called PowerXpress. With Windows this switch can be done without reboot but X needs a restart. Therefore the powersaving feature called PowerPlay does not use PowerXpress under Linux but just other features like dynamic clock rate change, .... BUT: PowerXpress is NOT "dual graphics".

"dual graphics" means: Both graphics engine act like a single one using the CrossFireX-Technology. This is provided for Windows 7 DirectX 10+ but NOT for Windows XP or Linux! For more information compare the AMD dual graphics FAQ: [http://www.amd.com/us/products/technologies/dual-graphics/pages/dual-graphics.aspx#4](http://www.amd.com/us/products/technologies/dual-graphics/pages/dual-graphics.aspx#4)

If there is any newer information about dual graphics and Linux: Please let me know!

but since he does not use the exact simular card to mine i won't try what he did.
Safety reasons for my machine don't want to break things xp.

Greetings InQontroll and thanks in advance.
Yes you can do that - that's where I was going. But the erratic problems booting Ubuntu that result in you having to keep reinstalling are not normal. And there's little point running an install that lasts one or two boots.

If you need Ubuntu you can easily install it under Windows using Virtual Box or VMWare. It's not going to work great for games or graphics intensive stuff, but apparently you can't use your graphics card anyway so it shouldn't be such a big loss. I'd also recommend 12.04 in that case because it supports 2d unity so should run better in the vm.

---

### Post by InQontroll on 2012-11-15
damn that sucks...
You really mean i can only do it using vmware..
how lame is that, isnt there really another way?

---

### Post by bcbc on 2012-11-15
> **InQontroll said:**
> damn that sucks...
You really mean i can only do it using vmware..

That gives you a chance to try out Ubuntu - and it works fine for most tasks (i.e. is exactly the same as running a normal install for most non-graphic related tasks). If you like it, then this is what I'd suggest:

If others with the same or very similar cards are successfully running Ubuntu then there is no reason that you shouldn't be able to. I'd recommend posting on that thread you found so you get someone with the same hardware who can answer specific questions and guide you.

If you're still not able to do it with the same workarounds, then I suggest you try to hook up with an ubuntu loco team in your area and find someone who can help you in person.

Since most people don't use Wubi they'll likely help you install a normal dual boot (which is the right thing anyway). Beforehand, create full restore image of Windows and a system repair CD (if you don't have the original install DVD). Also take full data backups. Then you'll be set for any outcome.

---

### Post by InQontroll on 2012-11-15
> **bcbc said:**
> That gives you a chance to try out Ubuntu - and it works fine for most tasks (i.e. is exactly the same as running a normal install for most non-graphic related tasks). If you like it, then this is what I'd suggest:

If others with the same or very similar cards are successfully running Ubuntu then there is no reason that you shouldn't be able to. I'd recommend posting on that thread you found so you get someone with the same hardware who can answer specific questions and guide you.

If you're still not able to do it with the same workarounds, then I suggest you try to hook up with an ubuntu loco team in your area and find someone who can help you in person.

Since most people don't use Wubi they'll likely help you install a normal dual boot (which is the right thing anyway). Beforehand, create full restore image of Windows and a system repair CD (if you don't have the original install DVD). Also take full data backups. Then you'll be set for any outcome.


I allready used ubuntu, the thing is i did not use it on this comp..
And damn hell i don't like windows compared to ubuntu.

The vmware is no selution.
wubi actually is no sulution either..

I want to do it using a live usb/cd and install it using that once and for all.

But before i do that i need to be sure if its gonna run smooth.

backups have been taken ages ago :).
well i'm going to report back tomorrow when i installed the iso on my usb.
but wont install it before i'm sure the radeon dual graphics card wont make trouble in future.

sorry for my bad english :) i'm from belgium :D

---

### Post by InQontroll on 2012-11-24
Ubuntu got installed all runs well.
You need a clean install if you want it on pavilion dv7

No windows or other os installed. Graphics drivers run well, no overheating and smooth startup.

Greetings, InQontroll.

---

