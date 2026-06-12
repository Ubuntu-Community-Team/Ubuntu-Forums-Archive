---
title: "Where has my Ubuntu splash screen gone?"
date: 2013-02-25
forum: General Help
---

### Post by Ahari on 2013-02-25
Hi all!

I am totally new to forums and Ubuntu, so please forgive any indiscretions!

I am running Ubuntu 12.04 on an old P4 for my mother in law. The hard drive crashed. I recovered the installation to a new 500GB hdd using a Redo Backup image I had. It would not boot, so I fixed the booting with Boot Repair by booting from an Ubuntu CD. Now it boots - yay!

I then updated the Grub to Grub 2.00. 

My problem is that the default Ubuntu splash screen is gone and instead I get the Grub menu and a bunch of technical stuff scrolling up the screen. I just want it to boot with the simple Ubuntu splash screen that it used to have. How do I get it back?

I need someone to hold my hand on this as I am not familiar with Ubuntu at all. I have tried various things I found by Googling, but nothing works! I have spent too much time trying to get this to work - it should be simple, but I just can't get it right!!

Ready to just give up...

Please help me! I find Ubuntu very confusing as I am only familiar with windows!

---

### Post by matt_symes on 2013-02-25
Hi

Post into Ubuntu, open a terminal and type

```
cat /proc/cmdline
```

Post the output back here.

Kind regards

---

### Post by Ahari on 2013-02-25
Hi,

Thanks for the reply.

The result is:

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro

```

Hope I did it right!

---

### Post by matt_symes on 2013-02-25
Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```

Enter your passwoprd.  It will not be echoed to the screen.

Look for the line that contains
```
GRUB_CMDLINE_LINUX_DEFAULT=
```

and add quiet and splash as so.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Press ctrl + o to save the file and ctrl + x to exit

Then type
```

sudo update-grub
```

Once finished

```
sudo reboot
```

Kind regards

---

### Post by Ahari on 2013-02-25
Hi,

Thanks. I did exactly as you said, but it still shows the Grub menu, etc...!
:(

---

### Post by matt_symes on 2013-02-25
Hi

Yes it will still display the grub menu to allow you to pick a kernel (although that can be changed)  but you should get a splash screen.

Can you repost 

```
cat /proc/cmdline
```Kind regards

---

### Post by Ahari on 2013-02-25
Here is the result:
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro

```

No splash screen appeared on reboot.

---

### Post by matt_symes on 2013-02-25
Hi

something went wrong with what you did.

Take a look at mine

```
matthew-S206:/home/matthew % cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-030800rc7-generic root=UUID=985600e2-5d29-4530-ad2e-99d1acfd0ab9 ro [COLOR=Red]quiet splash[/COLOR] acpi_backlight=vendor vt.handoff=7
matthew-S206:/home/matthew % 
```You need that in your command line. Scroll and you will see what i mean.

Please post the output of

```
cat /etc/default/grub
```Kind regards

---

### Post by Ahari on 2013-02-25
Here is the output:

```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="1"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="010"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"
GRUB_CMDLINE_LINUX_DEFAULT=""

```

I don't know what I could have done wrong?  I followed what you said exactly and used copy and paste.

Thanks for all your patient help - I find this very bewildering and really have no idea what I am doing! I'm just blindly following what you say!! I am trying to learn at the same time though not a lot is "sticking" at the moment....

---

### Post by matt_symes on 2013-02-25
Hi

> I don't know what I could have done wrong?  I followed what you said exactly and used copy and paste.

Nor am i. I am run those commands loads to times to remove and add the splash screen.

can you run

```
sudo update-grub
```

Post the output back here.

Kind regards

---

### Post by Ahari on 2013-02-25
Hi,

I am glad that it's not just me that is confused! If a Ubuntu veteran such as yourself  is confused, imagine how I feel!

Your help is truly appreciated.

Here is the output as requested:

```
miriam@PC1-MIRIAM:~$ sudo update-grub
[sudo] password for miriam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
done
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

This may be because you are using grub 2. I am just checking.

If you reboot you get no splash screen and your command parameters dont change ?

EDIT: No i'm using grub 2

```
matthew-S206:/home/matthew % dpkg -l | grep -i grub-pc
ii  grub-pc                                        2.00-7ubuntu11                            amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                    2.00-7ubuntu11                            amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
matthew-S206:/home/matthew %
```

Kind regards

---

### Post by Ahari on 2013-02-25
Yes, I am using Grub 2.00. I updated to it when I could not get the splash screen to work on 1.98 and then 1.99!

I have not seen a splash screen since before the hdd crashed and I restored the Redo Backup image to the new hdd.

I don't know what you mean by "command parameters"?  (noob!)

---

### Post by Ahari on 2013-02-25
After reading you edit above, I ran the following:

```
miriam@PC1-MIRIAM:~$ dpkg -l | grep -i grub-pc
ii  grub-pc                                1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                            1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
miriam@PC1-MIRIAM:~$ 

```

Confused! It says 2.00 on boot screen and 1.99-21 (whatever that is) version 2 here?:confused:

---

### Post by matt_symes on 2013-02-25
Hi

can you post the output of the file.

```
gedit /boot/grub/grub.cfg 
```

Kind regards

---

### Post by Ahari on 2013-02-25
Your code did not work, so I added sudo to the front and it worked - I may be starting to get it (vaguely!!) Just kicking my shins on the furniture in the dark too often!! ;)

