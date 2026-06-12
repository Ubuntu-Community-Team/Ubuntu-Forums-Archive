---
title: "A lot of /boot/grub vanished!"
date: 2012-10-22
forum: General Help
---

### Post by Stonecold1995 on 2012-10-22
For some reason, most of the files in /boot/grub just vanished!  When I run "sudo update-grub", I get this:
```
alex@kubuntu:~$ sudo update-grub
Generating grub.cfg ...
  No volume groups found
done
```

And the contents of /boot/grub are:
```
alex@kubuntu:~$ ls -CF /boot/grub
fonts/  gfxblacklist.txt  grub.cfg  grubenv  i386-pc/  load.cfg  locale/  unicode.pf2
```

Also, when I reboot, Grub only shows Memtest and Ubuntu...


**EDIT: I fell really stupid right now...  It turns out they all moved from /boot/grub to /boot/grub/i386-pc...  But I'm still having problems with "sudo update-grub" not being able to do anything and not having the right menu entries.**

---

### Post by ~LoKe on 2012-10-22
> **Stonecold1995 said:**
> For some reason, most of the files in /boot/grub just vanished!  When I run "sudo update-grub", I get this:
```
alex@kubuntu:~$ sudo update-grub
Generating grub.cfg ...
  No volume groups found
done
```

And the contents of /boot/grub are:
```
alex@kubuntu:~$ ls -CF /boot/grub
fonts/  gfxblacklist.txt  grub.cfg  grubenv  i386-pc/  load.cfg  locale/  unicode.pf2
```

Also, when I reboot, Grub only shows Memtest and Ubuntu...


**EDIT: I fell really stupid right now...  It turns out they all moved from /boot/grub to /boot/grub/i386-pc...  But I'm still having problems with "sudo update-grub" not being able to do anything and not having the right menu entries.**
sudo grub-install /dev/sdX

---

### Post by Stonecold1995 on 2012-10-22
> **~LoKe said:**
> sudo grub-install /dev/sdX

I have two drives, one for / and one for /home (drives, not partitions), and both are encrypted.  Will trying to install it to / corrupt my disk if its encrypted, or damage any data?

EDIT: I went and did that to /dev/sdb.  It completely f*cked up my disk and forced Grub into the text-only mode after being installed to the MBR (so I had to set the root, boot options, and start the kernel manually) and I'm still trying to find out how to undo what I did to the MBR so I can use graphical Grub again.  I tried using the "install-mbr" command (sudo install-mbr -i n -p 1 -t 0 /dev/sdb), but it didn't seem to do anything.  Currently, my disk layout is like this:
/dev/sdb5 = / (encrypted)
/dev/sda1 = /home (encrypted)
/dev/sdb1 = /boot

How do I set the boot device back to /dev/sdb1 (/boot), because the Grub that was installed to the MBR seems to be unable to do anything?

---

### Post by Stonecold1995 on 2012-10-23
I ran "bootinfoscript" and this is the output (I bolded what I thought was relevant):
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

[b] => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Testdisk is installed in the MBR of /dev/sdb.[/b]

