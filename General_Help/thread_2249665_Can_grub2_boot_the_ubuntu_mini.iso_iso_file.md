---
title: "Can grub2 boot the ubuntu mini.iso iso file?"
date: 2014-10-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-10-23
I have my grub2 multi-boot usb disk and i was wondering if i can add the mini.iso to the list, wasting a cd on a sub 50mb files really seems like a waste 
here are the files on the iso
```
mini
&#9500;&#9472;&#9472; adtxt.cfg
&#9500;&#9472;&#9472; boot
&#9474;   &#9492;&#9472;&#9472; grub
&#9474;       &#9500;&#9472;&#9472; efi.img
&#9474;       &#9500;&#9472;&#9472; font.pf2
&#9474;       &#9500;&#9472;&#9472; grub.cfg
&#9474;       &#9492;&#9472;&#9472; x86_64-efi
&#9474;           &#9500;&#9472;&#9472; acpi.mod
&#9474;           &#9500;&#9472;&#9472; adler32.mod
&#9474;           &#9500;&#9472;&#9472; ahci.mod
&#9474;           &#9500;&#9472;&#9472; all_video.mod
&#9474;           &#9500;&#9472;&#9472; aout.mod
&#9474;           &#9500;&#9472;&#9472; appleldr.mod
&#9474;           &#9500;&#9472;&#9472; archelp.mod
&#9474;           &#9500;&#9472;&#9472; ata.mod
&#9474;           &#9500;&#9472;&#9472; at_keyboard.mod
&#9474;           &#9500;&#9472;&#9472; backtrace.mod
&#9474;           &#9500;&#9472;&#9472; bfs.mod
&#9474;           &#9500;&#9472;&#9472; bitmap.mod
&#9474;           &#9500;&#9472;&#9472; bitmap_scale.mod
&#9474;           &#9500;&#9472;&#9472; blocklist.mod
&#9474;           &#9500;&#9472;&#9472; boot.mod
&#9474;           &#9500;&#9472;&#9472; bsd.mod
&#9474;           &#9500;&#9472;&#9472; btrfs.mod
&#9474;           &#9500;&#9472;&#9472; bufio.mod
&#9474;           &#9500;&#9472;&#9472; cat.mod
&#9474;           &#9500;&#9472;&#9472; cbfs.mod
&#9474;           &#9500;&#9472;&#9472; cbls.mod
&#9474;           &#9500;&#9472;&#9472; cbmemc.mod
&#9474;           &#9500;&#9472;&#9472; cbtable.mod
&#9474;           &#9500;&#9472;&#9472; cbtime.mod
&#9474;           &#9500;&#9472;&#9472; chain.mod
&#9474;           &#9500;&#9472;&#9472; cmdline_cat_test.mod
&#9474;           &#9500;&#9472;&#9472; cmp.mod
&#9474;           &#9500;&#9472;&#9472; command.lst
&#9474;           &#9500;&#9472;&#9472; cpio_be.mod
&#9474;           &#9500;&#9472;&#9472; cpio.mod
&#9474;           &#9500;&#9472;&#9472; cpuid.mod
&#9474;           &#9500;&#9472;&#9472; crc64.mod
&#9474;           &#9500;&#9472;&#9472; cryptodisk.mod
&#9474;           &#9500;&#9472;&#9472; crypto.lst
&#9474;           &#9500;&#9472;&#9472; crypto.mod
&#9474;           &#9500;&#9472;&#9472; cs5536.mod
&#9474;           &#9500;&#9472;&#9472; datehook.mod
&#9474;           &#9500;&#9472;&#9472; date.mod
&#9474;           &#9500;&#9472;&#9472; datetime.mod
&#9474;           &#9500;&#9472;&#9472; diskfilter.mod
&#9474;           &#9500;&#9472;&#9472; disk.mod
&#9474;           &#9500;&#9472;&#9472; div_test.mod
&#9474;           &#9500;&#9472;&#9472; dm_nv.mod
&#9474;           &#9500;&#9472;&#9472; echo.mod
&#9474;           &#9500;&#9472;&#9472; efifwsetup.mod
&#9474;           &#9500;&#9472;&#9472; efi_gop.mod
&#9474;           &#9500;&#9472;&#9472; efinet.mod
&#9474;           &#9500;&#9472;&#9472; efi_uga.mod
&#9474;           &#9500;&#9472;&#9472; ehci.mod
&#9474;           &#9500;&#9472;&#9472; elf.mod
&#9474;           &#9500;&#9472;&#9472; eval.mod
&#9474;           &#9500;&#9472;&#9472; exfat.mod
&#9474;           &#9500;&#9472;&#9472; exfctest.mod
&#9474;           &#9500;&#9472;&#9472; ext2.mod
&#9474;           &#9500;&#9472;&#9472; fat.mod
&#9474;           &#9500;&#9472;&#9472; file.mod
&#9474;           &#9500;&#9472;&#9472; fixvideo.mod
&#9474;           &#9500;&#9472;&#9472; font.mod
&#9474;           &#9500;&#9472;&#9472; fs.lst
&#9474;           &#9500;&#9472;&#9472; gcry_arcfour.mod
&#9474;           &#9500;&#9472;&#9472; gcry_blowfish.mod
&#9474;           &#9500;&#9472;&#9472; gcry_camellia.mod
&#9474;           &#9500;&#9472;&#9472; gcry_cast5.mod
&#9474;           &#9500;&#9472;&#9472; gcry_crc.mod
&#9474;           &#9500;&#9472;&#9472; gcry_des.mod
&#9474;           &#9500;&#9472;&#9472; gcry_dsa.mod
&#9474;           &#9500;&#9472;&#9472; gcry_idea.mod
&#9474;           &#9500;&#9472;&#9472; gcry_md4.mod
&#9474;           &#9500;&#9472;&#9472; gcry_md5.mod
&#9474;           &#9500;&#9472;&#9472; gcry_rfc2268.mod
&#9474;           &#9500;&#9472;&#9472; gcry_rijndael.mod
&#9474;           &#9500;&#9472;&#9472; gcry_rmd160.mod
&#9474;           &#9500;&#9472;&#9472; gcry_rsa.mod
&#9474;           &#9500;&#9472;&#9472; gcry_seed.mod
&#9474;           &#9500;&#9472;&#9472; gcry_serpent.mod
&#9474;           &#9500;&#9472;&#9472; gcry_sha1.mod
&#9474;           &#9500;&#9472;&#9472; gcry_sha256.mod
&#9474;           &#9500;&#9472;&#9472; gcry_sha512.mod
&#9474;           &#9500;&#9472;&#9472; gcry_tiger.mod
&#9474;           &#9500;&#9472;&#9472; gcry_twofish.mod
&#9474;           &#9500;&#9472;&#9472; gcry_whirlpool.mod
&#9474;           &#9500;&#9472;&#9472; geli.mod
&#9474;           &#9500;&#9472;&#9472; gettext.mod
&#9474;           &#9500;&#9472;&#9472; gfxmenu.mod
&#9474;           &#9500;&#9472;&#9472; gfxterm_background.mod
&#9474;           &#9500;&#9472;&#9472; gfxterm_menu.mod
&#9474;           &#9500;&#9472;&#9472; gfxterm.mod
&#9474;           &#9500;&#9472;&#9472; gptsync.mod
&#9474;           &#9500;&#9472;&#9472; grub.cfg
&#9474;           &#9500;&#9472;&#9472; gzio.mod
&#9474;           &#9500;&#9472;&#9472; halt.mod
&#9474;           &#9500;&#9472;&#9472; hashsum.mod
&#9474;           &#9500;&#9472;&#9472; hdparm.mod
&#9474;           &#9500;&#9472;&#9472; help.mod
&#9474;           &#9500;&#9472;&#9472; hexdump.mod
&#9474;           &#9500;&#9472;&#9472; hfs.mod
&#9474;           &#9500;&#9472;&#9472; hfspluscomp.mod
&#9474;           &#9500;&#9472;&#9472; hfsplus.mod
&#9474;           &#9500;&#9472;&#9472; http.mod
&#9474;           &#9500;&#9472;&#9472; iorw.mod
&#9474;           &#9500;&#9472;&#9472; jfs.mod
&#9474;           &#9500;&#9472;&#9472; jpeg.mod
&#9474;           &#9500;&#9472;&#9472; keylayouts.mod
&#9474;           &#9500;&#9472;&#9472; keystatus.mod
&#9474;           &#9500;&#9472;&#9472; ldm.mod
&#9474;           &#9500;&#9472;&#9472; legacycfg.mod
&#9474;           &#9500;&#9472;&#9472; legacy_password_test.mod
&#9474;           &#9500;&#9472;&#9472; linux16.mod
&#9474;           &#9500;&#9472;&#9472; linuxefi.mod
&#9474;           &#9500;&#9472;&#9472; linux.mod
&#9474;           &#9500;&#9472;&#9472; loadbios.mod
&#9474;           &#9500;&#9472;&#9472; loadenv.mod
&#9474;           &#9500;&#9472;&#9472; loopback.mod
&#9474;           &#9500;&#9472;&#9472; lsacpi.mod
&#9474;           &#9500;&#9472;&#9472; lsefimmap.mod
&#9474;           &#9500;&#9472;&#9472; lsefi.mod
&#9474;           &#9500;&#9472;&#9472; lsefisystab.mod
&#9474;           &#9500;&#9472;&#9472; lsmmap.mod
&#9474;           &#9500;&#9472;&#9472; ls.mod
&#9474;           &#9500;&#9472;&#9472; lspci.mod
&#9474;           &#9500;&#9472;&#9472; lssal.mod
&#9474;           &#9500;&#9472;&#9472; luks.mod
&#9474;           &#9500;&#9472;&#9472; lvm.mod
&#9474;           &#9500;&#9472;&#9472; lzopio.mod
&#9474;           &#9500;&#9472;&#9472; macbless.mod
&#9474;           &#9500;&#9472;&#9472; macho.mod
&#9474;           &#9500;&#9472;&#9472; mdraid09_be.mod
&#9474;           &#9500;&#9472;&#9472; mdraid09.mod
&#9474;           &#9500;&#9472;&#9472; mdraid1x.mod
&#9474;           &#9500;&#9472;&#9472; memrw.mod
&#9474;           &#9500;&#9472;&#9472; minicmd.mod
&#9474;           &#9500;&#9472;&#9472; minix2_be.mod
&#9474;           &#9500;&#9472;&#9472; minix2.mod
&#9474;           &#9500;&#9472;&#9472; minix3_be.mod
&#9474;           &#9500;&#9472;&#9472; minix3.mod
&#9474;           &#9500;&#9472;&#9472; minix_be.mod
&#9474;           &#9500;&#9472;&#9472; mmap.mod
&#9474;           &#9500;&#9472;&#9472; moddep.lst
&#9474;           &#9500;&#9472;&#9472; morse.mod
&#9474;           &#9500;&#9472;&#9472; mpi.mod
&#9474;           &#9500;&#9472;&#9472; msdospart.mod
&#9474;           &#9500;&#9472;&#9472; multiboot2.mod
&#9474;           &#9500;&#9472;&#9472; multiboot.mod
&#9474;           &#9500;&#9472;&#9472; nativedisk.mod
&#9474;           &#9500;&#9472;&#9472; net.mod
&#9474;           &#9500;&#9472;&#9472; newc.mod
&#9474;           &#9500;&#9472;&#9472; ntfscomp.mod
&#9474;           &#9500;&#9472;&#9472; ntfs.mod
&#9474;           &#9500;&#9472;&#9472; odc.mod
&#9474;           &#9500;&#9472;&#9472; offsetio.mod
&#9474;           &#9500;&#9472;&#9472; ohci.mod
&#9474;           &#9500;&#9472;&#9472; part_acorn.mod
&#9474;           &#9500;&#9472;&#9472; part_amiga.mod
&#9474;           &#9500;&#9472;&#9472; part_apple.mod
&#9474;           &#9500;&#9472;&#9472; part_bsd.mod
&#9474;           &#9500;&#9472;&#9472; part_dfly.mod
&#9474;           &#9500;&#9472;&#9472; part_dvh.mod
&#9474;           &#9500;&#9472;&#9472; part_gpt.mod
&#9474;           &#9500;&#9472;&#9472; partmap.lst
&#9474;           &#9500;&#9472;&#9472; part_msdos.mod
&#9474;           &#9500;&#9472;&#9472; part_plan.mod
&#9474;           &#9500;&#9472;&#9472; part_sun.mod
&#9474;           &#9500;&#9472;&#9472; part_sunpc.mod
&#9474;           &#9500;&#9472;&#9472; parttool.lst
&#9474;           &#9500;&#9472;&#9472; parttool.mod
&#9474;           &#9500;&#9472;&#9472; password.mod
&#9474;           &#9500;&#9472;&#9472; password_pbkdf2.mod
&#9474;           &#9500;&#9472;&#9472; pata.mod
&#9474;           &#9500;&#9472;&#9472; pbkdf2.mod
&#9474;           &#9500;&#9472;&#9472; pbkdf2_test.mod
&#9474;           &#9500;&#9472;&#9472; pcidump.mod
&#9474;           &#9500;&#9472;&#9472; play.mod
&#9474;           &#9500;&#9472;&#9472; png.mod
&#9474;           &#9500;&#9472;&#9472; priority_queue.mod
&#9474;           &#9500;&#9472;&#9472; probe.mod
&#9474;           &#9500;&#9472;&#9472; procfs.mod
&#9474;           &#9500;&#9472;&#9472; progress.mod
&#9474;           &#9500;&#9472;&#9472; raid5rec.mod
&#9474;           &#9500;&#9472;&#9472; raid6rec.mod
&#9474;           &#9500;&#9472;&#9472; read.mod
&#9474;           &#9500;&#9472;&#9472; reboot.mod
&#9474;           &#9500;&#9472;&#9472; regexp.mod
&#9474;           &#9500;&#9472;&#9472; reiserfs.mod
&#9474;           &#9500;&#9472;&#9472; relocator.mod
&#9474;           &#9500;&#9472;&#9472; romfs.mod
&#9474;           &#9500;&#9472;&#9472; scsi.mod
&#9474;           &#9500;&#9472;&#9472; serial.mod
&#9474;           &#9500;&#9472;&#9472; setjmp.mod
&#9474;           &#9500;&#9472;&#9472; setjmp_test.mod
&#9474;           &#9500;&#9472;&#9472; setpci.mod
&#9474;           &#9500;&#9472;&#9472; signature_test.mod
&#9474;           &#9500;&#9472;&#9472; sleep.mod
&#9474;           &#9500;&#9472;&#9472; sleep_test.mod
&#9474;           &#9500;&#9472;&#9472; spkmodem.mod
&#9474;           &#9500;&#9472;&#9472; squash4.mod
&#9474;           &#9500;&#9472;&#9472; syslinuxcfg.mod
&#9474;           &#9500;&#9472;&#9472; terminal.lst
&#9474;           &#9500;&#9472;&#9472; terminal.mod
&#9474;           &#9500;&#9472;&#9472; terminfo.mod
&#9474;           &#9500;&#9472;&#9472; test_blockarg.mod
&#9474;           &#9500;&#9472;&#9472; testload.mod
&#9474;           &#9500;&#9472;&#9472; test.mod
&#9474;           &#9500;&#9472;&#9472; testspeed.mod
&#9474;           &#9500;&#9472;&#9472; tftp.mod
&#9474;           &#9500;&#9472;&#9472; tga.mod
&#9474;           &#9500;&#9472;&#9472; time.mod
&#9474;           &#9500;&#9472;&#9472; trig.mod
&#9474;           &#9500;&#9472;&#9472; tr.mod
&#9474;           &#9500;&#9472;&#9472; true.mod
&#9474;           &#9500;&#9472;&#9472; udf.mod
&#9474;           &#9500;&#9472;&#9472; ufs1_be.mod
&#9474;           &#9500;&#9472;&#9472; ufs1.mod
&#9474;           &#9500;&#9472;&#9472; ufs2.mod
&#9474;           &#9500;&#9472;&#9472; uhci.mod
&#9474;           &#9500;&#9472;&#9472; usb_keyboard.mod
&#9474;           &#9500;&#9472;&#9472; usb.mod
&#9474;           &#9500;&#9472;&#9472; usbms.mod
&#9474;           &#9500;&#9472;&#9472; usbserial_common.mod
&#9474;           &#9500;&#9472;&#9472; usbserial_ftdi.mod
&#9474;           &#9500;&#9472;&#9472; usbserial_pl2303.mod
&#9474;           &#9500;&#9472;&#9472; usbserial_usbdebug.mod
&#9474;           &#9500;&#9472;&#9472; usbtest.mod
&#9474;           &#9500;&#9472;&#9472; verify.mod
&#9474;           &#9500;&#9472;&#9472; video_bochs.mod
&#9474;           &#9500;&#9472;&#9472; video_cirrus.mod
&#9474;           &#9500;&#9472;&#9472; video_colors.mod
&#9474;           &#9500;&#9472;&#9472; video_fb.mod
&#9474;           &#9500;&#9472;&#9472; videoinfo.mod
&#9474;           &#9500;&#9472;&#9472; video.lst
&#9474;           &#9500;&#9472;&#9472; video.mod
&#9474;           &#9500;&#9472;&#9472; videotest_checksum.mod
&#9474;           &#9500;&#9472;&#9472; videotest.mod
&#9474;           &#9500;&#9472;&#9472; xfs.mod
&#9474;           &#9500;&#9472;&#9472; xnu.mod
&#9474;           &#9500;&#9472;&#9472; xnu_uuid.mod
&#9474;           &#9500;&#9472;&#9472; xnu_uuid_test.mod
&#9474;           &#9500;&#9472;&#9472; xzio.mod
&#9474;           &#9492;&#9472;&#9472; zfscrypt.mod
&#9500;&#9472;&#9472; boot.cat
&#9500;&#9472;&#9472; exithelp.cfg
&#9500;&#9472;&#9472; f10.txt
&#9500;&#9472;&#9472; f1.txt
&#9500;&#9472;&#9472; f2.txt
&#9500;&#9472;&#9472; f3.txt
&#9500;&#9472;&#9472; f4.txt
&#9500;&#9472;&#9472; f5.txt
&#9500;&#9472;&#9472; f6.txt
&#9500;&#9472;&#9472; f7.txt
&#9500;&#9472;&#9472; f8.txt
&#9500;&#9472;&#9472; f9.txt
&#9500;&#9472;&#9472; initrd.gz
&#9500;&#9472;&#9472; isolinux.bin
&#9500;&#9472;&#9472; isolinux.cfg
&#9500;&#9472;&#9472; linux
&#9500;&#9472;&#9472; menu.cfg
&#9500;&#9472;&#9472; prompt.cfg
&#9500;&#9472;&#9472; rqtxt.cfg
&#9500;&#9472;&#9472; splash.png
&#9500;&#9472;&#9472; stdmenu.cfg
&#9500;&#9472;&#9472; txt.cfg
&#9492;&#9472;&#9472; vesamenu.c32

3 directories, 265 files

```
here is my grub2 confg file
[http://pastebin.com/TisvBb0a](http://pastebin.com/TisvBb0a)
i need help with line 63

---

### Post by yancek on 2014-10-23
The only way to find out is to try copying the iso file to the disk and try the loopback method.  If that doesn't work, you can extract it and copy to the flash and boot it that way.  Two things you will need to change from your other entries, the kernel file is named 'linux' rather than 'vmlinuz' as your other loopback entries and the initrd is 'initrd.gz' and not 'initrd.lz'.  If you don't get those right, I can guarantee it won't boot.  Also, I don't see a casper directory in your diagram so that part of the boot entry would have to be changed.  Post the contents of the isolinux.cfg or text.cfg file, whichever actually has the menuentries.

---

### Post by pqwoerituytrueiwoq on 2014-10-23
mini.iso/menu.cfg
```
menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include txt.cfg
include gtk.cfg
menu begin advanced
    menu title Advanced options
    include stdmenu.cfg
    label mainmenu
        menu label ^Back..
        menu exit
    include adtxt.cfg
    include adgtk.cfg
menu end
label help
    menu label ^Help
    text help
   Display help screens; type 'menu' at boot prompt to return to this menu
    endtext
    config prompt.cfg

```
mini.iso/txt.cfg
```
default install
label install
    menu label ^Install
    menu default
    kernel linux
    append vga=788 initrd=initrd.gz -- quiet 
label cli
    menu label ^Command-line install
    kernel linux
    append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=788 initrd=initrd.gz -- quiet 

```
/mini.iso/boot/grub/grub.cfg
```

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install" {
    set gfxpayload=keep
    linux    /linux -- quiet
    initrd    /initrd.gz
}

menuentry "Command-line install" {
    set gfxpayload=keep
    linux    /linux tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false -- quiet
    initrd    /initrd.gz
}

menuentry "Expert install" {
    set gfxpayload=keep
    linux    /linux priority=low --
    initrd    /initrd.gz
}

menuentry "Command-line expert install" {
    set gfxpayload=keep
    linux    /linux tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low --
    initrd    /initrd.gz
}

menuentry "Rescue mode" {
    set gfxpayload=keep
    linux    /linux rescue/enable=true -- quiet
    initrd    /initrd.gz
}

```
i fixed the file ext in my boot file but it told me to load the kernel 1st

---

### Post by pqwoerituytrueiwoq on 2014-10-23
This one works :)
```
    menuentry "Ubuntu mini 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/mini-amd64.iso"
        loopback loop $isofile
        linux (loop)/linux
        initrd (loop)/initrd.gz
    }
```

---

