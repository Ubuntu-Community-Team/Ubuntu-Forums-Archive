---
title: "Add Parted Magic to grub2 menu"
date: 2013-04-19
forum: General Help
---

### Post by Bladeforce on 2013-04-19
Hi, I have an iso of parted magic called (pmagic_2013_02_28.iso). All I would like to do is add this iso to the boot menu in grub2 and be able to boot to it so I dont have to boot from the usb drive because for some reason my bios takes ages to boot from usb. 



I have added this to my 40_custom file as per [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

menuentry "Parted Magic ISO" {

set isofile="/home/ade/pmagic_2013_02_28.iso"

loopback loop (hd0,1)$isofile

linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject

initrd (loop)/casper/initrd.lz

}

When i come to update grub I get this error

/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 5: /etc/grub.d/40_custom: Syntax error: "(" unexpected

The iso is stored in my home folder on sda1

Could anyone help please?

---

### Post by matt_symes on 2013-04-19
Hi

I just downloaded partedmagic and added my own custom entry to 40_custom and ran update-grub.

It added the custom menu items with no problems.
```

menuentry "Parted Magic ISO" {

set isofile="/home/matthew/pmagic_2013_02_28.iso"

loopback loop (hd0,1)$isofile

linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject

initrd (loop)/casper/initrd.lz

}
```

I have not rebooted to test as i am currently building a kernel. 

You are 100% Parted magic is in your home directory, of the correct size and is not corrupt ?

If you remove the entry from 40_custom and run update grub again, does it update successfully. That will eliminate something else.

Kind regards

---

### Post by oldfred on 2013-04-19
Parted Magic is not in the same file locations as Ubuntu installs and at least with the version I boot, I have different parameters.

```
menuentry "Parted Magic (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/pmagic_2012_05_30.iso"
    loopback loop (hd2,4)$isofile
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB
    initrd (loop)/pmagic/initrd.img
}

```

My iso folder is on another drive in the 4th partition (hd2,4) and drive is gpt partitioned so I have to have that insmod.

I also now create a text file for all my ISO grub boot entries like above and just have one small entry in grub2's 40_custom that never changes. Then I can edit text file (livecdimage.cfg) and not rerun the update-grub. I like this because just about every time I would edit file and forget to update.

# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#}

---

### Post by matt_symes on 2013-04-19
Hi

That's good to know about the file structure of partedmagic, oldfred. 

I would normally mount it and take a look myself if it does not work after a reboot.

You saved me some time.

Kind regards

---

### Post by Bladeforce on 2013-04-19
Thanks for the help :)Yes when I have no entry in my 40_custom the update-grub runs fine

I added matt_symes grub to my 40_custom and this is what happens when grub updates. My iso is fine and the md5 checks out with the md5 on the partedmagic page in my home directory

menuentry "Parted Magic ISO" {
set isofile="/home/ade/pmagic_2013_02_28.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

Generating grub.cfg ...
using custom appearance settings
Found background image: /home/ade/Pictures/Slick-Ubuntu.png
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Mac OS X on /dev/sdb2
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 3: /etc/grub.d/40_custom: Syntax error: "(" unexpected


I also have tried oldfreds attempt deleting the insmod line as it's not on a gpt  drive and substituted to hd0,1 and created a folder called "iso" and put the image into that folder

menuentry "Parted Magic (Boot ISO Image via Grub2) " {
set isofile="/iso/pmagic_2012_02_28.iso"
    loopback loop (hd0,1)$isofile
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB
    initrd (loop)/pmagic/initrd.img
}

I get the same error unfortunately

Generating grub.cfg ...
using custom appearance settings
Found background image: /home/ade/Pictures/Slick-Ubuntu.png
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Mac OS X on /dev/sdb2
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 3: /etc/grub.d/40_custom: Syntax error: "(" unexpected

 May I ask is it possible that my bios has my drives in a different order to how ubuntu sees them after booting? Scratching my hair out here ;)

---

### Post by oldfred on 2013-04-19
The first is giving an error about a missing (. 
Post your entire 40_custom.
I had a typo my my 40_custom for years (since almost the start of grub2). And with 12.04, it then gave an error. I was missing a boot stanza before but it was for a very old install I did not notice was missing.  So now os_prober is more particular about formatting.

       cat /etc/grub.d/40_custom

---

### Post by Bladeforce on 2013-04-19
Thanks this is the contents of my 40_custom

menuentry "Parted Magic ISO" {
 set isofile="/home/ade/pmagic_2013_02_28.iso"
 loopback loop (hd0,1)$isofile
 linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
 initrd (loop)/casper/initrd.lz
 }

---

### Post by oldfred on 2013-04-19
This is part of mine. Did you delete the lines it says not to delete?

```
fred@fred-Precise:~$ cat /etc/grub.d/40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry " " {
set root= 
}

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    insmod part_msdos
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry " " {
set root= 
}

menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

menuentry " " {
set root= 
}

menuentry 'Ubuntu 12.10, (on /dev/sdd4 from hd0' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root=(hd0,gpt4)
    linux /vmlinuz root=/dev/sdd4 ro quiet splash vt.handoff=7
    initrd /initrd
}

```

---

### Post by oldfred on 2013-04-19
I am posting from Parted Magic 2013 version.

I had to add nomodeset like I do with Ubuntu as it turned monitor off.
And it did have a minor setting change. The syslinux had 384 for vmalloc.
LiveCD also has efi and grub to boot efi.

> menuentry "Parted Magic 2013 (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/pmagic_2013_02_28.iso"
    loopback loop (hd2,4)$isofile
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=384MiB nomodeset
    initrd (loop)/pmagic/initrd.img
}


---

### Post by Bladeforce on 2013-04-19
OldFred, you sir are a bloody genius. Somewhere in the past I must have got hasty and deleted this line from the top

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


I have added this line so it now looks like :-

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Parted Magic ISO" {
set isofile="/home/ade/pmagic_2013_02_28.iso"
loopback loop (hd0,1)$isofile
linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=384MiB
initrd (loop)/pmagic/initrd.img
}


Works great now!! I didnt need the nomodeset as it runs fine without it

MANY, MANY thanks!!

---

### Post by oldfred on 2013-04-19
Glad you got it working.

Plus I now have the updated ISO in my (too large) inventory of repair ISOs.

---

### Post by matt_symes on 2013-04-19
> Plus I now have the updated ISO in my (too large) inventory of repair ISOs.

You can never have too many of them :D I've now got most of mine set to PXE boot onto damaged PCs.

With liveCD/USB, PXE booting and now this (removing hardware into a known good machine and booting a known good iso from the hard drive) there are a whole host of options to fix a damaged PC.

I'll be using what you posted here myself, so thanks :popcorn:

---

