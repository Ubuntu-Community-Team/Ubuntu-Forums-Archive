---
title: "Strange boot situation (Broken laptop screen can't view BIOS, and other weirdness)"
date: 2016-10-04
forum: General Help
---

### Post by T2uiYKb7 on 2016-10-04
Sorry this takes a while to explain because of it's uniqueness. **The whole thing would be extremely simple to fix if I could see BIOS.**

My fathers laptop (Samsung NP530U3B-A01) screen broke. It's been removed completely and he now just has what looks like a keyboard and track-pad connected to a new monitor via HDMI. (Actually looks surprisingly cool and somewhat intentional.)

This means that nothing appears on the screen until the HDMI kicks in which means no way to view BIOS or the BIOS boot menu.

On top of that his internal sata HDD ribbon connector split. A replacement is in the post but will be three weeks.

He's currently booting off an external HDD but the performance isn't great and it get in the way a bit.

It was quite a high end laptop a few years back and it has a weird 16GB solid state HDD in addition to the 500GB sata (with the connector in the mail.)

The internal SSD is always recognised as sda1 and still works fine, I can install Ubuntu on to it but it doesn't boot. [B](This would be a piece of cake to fix if I could see BIOS.)

[COLOR=#008000]It boots off USB fine so I installed Grub2 to an teeny USB stick and I want to put an entry in grub.cfg that points to the Ubuntu install on the sda1 SSD. How would I go about this?
[/COLOR][/B]

---

### Post by T2uiYKb7 on 2016-10-04
This is the entry as it look on the internal SSD's /boot/grub/grub.cfg file. This has Ubuntu Mate 16.04.1 installed on it.

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-58871eeb-cdf5-4efa-b4dd-9ee33147f6a5' {    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  58871eeb-cdf5-4efa-b4dd-9ee33147f6a5
    else
      search --no-floppy --fs-uuid --set=root 58871eeb-cdf5-4efa-b4dd-9ee33147f6a5
    fi
    linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=58871eeb-cdf5-4efa-b4dd-9ee33147f6a5 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-31-generic
}
```

**Edit: Got the internal SSD booting from the USB Grub2. :) I should have tried properly before opening a thread.**

---