sda1: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,465,147,391 1,465,145,344  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758    62,531,583    62,029,826   5 Extended
/dev/sdb5             501,760    62,531,583    62,029,824  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda1_crypt 74afd1aa-7510-408d-8b80-c28b704bf3ab   ext4       
/dev/mapper/sdb5_crypt bc224484-cdc1-403d-aaad-f4cc85734fd2   ext4       
/dev/sda1        7074348a-23ab-4140-ac64-2cc073387a20   crypto_LUKS 
/dev/sdb1        a797b490-b97a-413d-85da-0720ab258ce4   ext2       
/dev/sdb5        168c8fa4-352b-4a90-a4be-530259edf756   crypto_LUKS 
/dev/zram0       0d926c52-71b8-4693-9277-26d9807bb459   swap       
/dev/zram1       5c05bbb8-ab47-49fb-b786-05f5a21808a4   swap       
/dev/zram2       1191ee62-336e-4d9d-9905-6836fe0fc01d   swap       
/dev/zram3       29c8375b-c83d-4055-9095-2b53ceec2ec9   swap       
/dev/zram4       89fc8cd1-f6d8-4820-8cd4-bbf2dbaf70be   swap       
/dev/zram5       805e5d3c-1e6e-4dbd-8e4d-e8b4b9cc2777   swap       
/dev/zram6       889c3386-c895-4dd1-8fc2-ff7a8101315a   swap       
/dev/zram7       9556a6f1-22cb-41a4-a3c6-d8826eb16f94   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda1_crypt
sdb5_crypt

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/sda1_crypt /home                    ext4       (rw,noatime,errors=remount-ro)
/dev/mapper/sdb5_crypt /                        ext4       (rw,noatime,discard,errors=remount-ro)
/dev/sdb1        /boot                    ext2       (rw)


============================= sdb1/grub/grub.cfg: ==============================

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

insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  a797b490-b97a-413d-85da-0720ab258ce4
else
  search --no-floppy --fs-uuid --set=root a797b490-b97a-413d-85da-0720ab258ce4
fi
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=640x480
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
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.020999908 = 0.022548480    grub/grub.cfg                                  1
   0.210240364 = 0.225743872    initrd.img-3.2.0-30-generic                   96
   0.045204163 = 0.048537600    initrd.img-3.2.0-31-generic                   91
   0.081840515 = 0.087875584    initrd.img-3.2.0-32-generic                   112
   0.139793396 = 0.150102016    initrd.img-3.5.0-17-generic                   104
   0.171974182 = 0.184655872    initrd.img-3.5.0-18-generic                   108
   0.194385529 = 0.208719872    vmlinuz-3.2.0-30-generic                      21
   0.121084213 = 0.130013184    vmlinuz-3.2.0-31-generic                      22
   0.013683319 = 0.014692352    vmlinuz-3.2.0-32-generic                      21
   0.068150520 = 0.073176064    vmlinuz-3.5.0-17-generic                      23
   0.076579094 = 0.082226176    vmlinuz-3.5.0-18-generic                      21

======================== Unknown MBRs/Boot Sectors/etc: ========================

**Unknown BootLoader on sda1**

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  5d 93 37 df c4 d3 4d af  6d a6 53 2f e3 ae cf 41  |].7...M.m.S/...A|
00000080  a4 cb 8b 7a c1 b4 a8 4d  05 e3 f1 19 d5 de 53 42  |...z...M......SB|
00000090  af 50 a2 f0 4d a4 8c ba  0e 92 d4 5b 3a d9 13 ed  |.P..M......[:...|
000000a0  57 fc ba ea 00 00 d7 55  37 30 37 34 33 34 38 61  |W......U7074348a|
000000b0  2d 32 33 61 62 2d 34 31  34 30 2d 61 63 36 34 2d  |-23ab-4140-ac64-|
000000c0  32 63 63 30 37 33 33 38  37 61 32 30 00 00 00 00  |2cc073387a20....|
000000d0  00 ac 71 f3 00 03 5d 62  13 5c 87 db 27 45 d3 4b  |..q...]b.\..'E.K|
000000e0  68 fc f3 f0 ea da 2a af  db 51 e1 5a 1b 82 81 b6  |h.....*..Q.Z....|
000000f0  7f dd f2 bc 9d 48 b7 ed  00 00 00 08 00 00 0f a0  |.....H..........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

