---
title: "How to change /boot partition size without formatting?"
date: 2013-06-18
forum: General Help
---

### Post by arashiko28 on 2013-06-18
I made a terrible mistake and assigned only 200MB to /boot instead of 20GB... I need to resize without formatting, if possible... I think it's worth to mention that I've encrypted my HDD... on gparted there's a red warning sign and all options are blocked.
Please help!

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by Cheesemill on 2013-06-19
> **ahallubuntu said:**
> Why do you even want/need a separate /boot partition?[/CODE]

Because it's needed if the rest of the drive is encrypted.

To the OP, try uninstalling any old kernels. This should free up some space in /boot.

---

### Post by arashiko28 on 2013-06-19
>  sudo fdisk -l
[sudo] password for arashiko: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000aad3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999945142272 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953017856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 995.7 GB, 995673243648 bytes
255 heads, 63 sectors/track, 121050 cylinders, total 1944674304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4223 MB, 4223664128 bytes
255 heads, 63 sectors/track, 513 cylinders, total 8249344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

I'll try to clean up the old kernels.

---

### Post by arashiko28 on 2013-06-19
I found this... I don't know what to do from here....
```
 find /boot/ -type f | xargs du | sort -n
find: `/boot/.Trash-0': Permission denied
1    /boot/grub/gfxblacklist.txt
1    /boot/grub/grubenv
1    /boot/grub/i386-pc/all_video.mod
1    /boot/grub/i386-pc/boot.img
1    /boot/grub/i386-pc/cdboot.img
1    /boot/grub/i386-pc/crypto.lst
1    /boot/grub/i386-pc/diskboot.img
1    /boot/grub/i386-pc/fs.lst
1    /boot/grub/i386-pc/g2hdr.img
1    /boot/grub/i386-pc/lnxboot.img
1    /boot/grub/i386-pc/partmap.lst
1    /boot/grub/i386-pc/parttool.lst
1    /boot/grub/i386-pc/pxeboot.img
1    /boot/grub/i386-pc/setjmp.mod
1    /boot/grub/i386-pc/terminal.lst
1    /boot/grub/i386-pc/video.lst
1    /boot/grub/locale/en_AU.mo
1    /boot/grub/locale/en_CA.mo
2    /boot/grub/i386-pc/adler32.mod
2    /boot/grub/i386-pc/aout.mod
2    /boot/grub/i386-pc/backtrace.mod
2    /boot/grub/i386-pc/cmostest.mod
2    /boot/grub/i386-pc/cmp.mod
2    /boot/grub/i386-pc/cpuid.mod
2    /boot/grub/i386-pc/crc64.mod
2    /boot/grub/i386-pc/datehook.mod
2    /boot/grub/i386-pc/datetime.mod
2    /boot/grub/i386-pc/dm_nv.mod
2    /boot/grub/i386-pc/echo.mod
2    /boot/grub/i386-pc/exfctest.mod
2    /boot/grub/i386-pc/gcry_arcfour.mod
2    /boot/grub/i386-pc/hello.mod
2    /boot/grub/i386-pc/keystatus.mod
2    /boot/grub/i386-pc/lsmmap.mod
2    /boot/grub/i386-pc/mdraid09_be.mod
2    /boot/grub/i386-pc/mdraid09.mod
2    /boot/grub/i386-pc/mdraid1x.mod
2    /boot/grub/i386-pc/memdisk.mod
2    /boot/grub/i386-pc/part_acorn.mod
2    /boot/grub/i386-pc/part_amiga.mod
2    /boot/grub/i386-pc/part_dvh.mod
2    /boot/grub/i386-pc/part_plan.mod
2    /boot/grub/i386-pc/part_sun.mod
2    /boot/grub/i386-pc/part_sunpc.mod
2    /boot/grub/i386-pc/password.mod
2    /boot/grub/i386-pc/pbkdf2.mod
2    /boot/grub/i386-pc/pci.mod
2    /boot/grub/i386-pc/priority_queue.mod
2    /boot/grub/i386-pc/raid5rec.mod
2    /boot/grub/i386-pc/read.mod
2    /boot/grub/i386-pc/reboot.mod
2    /boot/grub/i386-pc/test_blockarg.mod
2    /boot/grub/i386-pc/time.mod
2    /boot/grub/i386-pc/trig.mod
2    /boot/grub/i386-pc/true.mod
2    /boot/grub/i386-pc/usbserial_common.mod
2    /boot/grub/i386-pc/xnu_uuid.mod
3    /boot/grub/i386-pc/bitmap.mod
3    /boot/grub/i386-pc/bitmap_scale.mod
3    /boot/grub/i386-pc/blocklist.mod
3    /boot/grub/i386-pc/boot.mod
3    /boot/grub/i386-pc/bufio.mod
3    /boot/grub/i386-pc/cat.mod
3    /boot/grub/i386-pc/configfile.mod
3    /boot/grub/i386-pc/date.mod
3    /boot/grub/i386-pc/freedos.mod
3    /boot/grub/i386-pc/fshelp.mod
3    /boot/grub/i386-pc/functional_test.mod
3    /boot/grub/i386-pc/gcry_crc.mod
3    /boot/grub/i386-pc/gcry_rfc2268.mod
3    /boot/grub/i386-pc/help.mod
3    /boot/grub/i386-pc/iorw.mod
3    /boot/grub/i386-pc/loopback.mod
3    /boot/grub/i386-pc/lsapm.mod
3    /boot/grub/i386-pc/lzma_decompress.img
3    /boot/grub/i386-pc/memrw.mod
3    /boot/grub/i386-pc/msdospart.mod
3    /boot/grub/i386-pc/ntldr.mod
3    /boot/grub/i386-pc/part_apple.mod
3    /boot/grub/i386-pc/part_bsd.mod
3    /boot/grub/i386-pc/part_gpt.mod
3    /boot/grub/i386-pc/part_msdos.mod
3    /boot/grub/i386-pc/password_pbkdf2.mod
3    /boot/grub/i386-pc/play.mod
3    /boot/grub/i386-pc/probe.mod
3    /boot/grub/i386-pc/pxechain.mod
3    /boot/grub/i386-pc/raid6rec.mod
3    /boot/grub/i386-pc/sleep.mod
3    /boot/grub/i386-pc/testload.mod
3    /boot/grub/i386-pc/tga.mod
3    /boot/grub/i386-pc/usbserial_ftdi.mod
3    /boot/grub/i386-pc/usbserial_pl2303.mod
3    /boot/grub/i386-pc/vga_text.mod
4    /boot/grub/i386-pc/at_keyboard.mod
4    /boot/grub/i386-pc/chain.mod
4    /boot/grub/i386-pc/command.lst
4    /boot/grub/i386-pc/cs5536.mod
4    /boot/grub/i386-pc/gcry_md4.mod
4    /boot/grub/i386-pc/gcry_md5.mod
4    /boot/grub/i386-pc/gcry_sha256.mod
4    /boot/grub/i386-pc/gptsync.mod
4    /boot/grub/i386-pc/hexdump.mod
4    /boot/grub/i386-pc/lsacpi.mod
4    /boot/grub/i386-pc/minicmd.mod
4    /boot/grub/i386-pc/minix2_be.mod
4    /boot/grub/i386-pc/minix2.mod
4    /boot/grub/i386-pc/minix3_be.mod
4    /boot/grub/i386-pc/minix3.mod
4    /boot/grub/i386-pc/minix_be.mod
4    /boot/grub/i386-pc/minix.mod
4    /boot/grub/i386-pc/moddep.lst
4    /boot/grub/i386-pc/ntfscomp.mod
4    /boot/grub/i386-pc/pxe.mod
4    /boot/grub/i386-pc/romfs.mod
4    /boot/grub/i386-pc/search_fs_file.mod
4    /boot/grub/i386-pc/search_fs_uuid.mod
4    /boot/grub/i386-pc/search_label.mod
4    /boot/grub/i386-pc/search.mod
4    /boot/grub/i386-pc/usb_keyboard.mod
4    /boot/grub/i386-pc/usbtest.mod
4    /boot/grub/i386-pc/videoinfo.mod
4    /boot/grub/locale/en_GB.mo
5    /boot/grub/i386-pc/biosdisk.mod
5    /boot/grub/i386-pc/cpio_be.mod
5    /boot/grub/i386-pc/cpio.mod
5    /boot/grub/i386-pc/crypto.mod
5    /boot/grub/i386-pc/elf.mod
5    /boot/grub/i386-pc/extcmd.mod
5    /boot/grub/i386-pc/gettext.mod
5    /boot/grub/i386-pc/halt.mod
5    /boot/grub/i386-pc/hashsum.mod
5    /boot/grub/i386-pc/keylayouts.mod
5    /boot/grub/i386-pc/ls.mod
5    /boot/grub/i386-pc/lspci.mod
5    /boot/grub/i386-pc/newc.mod
5    /boot/grub/i386-pc/odc.mod
5    /boot/grub/i386-pc/parttool.mod
5    /boot/grub/i386-pc/pata.mod
5    /boot/grub/i386-pc/scsi.mod
5    /boot/grub/i386-pc/sfs.mod
5    /boot/grub/i386-pc/tar.mod
5    /boot/grub/i386-pc/terminal.mod
5    /boot/grub/i386-pc/test.mod
5    /boot/grub/i386-pc/vga.mod
5    /boot/grub/i386-pc/videotest.mod
6    /boot/grub/i386-pc/affs.mod
6    /boot/grub/i386-pc/ata.mod
6    /boot/grub/i386-pc/drivemap.mod
6    /boot/grub/i386-pc/exfat.mod
6    /boot/grub/i386-pc/ext2.mod
6    /boot/grub/i386-pc/fat.mod
6    /boot/grub/i386-pc/gcry_sha512.mod
6    /boot/grub/i386-pc/geli.mod
6    /boot/grub/i386-pc/http.mod
6    /boot/grub/i386-pc/jpeg.mod
6    /boot/grub/i386-pc/linux16.mod
6    /boot/grub/i386-pc/loadenv.mod
6    /boot/grub/i386-pc/setpci.mod
6    /boot/grub/i386-pc/tftp.mod
6    /boot/grub/i386-pc/ufs1.mod
6    /boot/grub/i386-pc/ufs2.mod
6    /boot/grub/i386-pc/video_bochs.mod
6    /boot/grub/i386-pc/video_cirrus.mod
6    /boot/grub/i386-pc/xfs.mod
6    /boot/grub/i386-pc/zfscrypt.mod
7    /boot/grub/i386-pc/afs.mod
7    /boot/grub/i386-pc/hfsplus.mod
7    /boot/grub/i386-pc/jfs.mod
7    /boot/grub/i386-pc/ldm.mod
7    /boot/grub/i386-pc/luks.mod
7    /boot/grub/i386-pc/lvm.mod
7    /boot/grub/i386-pc/nilfs2.mod
7    /boot/grub/i386-pc/plan9.mod
7    /boot/grub/i386-pc/png.mod
7    /boot/grub/i386-pc/sendkey.mod
7    /boot/grub/i386-pc/serial.mod
7    /boot/grub/i386-pc/squash4.mod
7    /boot/grub/i386-pc/uhci.mod
7    /boot/grub/i386-pc/zfsinfo.mod
8    /boot/grub/i386-pc/915resolution.mod
8    /boot/grub/i386-pc/bfs.mod
8    /boot/grub/i386-pc/efiemu32.o
8    /boot/grub/i386-pc/gcry_blowfish.mod
8    /boot/grub/i386-pc/gcry_rmd160.mod
8    /boot/grub/i386-pc/gcry_sha1.mod
8    /boot/grub/i386-pc/gzio.mod
8    /boot/grub/i386-pc/hdparm.mod
8    /boot/grub/i386-pc/hfs.mod
8    /boot/grub/i386-pc/udf.mod
8    /boot/grub/i386-pc/usbms.mod
9    /boot/grub/grub.cfg
9    /boot/grub/i386-pc/ahci.mod
9    /boot/grub/i386-pc/cryptodisk.mod
9    /boot/grub/i386-pc/iso9660.mod
9    /boot/grub/i386-pc/lzopio.mod
9    /boot/grub/i386-pc/mmap.mod
9    /boot/grub/i386-pc/reiserfs.mod
10    /boot/grub/i386-pc/acpi.mod
10    /boot/grub/i386-pc/diskfilter.mod
10    /boot/grub/i386-pc/grldr.img
10    /boot/grub/i386-pc/ntfs.mod
10    /boot/grub/i386-pc/usb.mod
10    /boot/grub/i386-pc/vbe.mod
11    /boot/grub/i386-pc/ohci.mod
11    /boot/grub/i386-pc/terminfo.mod
11    /boot/grub/i386-pc/video.mod
12    /boot/grub/i386-pc/efiemu64.o
12    /boot/grub/i386-pc/font.mod
12    /boot/grub/i386-pc/gcry_tiger.mod
12    /boot/grub/i386-pc/gfxterm.mod
12    /boot/grub/i386-pc/linux.mod
14    /boot/grub/i386-pc/multiboot2.mod
14    /boot/grub/i386-pc/multiboot.mod
16    /boot/grub/i386-pc/btrfs.mod
16    /boot/grub/i386-pc/relocator.mod
16    /boot/grub/i386-pc/xzio.mod
17    /boot/grub/i386-pc/ehci.mod
17    /boot/grub/i386-pc/gcry_seed.mod
17    /boot/grub/i386-pc/gcry_serpent.mod
18    /boot/grub/i386-pc/gcry_cast5.mod
20    /boot/grub/i386-pc/gcry_des.mod
20    /boot/grub/i386-pc/gcry_rijndael.mod
21    /boot/grub/i386-pc/video_fb.mod
25    /boot/grub/i386-pc/efiemu.mod
25    /boot/grub/i386-pc/gcry_whirlpool.mod
27    /boot/grub/i386-pc/core.img
27    /boot/grub/i386-pc/gdb.mod
29    /boot/grub/i386-pc/legacycfg.mod
30    /boot/grub/i386-pc/kernel.img
31    /boot/grub/i386-pc/bsd.mod
34    /boot/grub/i386-pc/gfxmenu.mod
34    /boot/grub/i386-pc/xnu.mod
35    /boot/grub/i386-pc/gcry_camellia.mod
37    /boot/grub/i386-pc/zfs.mod
40    /boot/grub/i386-pc/gcry_twofish.mod
44    /boot/grub/i386-pc/net.mod
48    /boot/grub/i386-pc/hwmatch.mod
52    /boot/grub/i386-pc/regexp.mod
109    /boot/grub/i386-pc/normal.mod
153    /boot/config-3.8.0-23-generic
153    /boot/config-3.8.0-25-generic
174    /boot/memtest86+.bin
176    /boot/memtest86+_multiboot.bin
903    /boot/abi-3.8.0-23-generic
903    /boot/abi-3.8.0-25-generic
2185    /boot/grub/fonts/unicode.pf2
3002    /boot/System.map-3.8.0-23-generic
3003    /boot/System.map-3.8.0-25-generic
5254    /boot/vmlinuz-3.8.0-23-generic
5254    /boot/vmlinuz-3.8.0-25-generic
31397    /boot/initrd.img-3.8.0-23-generic
31399    /boot/initrd.img-3.8.0-25-generic

