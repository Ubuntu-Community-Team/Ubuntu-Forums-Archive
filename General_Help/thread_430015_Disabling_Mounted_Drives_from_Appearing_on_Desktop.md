---
title: "Disabling Mounted Drives from Appearing on Desktop"
date: 2007-05-01
forum: General Help
---

### Post by jazoon on 2007-05-01
Could someone explain to me how to disable mounted drives from showing up on the desktop. It's kind of an annoying feature for me just because I like to keep my desktop clean looking, just a pet peeve i guess. Oh yeah, and I'm using Gnome/Ubuntu Edgy Eft. Thanks in advance :p

---

### Post by apunc1 on 2007-05-01
```
gconf-editor
```

apps>nautilus>desktop

uncheck volumes_visible

---

### Post by dcstar on 2007-05-01
> **jazoon said:**
> Could someone explain to me how to disable mounted drives from showing up on the desktop. It's kind of an annoying feature for me just because I like to keep my desktop clean looking, just a pet peeve i guess. Oh yeah, and I'm using Gnome/Ubuntu Edgy Eft. Thanks in advance :p

Applications-System Tools-Configuration Editor-Apps-Nautilus-Desktop-volumes_visible

---

### Post by jazoon on 2007-05-01
Thank you so much :guitar:

---

### Post by apunc1 on 2007-05-01
i should probably add that now when you plug in external drives such as an usb drive, they will not be visible on your desktop. you can find them in /media or open up nautilus and click on "computer" to show all your volumes.

---

### Post by aidanr on 2007-05-01
or modify /etc/fstab to mount said partitions in /mnt rather than /media so that they won't show up on the desktop and you can still have cd's/usb thumb drives etc show up

---

### Post by apunc1 on 2007-05-01
> **aidanr said:**
> or modify /etc/fstab to mount said partitions in /mnt rather than /media so that they won't show up on the desktop and you can still have cd's/usb thumb drives etc show up

i think i read that here before and forgot. thanks for reminding me.

---

