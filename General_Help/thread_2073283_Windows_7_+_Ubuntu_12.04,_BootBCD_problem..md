---
title: "Windows 7 + Ubuntu 12.04, Boot\BCD problem."
date: 2012-10-19
forum: General Help
---

### Post by grzekos on 2012-10-19
Hello,
I'm pretty new to Ubuntu and it seems I need some help. I installed Ubuntu 12.04 few days ago,  everything went well. I installed EasyBCD also program on my Windows 7**x64bits** to create Ubuntu registration. This + GRUB2 made me to choose Windows7 two times every-time I restart my computer. It was bothering me so I've decided to click on 'reset BCD' in the EasyBCD program. After a restart of computer Windows7 did not want to start at all. Error which appeared:

//Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your windows installation disc and restart your computer.
2. Choose your language setting, and then click "Next"
3. Click "Repair your computer"

If you do not have this disc contact your system administrator or computer manufacturer for assistance.

File: \Boot\BCD

Status: 0xc0000098

Info: This windows Boot Configuration Data file does not contain a valid OS entry.//

I can't neither open Windows7 recovery loader (error: invalid EFI file path). I have Windows7 on DVD but it doesn't want to boot itself - can't enter BIOS. I have no idea what I should do next. I have some important stuff on my Windows7. What should I do next? Is it repairable at all, is it repairable from ubuntu? I have tried to boot-repair GRUB, but it didn't help. I'm completely lost...
Thanks in advance for any tips.

---

### Post by Mark Phelps on 2012-10-19
Since you apparently want to continue to use EasyBCD to boot both Windows and Ubuntu, you have a couple of avenues to get techincal help ...

First, I would suggest you go to a Win7 forum (sevenforums.com) and look through their tutorials on repairing Windows 7 boot.  There are ways to do this using Startup Repair and ways using the command line. But, BOTH will require you to be able to boot from the Win7 DVD -- as THAT is where the apps are that are required.

Second, you could go to the NeoSmart Technology forums and post about the problem with EasyBCD -- but you might need a working Win7 boot in order to repair those.

Also, the general way to repair boot problems is using Boot-Repair, but if that won't work, you will have to focus on the Win7 forums as the first approach.

---

### Post by grzekos on 2012-10-19
> **Mark Phelps said:**
> Since you apparently want to continue to use EasyBCD to boot both Windows and Ubuntu, you have a couple of avenues to get techincal help ...

First, I would suggest you go to a Win7 forum (sevenforums.com) and look through their tutorials on repairing Windows 7 boot.  There are ways to do this using Startup Repair and ways using the command line. But, BOTH will require you to be able to boot from the Win7 DVD -- as THAT is where the apps are that are required.

Second, you could go to the NeoSmart Technology forums and post about the problem with EasyBCD -- but you might need a working Win7 boot in order to repair those.

Also, the general way to repair boot problems is using Boot-Repair, but if that won't work, you will have to focus on the Win7 forums as the first approach.

I don't want to continue use EasyBCD, GRUB2 is fine to me. The main problem is, I don't know how to boot a CD/DVD from GRUB2 so WIndows7 can actually start. If someone could lead me to there I think I will handle the issue.

---

### Post by oldfred on 2012-10-19
You should be booting CD from BIOS not grub.

Do you have UEFI? Or was this error wrong?
> error: invalid EFI file path

Booting UEFI is different and Windows repairCD have to be changed to work with UEFI.
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)

If not sure of configuration, may be best to post link to BootInfo report.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by grzekos on 2012-10-19
[HTML]                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    574863360 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt9)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 1354481154 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt7)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792   574,861,311   574,187,520 Data partition (Windows/Linux)
/dev/sda4     574,863,360   574,865,407         2,048 BIOS Boot partition
/dev/sda5     574,865,408 1,354,441,579   779,576,172 Data partition (Windows/Linux)
/dev/sda6   1,413,949,440 1,465,147,618    51,198,179 Windows Recovery Environment (Windows)
/dev/sda7   1,354,442,752 1,355,442,175       999,424 Data partition (Windows/Linux)
/dev/sda8   1,355,442,176 1,374,973,951    19,531,776 Data partition (Windows/Linux)
/dev/sda9   1,374,973,952 1,382,787,071     7,813,120 Swap partition (Linux)
/dev/sda10  1,382,787,072 1,413,949,439    31,162,368 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8004-B626                              vfat       SYSTEM
/dev/sda10       63587317-428f-4ad5-8d70-0557968d432e   ext4       
/dev/sda3        A0EA67A2EA677386                       ntfs       OS
/dev/sda5        249A9D619A9D3072                       ntfs       Drugi
/dev/sda6        8E7233AF72339AC3                       ntfs       Recovery
/dev/sda7        66f4a3e2-e390-4e16-817e-66800aae126a   ext4       
/dev/sda8        36bb4529-476b-4988-a3e4-2cb362756a53   ext4       
/dev/sda9        76bc063b-047c-4091-b2ab-c70b77ac059a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /home                    ext4       (rw)
/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda7        /boot                    ext4       (rw)
/dev/sda8        /                        ext4       (rw,errors=remount-ro)