```

---

### Post by Bucky Ball on 2013-06-19
Boot from the LiveCD and see what you can come up with. You might be able to easily move stuff around and if you are going to resize partitions they need to be unmounted; booting from the LiveCD is the best way to achieve this. 

You might get away with booting from the LiveCD, launching Gparted and resizing, depending on how things are set up. Shrink the partition next to the /boot partition from that end, if you follow me, and expand the /boot partition into the free space that creates.

---

### Post by Impavidus on 2013-06-19
You have two kernels installed, which is OK. When I add up those numbers I get nowhere near 200MB. It's actually just 85746kB. This just leaves the /boot/.Trash-0 directory. Can you see what's in there? Anyway, it's called trash so you can probably empty it.

---

### Post by arashiko28 on 2013-06-19
It is empty, I'm creating an USB boot, so I can see if I can get out of this... Now that I remember, I didn't do this... this is the default configuration, I only chose to encrypt my HDD.

---

### Post by arashiko28 on 2013-06-19
Long story short, Had to wipe my entire HDD... but fixed the problem. Did a manual install and assigned 1GB to /boot, 30 GB to / and the rest to /home. Hope this will be enough.
Thanks to the ones who took the time to advise me :D

---

### Post by Bucky Ball on 2013-06-19
Please mark thread as solved to help the community. Follow the link in my signature.

---

