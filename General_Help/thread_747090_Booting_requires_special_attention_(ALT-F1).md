---
title: "Booting requires special attention (ALT-F1)"
date: 2008-04-06
forum: General Help
---

### Post by fa2k on 2008-04-06
I have a media pc connected to a TV using DVI/HDMI. The graphics card is a Radeon 2400.

When booting, I don't get the Ubuntu logo+progressbar screen, which is no big loss.
The problem is that the computer hangs, with a black screen, until I press ALT-F1 during boot.
This happens after it starts loading the kernel, I think. It says "Kernel Alive" at the bottom of the screen, and then it turns black. After I press the magic key, it continues normally with the 
Starting X .... [done]
type messages. I haven't tried ALT-F2, etc., but it will probably work too.

I have tried to add "nosplash" to this line in /boot/grub/menu.lst, bt it didn't help
```
# kopt=root=UUID=ad114e25-a470-4e25-9a7a-69213d47cd09 ro nosplash
```
Is that the correct one?

The real problem is that this machine also functions as a server, and needs to be rebooted unattended on power loss.

Hope someone can help me!

---

### Post by danwood76 on 2008-04-07
You need to add nosplash to the kernel line.

for example my line is:
```

kernel   /boot/vmlinuz-2.6.24-15-generic root=/dev/mapper/isw_bbbbfiiiih_HDb6 ro quiet splash

```

changing the splash to nosplash would remove my splash screen.

---

### Post by fa2k on 2008-04-07
Thanks! will try that.

Update: It works! I still need to have the TV on for X to recognize it (or later restart gdm), but this is progress:D

---

