---
title: "USB Keyboard - Not working in Gutsy"
date: 2008-03-19
forum: General Help
---

### Post by Blazed on 2008-03-19
So I recently migrated an old installation of Feisty to an external usb drive as I could not get Gutsy to install on my second SATA drive - first ever frustrating experience with Ubuntu. I then upgraded to Gutsy.

It worked in the end and boots and operates as well as before with all my settings and appz intact. There is one tiny niggle though: my usb comfort curve M$ keyboard won't work in gutsy. I'm a little nonplussed by this - it worked under feisty why not gutsy? I had a ps2 keyboard plugged in while I was migrating the system and while running the upgrade could it be related?

Anyway brief system specs: AMD Dualcore 4800+, 3gb ddr2, geforce 8600gt, 2 x SATA drives - ubuntu installed on external usb drive.

Anyone know how I could fix this issue? The usb keyboard is nice and comfortable to work with :) - the ps2 keyboard is clunky and horrible :(

---

### Post by Athelstan101 on 2008-03-19
You could try disconnecting your USB keyboard, then open a terminal window and type:

```
$ sudo cat /proc/kmsg
```

Then connect the USB keyboard and see what messages are logged.

Also, does running lsusb find the USB keyboard?

```
$ lsusb
```

---

### Post by Blazed on 2008-03-20
Ta, thanks for your help. The problem resolved itself this evening when I booted with only the usb keyboard plugged in.

> **Athelstan101 said:**
> You could try disconnecting your USB keyboard, then open a terminal window and type:

```
$ sudo cat /proc/kmsg
```

Then connect the USB keyboard and see what messages are logged.

Also, does running lsusb find the USB keyboard?

```
$ lsusb
```

---