**Unknown BootLoader on sdb5**

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  1e b4 66 ff 14 f8 d9 3e  c2 35 97 e2 d7 48 d2 b0  |..f....>.5...H..|
00000080  5b 57 b6 cd 66 0e 04 5e  41 a7 1c 36 45 88 cd c7  |[W..f..^A..6E...|
00000090  96 cb 0e e6 3d 91 92 6e  72 2f 2b 5a 22 53 a1 e3  |....=..nr/+Z"S..|
000000a0  ca 99 35 d5 00 00 d7 55  31 36 38 63 38 66 61 34  |..5....U168c8fa4|
000000b0  2d 33 35 32 62 2d 34 61  39 30 2d 61 34 62 65 2d  |-352b-4a90-a4be-|
000000c0  35 33 30 32 35 39 65 64  66 37 35 36 00 00 00 00  |530259edf756....|
000000d0  00 ac 71 f3 00 03 5d 8c  b1 23 a6 ee 7e bd 26 4d  |..q...]..#..~.&M|
000000e0  9a 1f 75 97 fe 5e 41 e7  63 c3 73 32 2f fe 2f 1e  |..u..^A.c.s2/./.|
000000f0  0c e4 b6 d7 73 38 da aa  00 00 00 08 00 00 0f a0  |....s8..........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

  **No volume groups found**
```

My guess is that the problem is that the Grub bootloader should be on /dev/sdb, not /dev/sda (/dev/sda is only for /home, /dev/sdb contains the root and /boot).  I'm hesitant to use "grub-install" again because that messed my computer up pretty bad.  And why in the world is Testdisk installed to the MBR of /dev/sdb??

---

### Post by Stonecold1995 on 2012-10-24
bump

---

### Post by oldfred on 2012-10-24
It should not really matter whether grub2's boot loader is in sda or sdb, as long as you are booting from that drive. I normally suggest having grub in the MBR of the same drive as the install, just so if the other drive fails you can still boot.

The testdisk boot loader may be from previous attempts to recover something? It can install a generic boot loader/ Windows like boot loader.

Your grub.cfg is missing boot stanzas. It did not see your kernels hat script does show you have.

With encription I do not know how to reinstall. I think you have to be sure to also mount the encrypted partition with your pass phase so grub can update correctly.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

Does Boot-Repair work if you manually mount encrypted partitions first?

Is there some reason you have 8 swaps in zram?

---

### Post by hal8000 on 2012-10-24
Try OldFred's solution first.

However, the reason testdisk  has been wrote to the MBR of sdb is because you placed it there, quote from post 3#


>  I tried using the "install-mbr" command (sudo install-mbr -i n -p 1 -t 0 /dev/sdb), but it didn't seem to do anything. Currently, my disk layout is like this:
/dev/sdb5 = / (encrypted)
/dev/sda1 = /home (encrypted)
/dev/sdb1 = /boot


As you created a separate /boot partition on sdb1 grub2 needs to be installed into the MBR of sdb.

I would boot using Ubuntu CD in live mode, see if you can recover and backup any data first you want to keep and then try running

sudo grub-install /dev/sdb
sudo update-grub

Hope that helps, but do your backups first, if you can.

---

### Post by Stonecold1995 on 2012-10-24
> **oldfred said:**
> It should not really matter whether grub2's boot loader is in sda or sdb, as long as you are booting from that drive. I normally suggest having grub in the MBR of the same drive as the install, just so if the other drive fails you can still boot.
Grub IS installed, but it's only using the Grub boot prompt.

> **oldfred said:**
> Your grub.cfg is missing boot stanzas. It did not see your kernels hat script does show you have.
How do I get that back?  Running "sudo updage-grub" doesn't fix it, and it's too unique for me to copy one from another computer.  That command only does this:
```
alex@kubuntu:~$ sudo update-grub
[sudo] password for alex: 
Generating grub.cfg ...
  No volume groups found
