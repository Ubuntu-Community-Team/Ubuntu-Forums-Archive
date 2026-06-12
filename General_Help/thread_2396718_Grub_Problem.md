---
title: "Grub Problem"
date: 2018-07-19
forum: General Help
---

### Post by gus_zernial on 2018-07-19
I have Kubuntu 18.04 on a UEFI BIOS intel i7 64-bit system. There's three kernels on the system, and currently the only one that boots correctly is 4.15.0-23-generic (see /boot/grub/grub.cfg below - it's menuentry 'Ubuntu, with Linux 4.15.0-23-generic'). I also put my /etc/default/grub below.

For now, what I want is to show the grub menu for 10 seconds, and absent intervention, automatically boot 4.15.0-23-generic by default. But it selects EFI/BOOT/bkpbootx64.efi as default and hangs (no boot). Or, I can select "Advanced" and select 4.15.0-23-generic, and it will boot that correctly.

Can someone look at my /etc/default/grub and see if it's correct? Or, is there another possible culprit?

Thx, Gus


```
$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=2
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="console=tty1 console=ttyS0 panic=-1"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.alpha_support=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

--------------------------------------------
```

```
/boot/grub/grub.cfg

.
.
.
etc,etc, then
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
        else
          search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
        fi
        linux   /boot/vmlinuz-4.15.0-24-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro  console=tty1 console=ttyS0 panic=-1
        initrd  /boot/initrd.img-4.15.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
        menuentry 'Ubuntu, with Linux 4.15.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-24-generic-advanced-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.15.0-24-generic ...'
                linux   /boot/vmlinuz-4.15.0-24-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro  console=tty1 console=ttyS0 panic=-1
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.15.0-24-generic
        }
        menuentry 'Ubuntu, with Linux 4.15.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-24-generic-recovery-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.15.0-24-generic ...'
                linux   /boot/vmlinuz-4.15.0-24-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro recovery nomodeset 
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.15.0-24-generic
        }
        menuentry 'Ubuntu, with Linux 4.15.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-23-generic-advanced-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.15.0-23-generic ...'
                linux   /boot/vmlinuz-4.15.0-23-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro  console=tty1 console=ttyS0 panic=-1
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.15.0-23-generic
        }
        menuentry 'Ubuntu, with Linux 4.15.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-23-generic-recovery-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.15.0-23-generic ...'
                linux   /boot/vmlinuz-4.15.0-23-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro recovery nomodeset 
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.15.0-23-generic
        }
        menuentry 'Ubuntu, with Linux 4.14.15-041415-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.14.15-041415-generic-advanced-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.14.15-041415-generic ...'
                linux   /boot/vmlinuz-4.14.15-041415-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro  console=tty1 console=ttyS0 panic=-1
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.14.15-041415-generic
        }
        menuentry 'Ubuntu, with Linux 4.14.15-041415-generic (recovery mode)' --class ubuntu --clasEFI/BOOT/bkpbootx64.efis gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.14.15-041415-generic-recovery-8e3d59ea-1204-4ffb-baef-1b8790e5393b' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root  8e3d59ea-1204-4ffb-baef-1b8790e5393b
                else
                  search --no-floppy --fs-uuid --set=root 8e3d59ea-1204-4ffb-baef-1b8790e5393b
                fi
                echo    'Loading Linux 4.14.15-041415-generic ...'
                linux   /boot/vmlinuz-4.14.15-041415-generic root=UUID=8e3d59ea-1204-4ffb-baef-1b8790e5393b ro recovery nomodeset 
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.14.15-041415-generic
        }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/BOOT/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 260A-EE4B
chainloader (${root})/EFI/BOOT/bkpbootx64.efi
}

menuentry "EFI/BOOT/fbx64.efi" {
search --fs-uuid --no-floppy --set=root 260A-EE4B
chainloader (${root})/EFI/BOOT/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 260A-EE4B
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 260A-EE4B
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
.
.
.
etc.
```

---

### Post by oldfred on 2018-07-19
Please use code tags for longer or terminal output. Easy to add with Forum's advanced editor & # icon.

If UEFI, initial boot is set by UEFI.
Post this:
sudo efibootmgr -v

You can usually change boot order with efibootmgr. See this and -o option:
man efibootmgr

       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

A few systems do not seem to accept the efibootmgr entries?
Then you have to use UEFI to change boot order. 
And if an Acer you have to first set "trust". Some other brands need other work arounds.
What brand/model system?

---

### Post by Impavidus on 2018-07-20
You could also remove kernel 4.15.0-24. Its metapackages has been removed from the repositories because of problems with this kernel, so no more systems should automatically attempt to upgrade to -24. Downgrade the metapackages on your system (probably linux-generic, linux-image-generic and linux-headers-generic, but check with dpkg --list linux*) to 4.15.0.23, which is the latest version in the repositories, then you can remove kernel -24, then kernel -23 should boot automatically. The easiest way to do this is using the synaptic package manager.

The bugs in -24 don't affect me, so I didn't try this myself.

---

### Post by kazakore on 2018-07-20
I've noticed they seem to have removed -24 from the repos but not set -23 to replace it. I run Studio hence the lowlatency version of the kernal

```
$ apt-cache policy linux-image-lowlatency
linux-image-lowlatency:
  Installed: 4.15.0.24.26
  Candidate: 4.15.0.24.26
  Version table:
 *** 4.15.0.24.26 100
        100 /var/lib/dpkg/status
     4.15.0.23.25 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     4.15.0.20.23 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

As this issue doesn't affect me I've not worried about this but thought it seems rather weird!....

---

### Post by gus_zernial on 2018-07-20
Current efibootmgr -v ......

$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0004,0003
Boot0001* ubuntu        HD(1,GPT,ec6708eb-c22c-4e48-867f-9e5a584f9d7b,0x800,0x96000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* Hard Drive    BBS(HD,,0x0)..GO..NO........o.W.D.C. .W.D.2.0.0.3.F.Z.E.X.-.0.0.Z.4.S.A.0....................A.....................D.2.0.0.3.F.Z.E.X.-.0.0.Z.4.S.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.1.C.0.P.0.E.J.J.C.7.
Boot0004* CD/DVD Drive  BBS(CDROM,,0x0)..GO..NO........I.P.I.O.N.E.E.R. .B.D.-.R.W. . . .B.D.R.-.2.0.6.D....................A..............

---

### Post by oldfred on 2018-07-20
UEFI is booting Ubuntu as first in BootOrder. 

Because you have 25_custom that resets the order in grub.cfg. So then setting boot to default to 2 then may not boot the choice you want. You may have to experiment with this setting, normally 0 is the default.
GRUB_DEFAULT=2

And when a new kernel is downloaded, you will not to reset to 0.

---

### Post by Impavidus on 2018-07-21
Kernel 4.15.0-29 is now in the repositories, so it should be possible to simply upgrade and undo any other changes you made (assuming -29 works for you).

---