Here are the file contents:

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /usr/etc/grub.d and settings from /usr/etc/default/grub
#

### BEGIN /usr/etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
else
  search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_ZA
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /usr/etc/grub.d/00_header ###

### BEGIN /usr/etc/grub.d/10_linux ###
menuentry 'GNU/Linux' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d8104884-5b62-4a2c-9078-debaff0b3310' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
    else
      search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
    fi
    echo    'Loading Linux 3.2.0-38-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-generic-pae
}
submenu 'Advanced options for GNU/Linux' $menuentry_id_option 'gnulinux-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
    menuentry 'GNU/Linux, with Linux 3.2.0-38-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-38-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-38-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-38-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-38-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-38-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-38-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-38-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-37-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-37-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-37-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-37-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-37-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-37-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-37-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-37-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-36-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-36-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-36-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-36-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-36-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-36-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-36-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-36-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-35-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-35-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-35-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-35-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-29-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-29-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-27-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-27-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-27-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-27-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-26-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-26-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-26-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-26-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-25-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-25-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-25-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-25-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-24-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-24-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-24-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-24-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic-pae
    }
}

### END /usr/etc/grub.d/10_linux ###

### BEGIN /usr/etc/grub.d/20_linux_xen ###

### END /usr/etc/grub.d/20_linux_xen ###

### BEGIN /usr/etc/grub.d/30_os-prober ###
### END /usr/etc/grub.d/30_os-prober ###

### BEGIN /usr/etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /usr/etc/grub.d/40_custom ###

### BEGIN /usr/etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /usr/etc/grub.d/41_custom ###
```

---

### Post by Ahari on 2013-02-25
It's all Greek to me, but there does seem to be an awful lot of "menuentry" items in there!

---

### Post by schragge on 2013-02-25
You have an extra GRUB_CMDLINE_LINUX_DEFAULT="" line at the end of your */etc/default/grub* that overrides your change. Remove it:
```
sudo sed -i '/^GRUB_CMDLINE_LINUX_DEFAULT=""/' /etc/default/grub
```
then
```

sudo update-grub

```

---

### Post by matt_symes on 2013-02-25
Hi

Your grub.cfg file is not being updated. we can look inti that a bit later but first a test```


sudo nano /boot/grub/grub.cfg
```Look for this line (note the number 3.2.0-38) 

```
linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro       echo    'Loading initial ramdisk ...'
```and change to this

```
linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 [COLOR=Red]quiet splash[/COLOR] ro       echo    'Loading initial ramdisk ...'
```double check you have done it right.

ctrl + o to save and ctrl + x to exit.

```
sudo reboot
```Don't touch the PC when the grub menu appears. Just let it boot.

Do you get a splash screen now. This not a long term fix btw.

Kind regards

---

### Post by Ahari on 2013-02-25
I wonder where that came from?

Deleted the offending line.

```
miriam@PC1-MIRIAM:~$ sudo nano /etc/default/grub
[sudo] password for miriam: 
miriam@PC1-MIRIAM:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
done
miriam@PC1-MIRIAM:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro
miriam@PC1-MIRIAM:~$ 

```

Still no "quiet splash" at the end of the last command though...

---

### Post by schragge on 2013-02-25
Please reboot now

---

### Post by matt_symes on 2013-02-25
Hi

You were not meant to sudo update-grub after editing the file by hand. 

That's not what i was trying to prove. Can you do it again and just do the reboot please. Don't even check the kernel.

You have problems with grub and i am trying to find out what. Please follow my instruction :)

Kind regards

---

### Post by schragge on 2013-02-25
@**matt_symes**.
No, Matt. It's simpler than this. Please read [post=12529892]my last post[/post] on the previous page.

---

### Post by matt_symes on 2013-02-25
Hi

Blimey. Another good call. 

I did not even check that low down in the file. I must pay more attention :D

I was going to check permissions next.

Kind regards

---

### Post by Ahari on 2013-02-25
Sorry for the delay in replying - family commitments!

Okay, I did as you asked and I got the splash screen! Yay!

What now?

---

### Post by matt_symes on 2013-02-25
Hi

You can have a picture on the grub screen ? You can hide the grub menu altogether ?

Kind regards

---

### Post by Ahari on 2013-02-25
Oops! I did as you said, matt_symes and I got the Grub screen followed by the splash screen. Then I tried what schragge said and the splash screen is gone again!

What have I done now? My apologies for jumping the gun earlier!

---

### Post by matt_symes on 2013-02-25
Hi

Thats a shame i thought this was fixed. Please post the output of

```
cat /etc/default/grub
```

Lets see where we are.

Kind regards

---

### Post by Ahari on 2013-02-25
Sorry - I'm bad!! I get a bit excited when things start to work!!

Output of your last request:

```
miriam@PC1-MIRIAM:~$ sudo nano /boot/grub/grub.cfg
[sudo] password for miriam: 
miriam@PC1-MIRIAM:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="1"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="010"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

Next please run this again

```

sudo update-grub
```

the please post the output of

```
gksudo gedit /boot/grub/grub.cfg
```

Can you also post the output of

```
cat /proc/cmdline
```

Kind regards

---

