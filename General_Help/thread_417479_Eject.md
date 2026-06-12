---
title: "Eject"
date: 2007-04-21
forum: General Help
---

### Post by BrokeBody on 2007-04-21
In previous versions of Ubuntu, when I would insert CD, DVD or USB Flash Drive, an icon of that drive would appear on desktop. When my work is done, right click on that icon-> "Eject". Now, under Feisty, there is no that icon on desktop anymore, and it's really getting on my nerves to type in Terminal every time when I have to eject a medium (CD, DVD, USB Flsh Drive...)! :mad: I tried with editing fstab, but no luck. :(

Any way to fix/create this?

---

### Post by raja on 2007-04-21
In gconf, you can go to apps>nautilus>desktop> and check volumes visible. Otherwise just copy and paste this in the terminal.
```
gconftool-2 --set "/apps/nautilus/desktop/volumes_visible" --type bool "true"
```

Another option is to put the 'disk-mounter' applet on the panel and use it.

---

### Post by BrokeBody on 2007-04-21
It's already checked. :( I can see only sda volumes (hard disks), but I can't see scd volumes (CD/DVD).

---

### Post by raja on 2007-04-21
Thats strange. Are the disks mounted at /media?

---

### Post by BrokeBody on 2007-04-21
Yes, they are.

---

### Post by raja on 2007-04-21
Sorry - cant think of anything else there. Did you try the disk mounter applet?

---

### Post by BrokeBody on 2007-04-21
It's ok. ;) I restarted system and it works now. Every volume has it's own icon on desktop when mounted. :)

I'm still curious what actually happened, what was this all about? :confused:

---