done
```
But grub.cfg doesn't change at all.

> **oldfred said:**
> Is there some reason you have 8 swaps in zram?
ZRAM gives one swap device for each CPU, and I have 8 logical CPU cores.  Each swap can compress one GB of RAM (giving me 8 GB of swap).

> **hal8000 said:**
> As you created a separate /boot partition on sdb1 grub2 needs to be installed into the MBR of sdb.

I would boot using Ubuntu CD in live mode, see if you can recover and backup any data first you want to keep and then try running

sudo grub-install /dev/sdb
sudo update-grub

Hope that helps, but do your backups first, if you can.
I tried those commands, but no difference.  The output of bootinfoscript has changed to have this though:
```
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
```
This makes me think that the problem is that Grub is also installed to /dev/sda, and I'd assume the computer will look at the MBR of /dev/sda before /dev/sdb (and /dev/sda doesn't have the boot partition).  So from what I can tell, I currently have two problems.  One is that /dev/sda has Grub but no /boot, so Grub can't find grub.cfg.  And two is that grub.cfg is corrupt.  So I have to remove the bootloader from /dev/sda, and fix grub.cfg, and then I assume it'll work.  Does this sound right?

It's not that Grub is completely *gone*, it's that I followed ~LoKe's advice (sudo grub-install /dev/sdb) and that somehow messed up Grub, even though Grub is still sort of there.  I don't need a live CD because I can boot up, but I have to do so manually (I'm using this computer right now).  I need to know how to repair grub.cfg, and point the bootloader (if I got that right) to grub.cfg, because it seems like it cannot detect it, so it's falling back to the manual prompt.

[img]http://www.pictureshack.us/images/41938_HNI_0020.JPG[/img]

**EDIT: Would something like "sudo grub-install /dev/sdX --boot-directory=/boot" work?**

---

### Post by oldfred on 2012-10-24
If you are not in your install you have to mount the partition you want to install grub from and if a separate /boot you have to mount it also. 

#If separate /boot
$ sudo mount /dev/mapper/sdb5_crypt /  /mnt
$ sudo mount /dev/sdb1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sdb

or:

#If separate /boot & Natty or later
$ sudo mount /dev/mapper/sdb5_crypt /  /mnt
$ sudo mount /dev/sdb1 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Not sure if Boot-Repair works with encryption, but it should as long as you mount it first.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Stonecold1995 on 2012-10-24
I'm trying boot-repair, but I'm not sure if it detected my setup correctly.  It seems to think I'm using RAID, but I'm not.

[[IMG]http://www.pictureshack.us/thumbs/23966_raid.png[/IMG]](http://www.pictureshack.us/images/23966_raid.png)

Should I go ahead and run those commands?

---

### Post by oldfred on 2012-10-24
I thought encryption was LVM, not RAID. But I do not know either and cannot really say.

---

### Post by Stonecold1995 on 2012-10-24
So I managed to fix it with Boot Repair.  Reinstalling Grub worked, and I didn't loose any of my data even though the drives are encrypted.

I also found out what caused this.  Apparently Grub Customizer will corrupt grub.cfg and remove all menu entries if you try to rename any of them, even though that's one of the basic functions of that app.  So does anyone know how to rename Grub menu entries without using Grub Customizer?

Also, it seems that Memtest86+ is no longer in the menu, even though it is present in /boot.  How do I add that back to the menu?

---

### Post by oldfred on 2012-10-24
I thought grub customizer worked, but not with the new sub-menus in grub2 2.00.

This recommends grub customizer but has the old ways.

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Multiboot Ubuntu edit host names for better grub2 menu titles
[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20OS%20Hostnames.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20OS%20Hostnames.html)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I started before grub customizer and have never used it. I have so many old installs that I cannot really run the os-prober, so I turn it off. I only copy the entries  want into 40_custom similar to Cavsfan methods above. I also learned from Ranch Hand & drs305.

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Copy entires to and edit :
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

These were the old memtest entries I had.

```
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}