### Post by Ahari on 2013-02-25
You did say it wasn't a long term fix, so I thought that I would try [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515")'s fix since you seemed excited about it! Silly me! I went and ran the command [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515") instructed for a second time and I think it deleted the next last line! 

I am a Paw Paw! I won't do anything again unless you say so!!

---

### Post by Ahari on 2013-02-25
First output:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /usr/etc/grub.d and settings from /usr/etc/default/grub
#

### BEGIN /usr/etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
else
  search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_ZA
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /usr/etc/grub.d/00_header ###

### BEGIN /usr/etc/grub.d/10_linux ###
menuentry 'GNU/Linux' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d8104884-5b62-4a2c-9078-debaff0b3310' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
    else
      search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
    fi
    echo    'Loading Linux 3.2.0-38-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-generic-pae
}
submenu 'Advanced options for GNU/Linux' $menuentry_id_option 'gnulinux-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
    menuentry 'GNU/Linux, with Linux 3.2.0-38-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-38-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-38-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-38-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-38-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-38-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-38-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-38-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-37-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-37-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-37-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-37-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-37-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-37-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-37-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-37-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-36-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-36-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-36-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-36-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-36-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-36-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-36-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-36-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-36-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-35-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-35-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-35-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-35-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-29-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-29-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-27-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-27-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-27-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-27-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-26-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-26-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-26-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-26-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-25-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-25-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-25-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-25-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-24-generic-pae' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-pae-advanced-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-24-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'GNU/Linux, with Linux 3.2.0-24-generic-pae (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-pae-recovery-d8104884-5b62-4a2c-9078-debaff0b3310' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  d8104884-5b62-4a2c-9078-debaff0b3310
        else
          search --no-floppy --fs-uuid --set=root d8104884-5b62-4a2c-9078-debaff0b3310
        fi
        echo    'Loading Linux 3.2.0-24-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic-pae
    }
}

### END /usr/etc/grub.d/10_linux ###

### BEGIN /usr/etc/grub.d/20_linux_xen ###

### END /usr/etc/grub.d/20_linux_xen ###

### BEGIN /usr/etc/grub.d/30_os-prober ###
### END /usr/etc/grub.d/30_os-prober ###

### BEGIN /usr/etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /usr/etc/grub.d/40_custom ###

### BEGIN /usr/etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /usr/etc/grub.d/41_custom ###
```

Second one:
```
miriam@PC1-MIRIAM:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic-pae root=UUID=d8104884-5b62-4a2c-9078-debaff0b3310 ro
miriam@PC1-MIRIAM:~$
```

---

### Post by matt_symes on 2013-02-25
Hi

His advice was good and was identified a problem. I'm just trying to find out where were are now.

If you could follow the steps in my last post.

We are almost there. 

You saw the splash screen because you edited the file. That's what i wanted to prove. That you could see the splash screen and you didn't have a problem there. 

We just have to make sure it's going to be permanent.

Kind regards

---

### Post by matt_symes on 2013-02-25
Hi

You ran 

```
sudo update-grub
```before posting that last file ? 

It still does not have the updates in it.

Kind regards

---

### Post by Ahari on 2013-02-25
I have done as you asked in your last post - see my last post.

I think I posted it while you were typing.

---

### Post by Ahari on 2013-02-25
> **matt_symes said:**
> Hi

You ran 

```
sudo update-grub
```before posting that last file ? 

It still does not have the updates in it.

Kind regards

Yes I did.

---

### Post by Ahari on 2013-02-25
The updates may have been lost when I ran schragge's suggestion the second time!

> You have an extra GRUB_CMDLINE_LINUX_DEFAULT="" line at the end of your */etc/default/grub* that overrides your change. Remove it:
 	Code:
 	sudo sed -i '$d' /etc/default/grub 
then
 	Code:
 	sudo update-grub


---

### Post by matt_symes on 2013-02-25
Hi

Can you run this command please in this order. I want to check the timestamps with both ls commands.

```
ls -l /boot/grub/grub.cfg
```

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

The is what update-grub calls.

```
ls -l /boot/grub/grub.cfg
```

Kind regards

---

### Post by Ahari on 2013-02-25
Lost my internet for a bit there! Sorry! South African internet can be a bit flaky! ;)

Here are the results of you last post:

```
miriam@PC1-MIRIAM:~$ ls -l /boot/grub/grub.cfg
-rw------- 1 root root 18516 Feb 25 22:01 /boot/grub/grub.cfg
miriam@PC1-MIRIAM:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
[sudo] password for miriam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
done
miriam@PC1-MIRIAM:~$ ls -l /boot/grub/grub.cfg
-rw------- 1 root root 18516 Feb 25 22:32 /boot/grub/grub.cfg
miriam@PC1-MIRIAM:~$ 

```

I have no idea what I am doing - just trusting you!! :D

---

### Post by matt_symes on 2013-02-25
Hi

And

```
grep splash /boot/grub/grub.cfg
```I expect the above command to return nothing.

What seems to be happening is that it's updating the grub.cfg file but not pulling values out from /etc/default/grub and putting them into grub.cfg. 

It should be pulling the "quiet splash" out from that file and put them into grub.cfg like you did manually.

That's why you saw the splash screen because becuase you edited the file.

I have not seen this happen before.

Kind regards

---

### Post by Ahari on 2013-02-25
I got "permission denied" so I ran it with sudo in front:

```
miriam@PC1-MIRIAM:~$ sudo grep splash /boot/grub/grub.cfg
miriam@PC1-MIRIAM:~$ 