============================= sda7/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt8)'
search --no-floppy --fs-uuid --set=root 36bb4529-476b-4988-a3e4-2cb362756a53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt7)'
  search --no-floppy --fs-uuid --set=root 66f4a3e2-e390-4e16-817e-66800aae126a
  set locale_dir=($root)/grub/locale
  set lang=pl_PL
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
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 66f4a3e2-e390-4e16-817e-66800aae126a
    linux    /vmlinuz-3.2.0-32-generic root=UUID=36bb4529-476b-4988-a3e4-2cb362756a53 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 66f4a3e2-e390-4e16-817e-66800aae126a
    echo    'Loading Linux 3.2.0-32-generic ...'
    linux    /vmlinuz-3.2.0-32-generic root=UUID=36bb4529-476b-4988-a3e4-2cb362756a53 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-32-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 66f4a3e2-e390-4e16-817e-66800aae126a
    linux    /vmlinuz-3.2.0-29-generic root=UUID=36bb4529-476b-4988-a3e4-2cb362756a53 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 66f4a3e2-e390-4e16-817e-66800aae126a
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /vmlinuz-3.2.0-29-generic root=UUID=36bb4529-476b-4988-a3e4-2cb362756a53 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root 8004-B626
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

menuentry "Windows UEFI memory test" {
search --fs-uuid --no-floppy --set=root 8004-B626
chainloader (${root})/EFI/Microsoft/Boot/memtest.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root A0EA67A2EA677386
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda6)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt6)'
    search --no-floppy --fs-uuid --set=root 8E7233AF72339AC3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 646.106945038 = 693.752049664  grub/grub.cfg                                  1
 645.902870178 = 693.532925952  initrd.img-3.2.0-29-generic                    2
 645.910936356 = 693.541586944  initrd.img-3.2.0-32-generic                    3
 645.866926193 = 693.494331392  vmlinuz-3.2.0-29-generic                       2
 645.874744415 = 693.502726144  vmlinuz-3.2.0-32-generic                       2

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=36bb4529-476b-4988-a3e4-2cb362756a53 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=66f4a3e2-e390-4e16-817e-66800aae126a /boot           ext4    defaults        0       2
# /home was on /dev/sda10 during installation
UUID=63587317-428f-4ad5-8d70-0557968d432e /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=76bc063b-047c-4091-b2ab-c70b77ac059a none            swap    sw              0       0
UUID=8004-B626    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 646.387498856 = 694.053292032  initrd.img                                     3
 646.379432678 = 694.044631040  initrd.img.old                                 2
 646.351306915 = 694.014431232  vmlinuz                                        2
 646.343488693 = 694.006036480  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 de 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 06 00 11 03 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 26 b6 04 80 4e  4f 20 4e 41 4d 45 20 20  |..)&...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


[/HTML]

---

### Post by grzekos on 2012-10-19
Do You think it might be a MBR connected problem? Should I try to fix it with ms-sys or it is a long-shot? I'm newbie when it comes to stuff like that.

---

### Post by oldfred on 2012-10-19
You have a new system with UEFI not BIOS and gpt partitioning.

But you installed Ubuntu in BIOS mode. You also installed the grub boot loader to the partition boot sector of sda7. That will never be used.

With UEFI you need to boot the Ubuntu 64 bit installer in UEFI mode. Then it will also install in UEFI mode. And then you install grub to the efi partition. 

Boot-Repair has a function to convert MBR Ubuntu installs to UEFI installs since so many are making that mistake. It uninstalls grub-pc and installs grub-efi and updates fstab with efi partition info.

But I am not sure if your sda1 efi partition has an issue or not?? I thought script showed something in Boot Sector type. It just may need chkdsk from a Windows repair CD.

---

### Post by grzekos on 2012-10-19
> With UEFI you need to boot the Ubuntu 64 bit installer in UEFI mode.

How can I do it? Can You lead me step by step? I would appreciated it very much. 

Does it mean I have to reinstall Ubuntu?

---

### Post by oldfred on 2012-10-19
No, you should not have to reinstall since Boot-Repair makes it easy to fix.

From your UEFI (BIOS) you should select the Ubuntu ISO. When you do that you should have two choices to boot. One is UEFI and the other is BIOS/AHCI/legacy or whatever. You want to boot in UEFI mode.

You can run Boot-Repair from your liveCD or download a full liveCD to make fixes.

---

