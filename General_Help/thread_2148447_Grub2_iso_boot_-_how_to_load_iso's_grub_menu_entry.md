---
title: "Grub2 iso boot - how to load iso's grub menu entry."
date: 2013-05-25
forum: General Help
---

### Post by darekch on 2013-05-25
Following this guide: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) I have usb with multiple isos. One of isos is ubuntu iso. Now I would like to invoke ubuntu iso, see ubuntu iso's it's own menu entry and run it's memtest86+. It's available if I will burn the iso on the CD but how to achieve this if iso is loaded by GRUB2?

As a workaround I put memtest86+bin in isos folder and put menuentry for it:
```

menuentry "Memory test (memtest86+ 4.20)" {
    linux16 /boot/isos/memtest86+-4.20.bin
}

```

Another example would be to reach parted magic menu: [http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots)
Such solution would bring much more flexibility.

I guess it's not possible? But maybe I can create additional menu entry to reach i.e. ubuntu's memtest?

---

### Post by deadflowr on 2013-05-25
You could look into trying to chainload into the iso's bootloader, which would then give you the iso's boot options.
Don't know if it's even possible, but worth looking into.

Anyway, what's wrong with the memtest already provided in the grub that's loading?

---

### Post by sudodus on 2013-05-25
> **darekch said:**
> Following this guide: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) I have usb with multiple isos. One of isos is ubuntu iso. Now I would like to invoke ubuntu iso, see ubuntu iso's it's own menu entry and run it's memtest86+. It's available if I will burn the iso on the CD but how to achieve this if iso is loaded by GRUB2?

As a workaround I put memtest86+bin in isos folder and put menuentry for it:
```

menuentry "Memory test (memtest86+ 4.20)" {
    linux16 /boot/isos/memtest86+-4.20.bin
}

```

Another example would be to reach parted magic menu: [http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots)
Such solution would bring much more flexibility.

I guess it's not possible? But maybe I can create additional menu entry to reach i.e. ubuntu's memtest?

The 'grub-n-iso' method works unless you have Windows 8 and UEFI.

See my posts in this thread

[http://ubuntuforums.org/showthread.php?t=2146967&page=2](http://ubuntuforums.org/showthread.php?t=2146967&page=2)

Browsing the internet you can find the command lines needed for many iso files except the Ubuntu files (but I think it is hard or impossible with some of them, for example the Ubuntu alternate iso files).

---