```

You are right, nothing returned.

---

### Post by matt_symes on 2013-02-25
Hi

I know what the problem is just not why.

I will need to do some research. 

I can see nothing wrong with the file /etc/default/grub but i suspect the problem may be there especially after a mistake has already been found in it.

There is something wrong with your grub setup.

Can you post the output of 

```
ls -l /etc/default/grub
```

Kind regards

---

### Post by Ahari on 2013-02-25
Just my luck to have something that stumps an expert!! Story of my life! :)

No wonder I have been pulling my hair out!!

```
miriam@PC1-MIRIAM:~$ ls -l /etc/default/grub
-rw-r--r-- 1 root root 1254 Feb 25 21:41 /etc/default/grub
miriam@PC1-MIRIAM:~$ 

```

---

### Post by Ahari on 2013-02-25
There may be something wrong with my grub setup since I tried just about everything I could Google to fix it before I tried here in desperation!

---

### Post by Ahari on 2013-02-25
I seem to recall one of the "fixes" I tried was to add those 2 lines to the end of the file - or something like that... I just don't know any more!!

---

### Post by schragge on 2013-02-25
Miriam, can you please also post the output of
```

ls -l /etc/grub.d/

```

---

### Post by Ahari on 2013-02-25
I was just thinking regarding my earlier post:

> **Ahari said:**
> After reading you edit above, I ran the following:

```
miriam@PC1-MIRIAM:~$ dpkg -l | grep -i grub-pc
ii  grub-pc                                1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                            1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
miriam@PC1-MIRIAM:~$ 

```Confused! It says 2.00 on boot screen and 1.99-21 (whatever that is) version 2 here?:confused:
Could it be that I have 2 versions of Grub fighting each other? Is that even possible?

---

### Post by Ahari on 2013-02-25
Hi schragge,

Here you are:

```
miriam@PC1-MIRIAM:~$ ls -l /etc/grub.d/
total 60
-rwxr-xr-x 1 root root 6743 Dec 10 14:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7780 Dec 10 14:16 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17  2012 30_os-prober
-rwxr-xr-x 1 root root 1388 Dec 10 14:16 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Apr 17  2012 40_custom
-rwxr-xr-x 1 root root   95 Apr 17  2012 41_custom
-rw-r--r-- 1 root root  483 Apr 17  2012 README
miriam@PC1-MIRIAM:~$ 

```

Glad to have both of you helping me!! Thank you sooo much ):P

Btw: My mother in law is Miriam, My name is Alan! I am trying to fix her PC.

---

### Post by schragge on 2013-02-25
No, grub 1.99 **is** a version of grub 2.0. grub-legacy aka grub 1.0 would have version number like 0.99

---

### Post by Ahari on 2013-02-25
Okay - I haven't a clue anyway!! I just thought since Matt's output of the same command said 2.00, that mine was strange! Glad it is not.

---

### Post by Ahari on 2013-02-25
Just thinking.... why then does my boot screen say Grub 2.00?

---

### Post by schragge on 2013-02-25
> **Ahari said:**
> Btw: My mother in law is Miriam, My name is Alan! I am trying to fix her PC.Oops, sorry! :oops:

I don't see any obvious problems with file permissions. Well, I'm away from my Linux PC now, maybe Matt can check if all the needed scripts in /etc/grub.d are present. Meanwhile, Alan, please post the output of
```