```

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by Stonecold1995 on 2012-10-24
I don't have /etc/grub.d/40_custom.  The closest I have are 41_custom and 40_custom_proxy.

```
alex@kubuntu:/etc/grub.d$ ls -CF
00_header*  05_debian_theme*  10_linux*  20_linux~1_proxy*  20_linux_xen*  20_memtest86+*  30_os-prober*  40_custom_proxy*  41_custom*  50_uefi-firmware*  bin/  proxifiedScripts/  README
```

---

### Post by oldfred on 2012-10-24
All the scripts are run if executable and have two digits and an underscore. But I do not have proxy versions with my grub2 2.00. Where are those coming from. It that related to your encryption? I just do not know.

What does your 40_custom_proxy file have in it.

this is my 40_custom from grub2 2.00 which I have not updated yet.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

Found it, your proxy files are from grub customizer.
[https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

---

### Post by Stonecold1995 on 2012-10-25
> **oldfred said:**
> What does your 40_custom_proxy file have in it.

```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom' | /etc/grub.d/bin/grubcfg_proxy "+*
+#text
-'Kubuntu (GNU/Linux)'~*there was a 32 character hash here, but I'm not sure if it's sensitive so I removed it*~
```

---

### Post by oldfred on 2012-10-25
It either is pulling in info from another location or running a script from that location. But if you are not running customizer then I would not care.

Just to clean up all those files I might do a full uninstall of grub2 and reinstall. That is an option in Boot-Repair.

---

### Post by Stonecold1995 on 2012-10-25
> **oldfred said:**
> Just to clean up all those files I might do a full uninstall of grub2 and reinstall. That is an option in Boot-Repair.

I already did that.  Using Boot Repair is what I used to fix (ish) Grub.

---

### Post by oldfred on 2012-10-26
I might backup everything in /etc/grub.d, then delete all the scripts,  and reinstall. It should then install all the default scripts.


chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YannBuntu on 2012-10-26
hello

> **Stonecold1995 said:**
> I already did that.  Using Boot Repair is what I used to fix (ish) Grub.

When you used the "Recommended Repair", did it ask you to type commands? If not, please:
1) indicate the URL that was provided by Boot-Repair at the end
2) run Boot-Repair --> Advanced Options --> GRUB options --> tick "Purge GRUB" --> Apply , tell us the new URL that will appear.

---

### Post by Stonecold1995 on 2012-10-26
> **oldfred said:**
> I might backup everything in /etc/grub.d, then delete all the scripts,  and reinstall. It should then install all the default scripts.


chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thank you!  Deleting the scripts and re-installing worked!

So the main culprit was Grub Customizer...  It seems to mess up Grub a lot for me, so I uninstalled it.  Does anyone know of a good alternative to Grub Customizer that works with my Grub?

---

### Post by YannBuntu on 2012-10-26
What do you use GRUB-Customizer for? (changing the timeout? making Windows the default OS?..)

---

### Post by oldfred on 2012-10-26
Customizer used to work well. But drs305 has a lot of info on doing it yourself. 

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Better link - above migrated to Ubuntu Community Documentation site
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)


I started doing it manually before Grub Customizer.  I turn off os-prober since I have a lot of now old installs and use 40_custom for all my entries I do want. I manually try to keep only 2 kernels. So I have two Ubuntu & my custom entries. Have not changed to that in grub2 2.00 yet but will try it in the next day or two.

---

### Post by Stonecold1995 on 2012-10-26
> **YannBuntu said:**
> What do you use GRUB-Customizer for? (changing the timeout? making Windows the default OS?..)

Changing the entry names and color, mainly.

---

### Post by YannBuntu on 2012-10-29
> **Stonecold1995 said:**
> Changing the entry names and color, mainly.

ok. For these changes, I don't know any graphical alternative to GRUB-Customizer. 
Changing the names in your /boot/grub/grub.cfg file is easy (but will be reset each time GRUB or Linux kernel is upgraded).
For the colors I don't know.
I don't recommend playing too much with GRUB configuration as any error may break the boot.

---

### Post by oldfred on 2012-10-29
I do not do themes, and do not know if it works with grub2 2.00 still. I just want a screen to choose and quickly boot.

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

