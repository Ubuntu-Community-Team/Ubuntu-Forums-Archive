---
title: "UEFI select boot device menu?"
date: 2016-07-06
forum: General Help
---

### Post by Paramite on 2016-07-06
Hey, on Windows 10 you have the possibility to enter a command ```
shutdown /r /o
``` which brings you to the UEFI menu without restarting your computer. There you can select the device you want to boot from, among other thing. (Pictures: <snip> and <snip>)Is there a built in way in *buntu where you can do the same, or is there a program that does this?

---

### Post by QIII on 2016-07-06
Rather than directing other users to random shortened urls, please use the attachment functionality to insert thumbnail images.

---

### Post by oldfred on 2016-07-06
I have never tried it, but you should if UEFI boot  have this entry at bottom of grub menu. 
May not work on all UEFI?

```

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```

---