grep default /etc/grub.d/*

```

---

### Post by Ahari on 2013-02-25
No problem schragge! Easy mistake to make! :)

```
miriam@PC1-MIRIAM:~$ grep default /etc/grub.d/*
/etc/grub.d/00_header:   set default="${GRUB_DEFAULT_BUTTON}"
/etc/grub.d/00_header:   set default="${GRUB_DEFAULT}"
/etc/grub.d/00_header:set default="${GRUB_DEFAULT}"
/etc/grub.d/00_header:function savedefault {
/etc/grub.d/05_debian_theme:set_default_theme(){
/etc/grub.d/05_debian_theme:    if [ -e /lib/plymouth/themes/default.grub ]; then
/etc/grub.d/05_debian_theme:        sed "s/^/${1}/" /lib/plymouth/themes/default.grub
/etc/grub.d/05_debian_theme:    # the default colors since we've got no idea how the image looks like.
/etc/grub.d/05_debian_theme:    # If loading the background image fails, use the default theme.
/etc/grub.d/05_debian_theme:    set_default_theme "  "
/etc/grub.d/05_debian_theme:# Earlier versions of grub-pc copied the default background image to /boot/grub
/etc/grub.d/05_debian_theme:    set_background_image "${GRUB_BACKGROUND}" || set_default_theme
/etc/grub.d/05_debian_theme:# If we haven't found a background image yet, use the default from desktop-base.
/etc/grub.d/05_debian_theme:# Finally, if all of the above fails, use the default theme.
/etc/grub.d/05_debian_theme:set_default_theme
/etc/grub.d/10_linux:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/20_linux_xen:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:    save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:    save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/README:the menu; and then adjust the default setting via /etc/default/grub.
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

Open a terminal and run these commands.

```
cd
``````
sudo strace -o tmp.txt  grub-mkconfig -o temp.grub
```It will create a file called tmp.txt.

The other file i am not so much worried about.

Please post the output of the file as an _attachment_ and not as inline text.

We can start to eliminate things. 

Your permissions are looking good. 

A look at your grub shell scripts may be in order as well.

These permissions are looking good [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515").

Kind regards

---

### Post by schragge on 2013-02-25
> **Ahari said:**
> Just thinking.... why then does my boot screen say Grub 2.00?Well, the grub developers are very conservative types. They'll label their product like 2.00 only when they're absolutely sure it's rock-solid stable. At the time precise (Ubuntu 12.04) was published, the grub 2 was still bearing the "beta" number 1.99. It's the right version as you can see [here](http://packages.ubuntu.com/precise-updates/grub-pc).

---

### Post by Ahari on 2013-02-25
Hi Matt,

Terminal output:

```
miriam@PC1-MIRIAM:~$ cd
miriam@PC1-MIRIAM:~$ sudo strace -o tmp.txt  grub-mkconfig -o temp.grub
[sudo] password for miriam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
done
miriam@PC1-MIRIAM:~$ 

```

How do I copy the txt file and paste it here? I am not very good with Linux yet!! i am trying to get a handle on it - all this command line stuff is mind boggling for me! i am used to windows GUI's :)

---

### Post by Ahari on 2013-02-25
> **schragge said:**
> Well, the grub developers are very conservative types. They'll label their product like 2.00 only when they're absolutely sure it's rock-solid stable. At the time precise (Ubuntu 12.04) was published, the grub 2 was still bearing the "beta" number 1.99. It's the right version, as you can see [here]("http://packages.ubuntu.com/precise-updates/grub-pc").
Makes sense - thanks!

---

### Post by matt_symes on 2013-02-25
Hi

@[[COLOR=#000000]Ahari[/COLOR]]("http://ubuntuforums.org/member.php?u=1658364")

Create a new post and look for  the add attachment button. I would like to take a look at that file.

Kind regards

---

### Post by Ahari on 2013-02-25
I meant that I didn't know where to find it. I think I found it, but the forum says it is too big to upload! It is 20k and the forum limit is 19k!!

---

### Post by schragge on 2013-02-25
OK. First,
```

gzip tmp.txt

```
Then upload tmp.txt.gz as attachment.

---

### Post by Ahari on 2013-02-25
Fun and games - copied to my other PC and then I put it here:
[https://dl.dropbox.com/u/3334489/tmp.txt](https://dl.dropbox.com/u/3334489/tmp.txt)

Hope I did it right!

Will also try to post it here as you suggested.

---

### Post by matt_symes on 2013-02-25
Hi 

@[[COLOR=#000000]Ahari[/COLOR]]("http://ubuntuforums.org/member.php?u=1658364") perfect.

Kind regards

---

### Post by Ahari on 2013-02-25
Hope the zip file is here now! Hope it is the right file too! LOL

---

### Post by schragge on 2013-02-25
```

stat64("/usr/etc/default/grub", 0xbfefab90) = -1 ENOENT (No such file or directory)

```This is weird. Why does it look for /etc/default/grub in /usr ? Do you have a separate /usr partition? Now, I'd like to see the output of
```

df -h

```

---

### Post by Ahari on 2013-02-25
> **matt_symes said:**
> Hi 

That's always the way. :)

Open a terminal and type

```
split -b 18000 tmp.txt
```It will produce 2 files. 

Upload the first file called xaa.

Kind regards

I got this!

```
miriam@PC1-MIRIAM:~$ split -b 18000 tmp.txt
split: cannot open `tmp.txt' for reading: No such file or directory
miriam@PC1-MIRIAM:~$ 

```

I feel so out of my depth...

---

### Post by Ahari on 2013-02-25
Here you go:```
miriam@PC1-MIRIAM:~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       449G  8,6G  418G   3% /
udev            981M  4,0K  981M   1% /dev
tmpfs           397M  1,4M  395M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            991M  244K  991M   1% /run/shm
miriam@PC1-MIRIAM:~$ 

```

You guys are amazing - this is a surreal adventure for me!

---

### Post by Ahari on 2013-02-25
> **schragge said:**
> ```

stat64("/usr/etc/default/grub", 0xbfefab90) = -1 ENOENT (No such file or directory)

```This is weird. Why does it look for /etc/default/grub in /usr ? Do you have a separate /usr partition? Now, I'd like to see the output of
```

df -h

```

As far as I know I only have 1 big partition for everything and another for the swap file - I think!

---

### Post by schragge on 2013-02-25
> split: cannot open `tmp.txt' for reading: No such file or directory
Oh don't worry. It's not there because you've packed it with gzip, so it's now called tmp.txt.gz.
To unpack it, you can run
```

gunzip tmp.txt.gz

```
But we're getting off topic now.

---

### Post by Ahari on 2013-02-25
> **schragge said:**
> Oh, don't worry. It's not there because you're packed it with gzip, so it's now called tmp.txt.gz.
To unpack it, you can run
```

gunzip tmp.txt.gz

```But we're getting off topic now.
I realised that after I posted - I was just blindly doing what you said - then I stopped to see what I had done!! LOL

---

### Post by Ahari on 2013-02-25
Back in 10 minutes - run out of coffee!

---

### Post by matt_symes on 2013-02-25
Hi

@[[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515").

I'm comparing the one i have generated against [[COLOR=#000000]Ahari[/COLOR]]("http://ubuntuforums.org/member.php?u=1658364")'s.

Mine opens /etc/default/grub

```
stat("/etc/default/grub", {st_mode=S_IFREG|0644, st_size=1260, ...}) = 0
open("/etc/default/grub", O_RDONLY)
```[[COLOR=#000000]Ahari[/COLOR]]("http://ubuntuforums.org/member.php?u=1658364")s does not even open it :)

Aharis where did you get grub from ? How did you install it ? As much detail as possibe please.

EDIT: [[COLOR=#000000]Ahari[/COLOR]]("http://ubuntuforums.org/member.php?u=1658364") when you get back please open a terminal and type.

```
ls -l /usr/etc/grub.d/
```

Kind regards

---

### Post by schragge on 2013-02-25
Well, IIRC */usr/sbin/grub-mkconfig* is nothing more than a /bin/sh script. Could it somehow get corrupted?

