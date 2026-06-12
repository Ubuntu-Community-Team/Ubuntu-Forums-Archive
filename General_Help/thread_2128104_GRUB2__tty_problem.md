---
title: "GRUB2 / tty problem"
date: 2013-03-22
forum: General Help
---

### Post by thyriel on 2013-03-22
Hi,

i would need some help sorting a problem with GRUB2 and tty not working.
I have two Kubuntu Versions installed (and Windows):
12.10 on /dev/sda3
13.04 on /dev/sdb5

Somehow during installing 13.04 (which was last installed) i where unable to install grub2 correctly, i tried with updating installer first and all variants of where to install bootloader, but it did always quit with a "grub-update" error.

So i just ignored that. After first reboot grub2 was messed up and kicked me to rescue console.
I was able to boot 12.10 manually from the rescue console. So i then did a "grub-update" after it was loaded. All three OS detected correctly and grub2 working again.

Later i mentioned that the tty (ctrl+alt+F1 to F6) on 13.04 is not working (black screen). Its definitly a screen only problem. When i just enter username + pw and then startx its starting to loading X and poping up an GDK error, closing X again leaving me with a blank screen again.

After some research on the net i think it has something to do with the grub vesa settings not being correctly for 13.04.
Whats also strange is that bootloader in 13.04 is not shown, it just runs a lot of console commands but with minimum screen resolution (looking like old MSDOS back in the 90s)

I then tryed to fix that from within 13.04, but it seems the /boot is messed up.
If i change something there in /etc/default/grub like setting GRUB_DEFAULT to a different value, and update-grub its not changing anything.
If i do the same in 12.10 its working.

My guess is that the /boot from 12.10 is the "active" one, and the /boot from 13.04 is inactive and not used at all.

So how i can i correct that behavior at best ?

/etc/default/grub from 12.10 is:
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

```

/boot/grub/grub.cfg (only relevant parts, first the working ubuntu and second the not correctly working raring ringtail)
```

menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-48dc6f23-13bf-43cb-b13a-9e845a25acca' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  48dc6f23-13bf-43cb-b13a-9e845a25acca
    else
      search --no-floppy --fs-uuid --set=root 48dc6f23-13bf-43cb-b13a-9e845a25acca
    fi
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=48dc6f23-13bf-43cb-b13a-9e845a25acca ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-25-generic
}

menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-812426bd-d224-4608-97d3-714cfcec2ae8' {    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  812426bd-d224-4608-97d3-714cfcec2ae8
    else
      search --no-floppy --fs-uuid --set=root 812426bd-d224-4608-97d3-714cfcec2ae8
    fi
    linux /boot/vmlinuz-3.8.0-13-generic root=UUID=812426bd-d224-4608-97d3-714cfcec2ae8 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.8.0-13-generic
}


```

---