How about
```

grep -w '/etc/default/grub' /usr/sbin/grub-mkconfig

```

---

### Post by Ahari on 2013-02-25
I can't remember where I got Grub from! I think I got it from the Ubuntu website - it was about a week ago now. I think I followed someone's guide to update it. I will try to find out what I did and where I got it from. 

In the meantime:```
miriam@PC1-MIRIAM:~$ ls -l /usr/etc/grub.d/
total 56
-rwxr-xr-x 1 root root  7523 Feb 22 10:38 00_header
-rwxr-xr-x 1 root root  9245 Feb 22 10:38 10_linux
-rwxr-xr-x 1 root root 10054 Feb 22 10:38 20_linux_xen
-rwxr-xr-x 1 root root  9348 Feb 22 10:38 30_os-prober
-rwxr-xr-x 1 root root   214 Feb 22 10:38 40_custom
-rwxr-xr-x 1 root root   216 Feb 22 10:38 41_custom
-rw-r--r-- 1 root root   483 Feb 22 10:38 README
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

I think the config files have been stored in an odd place.

I think if he does

```
sudo cp /etc/default/grub /usr/etc/default/grub
```and then

```
sudo update-grub
```he'll have a splash screen. :D

We need to know what he installed and how in detail. 

I suspect he's installed two different versions somehow.

Kind regards

---

### Post by Ahari on 2013-02-25
Hi schragge,

Here is your output:
> **schragge said:**
> Well, IIRC */usr/sbin/grub-mkconfig* is nothing more than a /bin/sh script. Could it somehow get corrupted?

How about
```

grep -w '/etc/default/grub' /usr/sbin/grub-mkconfig

```

```
miriam@PC1-MIRIAM:~$ grep -w '/etc/default/grub' /usr/sbin/grub-mkconfig
Ensure that there are no errors in /etc/default/grub
miriam@PC1-MIRIAM:~$
```

---

### Post by schragge on 2013-02-25
Yes, Matt, this makes sense.

---

### Post by matt_symes on 2013-02-25
Hi

@Ahari

Run those two commands in my last post and then

```
sudo reboot
```

Do you get a splash screen ?

Kind regards

---

### Post by Ahari on 2013-02-25
I didn't get that far!

```
miriam@PC1-MIRIAM:~$ sudo cp /etc/default/grub /usr/etc/default/grub
[sudo] password for miriam: 
cp: cannot create regular file `/usr/etc/default/grub': No such file or directory
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

```
sudo mkdir -p /usr/etc/default/
```

Then that last copy command again.

Kind regards

---

### Post by Ahari on 2013-02-25
```
miriam@PC1-MIRIAM:~$ sudo mkdir -p /usr/etc/default/
miriam@PC1-MIRIAM:~$ sudo cp /etc/default/grub /usr/etc/default/grub
miriam@PC1-MIRIAM:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
done
miriam@PC1-MIRIAM:~$ 

```

Should I reboot now?

---

### Post by schragge on 2013-02-25
> **matt_symes said:**
> I suspect he's installed two different versions somehow.Only if one of the versions was installed bypassing the package management system, because only one was shown by dpkg:
```

miriam@PC1-MIRIAM:~$ dpkg -l | grep -i grub-pc
ii  grub-pc                                1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                            1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
miriam@PC1-MIRIAM:~$

```

---

### Post by schragge on 2013-02-25
@Ahari
Yes, please reboot

---

### Post by matt_symes on 2013-02-25
Hi

yep. reboot please.

Kind regards

---

### Post by matt_symes on 2013-02-25
Hi

A new command for you Ahari after the reboot. no -pc on the end.

```
dpkg -l | grep -i grub
```Did you get a splash screen ?

EDIT: And this command please

```
dpkg-query --listfiles grub-pc
```

EDIT2: And this command please

```
dpkg-query --listfiles grub-common
```

Kind regards

---

### Post by Ahari on 2013-02-25
Yayyyy! I got a splash screen! :cool:

```
miriam@PC1-MIRIAM:~$ dpkg -l | grep -i grub
ii  grub-common                            1.99-21ubuntu3.9                        GRand Unified Bootloader (common files)
ii  grub-customizer                        3.0.4-0ubuntu1~ppa1p                    Grub Customizer - A graphical Grub2/BURG configuration application
ii  grub-gfxpayload-lists                  0.6                                     GRUB gfxpayload blacklist
ii  grub-pc                                1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                            1.99-21ubuntu3.9                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                           1.99-21ubuntu3.9                        GRand Unified Bootloader (common files for version 2)
miriam@PC1-MIRIAM:~$ 

```

Is it permanent?

Do I have 2 copies of Grub somehow?

What did I do to mess it up so badly?

---

### Post by schragge on 2013-02-25
I'd also suggest this command
```

dpkg -S /usr/etc/grub.d/00_header

```

---

### Post by Ahari on 2013-02-25
```
miriam@PC1-MIRIAM:~$ dpkg-query --listfiles grub-pc
/.
/usr
/usr/bin
/usr/share
/usr/share/bug
/usr/share/bug/grub-pc
/usr/share/bug/grub-pc/presubj
/usr/share/bug/grub-pc/script
/usr/share/doc
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/grub-install.8.gz
/usr/share/man/man8/grub-mknetdir.8.gz
/usr/share/man/man8/grub-setup.8.gz
/usr/lib
/usr/lib/grub-legacy
/usr/lib/grub-legacy/update-grub
/usr/sbin
/usr/sbin/upgrade-from-grub-legacy
/etc
/etc/kernel
/etc/kernel/postrm.d
/etc/kernel/postrm.d/zz-update-grub
/etc/kernel/postinst.d
/etc/kernel/postinst.d/zz-update-grub
/usr/bin/grub-ntldr-img
/usr/share/doc/grub-pc
/usr/sbin/grub-mknetdir
/usr/sbin/grub-setup
/usr/sbin/grub-install
miriam@PC1-MIRIAM:~$ 

```

---

### Post by Ahari on 2013-02-25
```
miriam@PC1-MIRIAM:~$ dpkg -S /usr/etc/grub.d/00_header
dpkg-query: no path found matching pattern /usr/etc/grub.d/00_header.
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

@Ahari

Check out my last post as i post ed another command for you to un.

EDIT:

Bingo.

Nicely done both [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515") and Ahari. Between the three of us we tracked it down.

@Ahari. It's permanent.

Kind regards

---

### Post by Ahari on 2013-02-25
Sorry, I did run it, I just forgot to post it!

```
miriam@PC1-MIRIAM:~$ dpkg-query --listfiles grub-common
/.
/usr
/usr/bin
/usr/bin/grub-mkrescue
/usr/bin/grub-kbdcomp
/usr/bin/grub-mkimage
/usr/bin/grub-menulst2cfg
/usr/bin/grub-mkfont
/usr/bin/grub-mount
/usr/bin/grub-fstest
/usr/bin/grub-mkrelpath
/usr/bin/grub-script-check
/usr/bin/grub-mklayout
/usr/bin/grub-mkpasswd-pbkdf2
/usr/bin/grub-bin2h
/usr/bin/grub-editenv
/usr/share
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/apport/package-hooks/source_grub2.py
/usr/share/bug
/usr/share/bug/grub-common
/usr/share/bug/grub-common/presubj
/usr/share/doc
/usr/share/doc/grub-common
/usr/share/doc/grub-common/examples
/usr/share/doc/grub-common/examples/grub.cfg
/usr/share/doc/grub-common/README
/usr/share/doc/grub-common/TODO
/usr/share/doc/grub-common/copyright
/usr/share/doc/grub-common/THANKS
/usr/share/doc/grub-common/NEWS.gz
/usr/share/doc/grub-common/AUTHORS
/usr/share/doc/grub-common/NEWS.Debian.gz
/usr/share/doc/grub-common/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/grub-menulst2cfg.1.gz
/usr/share/man/man1/grub-bin2h.1.gz
/usr/share/man/man1/grub-mkimage.1.gz
/usr/share/man/man1/grub-mklayout.1.gz
/usr/share/man/man1/grub-mkrescue.1.gz
/usr/share/man/man1/grub-script-check.1.gz
/usr/share/man/man1/grub-fstest.1.gz
/usr/share/man/man1/grub-mount.1.gz
/usr/share/man/man1/grub-mkrelpath.1.gz
/usr/share/man/man1/grub-editenv.1.gz
/usr/share/man/man1/grub-mkpasswd-pbkdf2.1.gz
/usr/share/man/man1/grub-mkfont.1.gz
/usr/share/man/man8
/usr/share/man/man8/grub-probe.8.gz
/usr/share/man/man8/grub-mkconfig.8.gz
/usr/share/man/man8/grub-mkdevicemap.8.gz
/usr/share/grub
/usr/share/grub/ascii.h
/usr/share/grub/ascii.pf2
/usr/share/grub/unicode.pf2
/usr/share/grub/update-grub_lib
/usr/share/grub/euro.pf2
/usr/share/grub/grub-mkconfig_lib
/usr/share/grub/widthspec.h
/usr/lib
/usr/lib/grub
/usr/sbin
/usr/sbin/grub-mkconfig
/usr/sbin/grub-probe
/usr/sbin/grub-mkdevicemap
/etc
/etc/init.d
/etc/init.d/grub-common
/etc/bash_completion.d
/etc/bash_completion.d/grub
/etc/grub.d
/etc/grub.d/20_linux_xen
/etc/grub.d/00_header
/etc/grub.d/README
/etc/grub.d/10_linux
/etc/grub.d/40_custom
/etc/grub.d/30_uefi-firmware
/etc/grub.d/41_custom
/etc/grub.d/30_os-prober
/etc/grub.d/05_debian_theme
/etc/pm
/etc/pm/sleep.d
/etc/pm/sleep.d/10_grub-common
/usr/lib/grub/update-grub_lib
/usr/lib/grub/grub-mkconfig_lib
miriam@PC1-MIRIAM:~$ 

```

---

### Post by matt_symes on 2013-02-25
Hi

I'm off for pizza. Well done to both of you. Between the three of us we cracked it.

Kind regards

---

### Post by Ahari on 2013-02-25
Thank you both sooo much! This has been driving me nuts! I am a little OCD about these things :lolflag:

I am so glad this is now resolved - I don't think I will ever really understand what you did, I am just glad it worked.

Next time I will stop off here first before I go and follow every Google result I can find!

You guys rock!:guitar:

---

### Post by schragge on 2013-02-25
Still, I'm puzzled why grub-mkconfig is looking for /etc/default/grub and grub scripts in /usr? This couldn't be /usr/sbin/grub-mkconfig, right? Wonder what this command would show
```

whereis grub-mkconfig

```

---

### Post by Ahari on 2013-02-25
I think I am going to reboot a few times just to watch that darned splash screen!

:popcorn::popcorn:

At least now my very aged mother in law (83) won't keep asking me what all that code means when she turns on her PC!!

Btw: How do I get rid of the Grub menu altogether? Just out of curiosity!! I won't mess it up again by trying it!!

---

### Post by Ahari on 2013-02-25
```
miriam@PC1-MIRIAM:~$ whereis grub-mkconfig
grub-mkconfig: /usr/sbin/grub-mkconfig /usr/share/man/man8/grub-mkconfig.8.gz
miriam@PC1-MIRIAM:~$
```

---

### Post by schragge on 2013-02-25
Hmm, it looks OK to me. Not the slightest idea, what that was.

> **Ahari said:**
> Btw: How do I get rid of the Grub menu altogether? Just out of curiosity!! I won't mess it up again by trying it!!Oh this one is simple. Check that GRUB_TIMEOUT in /usr/etc/default/grub is set to 0.
```

GRUB_TIMEOUT=0

```
But I'd prefer the menu to be always shown. Just in case you ever forget that you need to boot with the **Shift** key pressed to get it displayed again. ;)

---

### Post by Ahari on 2013-02-25
Thanks schragge! Don't worry, I am done with messing about for now!! At least I can find the info one day if I decide to do it.... 

So everything is fine now?

---

### Post by matt_symes on 2013-02-25
Hi

It's fine now. It's a bit odd but still fine.

Kind regards

---

### Post by Ahari on 2013-02-26
Good morning!

I was trying to think how this happened and can only think that when I restored the image from the Redo Backup to the new hdd, the PC would not boot. After some Googling, I used Boot-Repair to install a Grub.

I got the PC to boot, but it looked strange to me with no splash screen, so I thought I didn't do it right and I followed some other thread somewhere to install another Grub from the command line.

I tried a few of these and some tweaks from both the command line and GUI's (Grub Customizer) to fix the splash screen with no luck.

I think one of the threads said I must install it (Grub) to some folder and I probably chose the wrong one being the noob that I am!

So it was probably my fault or the fault of some well intentioned advice.

I hope that any future updates to Grub won't cause a problem for me now!

I can't thank you both enough for the patient help in resolving my problem late into the night! Hope the pizza was good! (mmmm... piiizzzaaa.....!) :D

---

### Post by schragge on 2013-02-26
I guess any future GRUB update will revert the system to using /etc/default/grub instead of /usr/etc/default/grub. You can test it now if so inclined by reinstalling *grub-common*:
```

sudo apt-get --reinstall install grub-common

```Since /usr/etc/default/grub and /etc/default/grub are now identical, there should not be any change in behaviour.

But, as the saying goes, if it's working, better don't touch it. :)

If you really want to investigate the cause then have a look at the files **/usr/sbin/grub-mkconfig** and **/usr/share/grub/grub-mkconfig_lib**. You may want to save copies of them to your home directory before making any changes to grub:
```

cp /usr/sbin/grub-mkconfig /usr/share/grub/grub-mkconfig_lib ~

```
then, after reinstalling grub-common as shown above, watch for any differences:
```

diff {~,/usr/sbin}/grub-mkconfig
diff {~,/usr/share/grub}/grub-mkconfig_lib

```
If there are no differences (i.e. the two commands above show nothing) then it's all a complete mistery to me as to what could had gone wrong. :?

For reference, this is what *grep sysconfdir /usr/sbin/grub-mkconfig* shows on my system (Debian wheezy):
```

sysconfdir="/etc"
grub_mkconfig_dir="${sysconfdir}"/grub.d
if test -f ${sysconfdir}/default/grub ; then
  . ${sysconfdir}/default/grub
# from ${grub_mkconfig_dir} and settings from ${sysconfdir}/default/grub

```

---

### Post by Ahari on 2013-02-26
Thanks for the info schragge. I am kinda all "Ubuntued" out for now. I will give this a try in a while.

At least I know where to find the info I need!

:)

---

