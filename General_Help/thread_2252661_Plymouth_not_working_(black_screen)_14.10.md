---
title: "Plymouth not working (black screen) 14.10"
date: 2014-11-13
forum: General Help
---

### Post by X_Splinter on 2014-11-13
Well I had no problems in 14.04 but this time in a 14.10 clean install the boot screen was working even after installing Nvidia drivers.

I went to change the plymouth to the Earth-Sunrise and now all I get is a black screen

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.16.0-24-generic.efi.signed root=UUID=e46c57df-8abd-4e09-be9f-472b2448b2f5 ro quiet splash

```

on grub

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
 GRUB_GFXMODE=1920x1080
 GRUB_GFXPAYLOAD_LINUX=kept
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
```

I have no idea what else to try... Please some one help

---

### Post by X_Splinter on 2014-11-15
Solved

Changed
      GRUB_GFXMODE=1920x1080
      GRUB_GFXPAYLOAD_LINUX=kept
to
      GRUB_GFXMODE=1920x1080
    GRUB_GFXPAYLOAD_LINUX=1920x1080

---

### Post by CantankRus on 2014-11-15
> **X_Splinter said:**
> Solved

Changed
      GRUB_GFXMODE=1920x1080
      GRUB_GFXPAYLOAD_LINUX=[COLOR="#FF0000"]kept[/COLOR]
to
      GRUB_GFXMODE=1920x1080
    GRUB_GFXPAYLOAD_LINUX=1920x1080
I believe it's [COLOR="#FF0000"]keep[/COLOR]

---

### Post by palto42 on 2015-05-27
Thanks [**[COLOR=#000000]X_Splinter[/COLOR]**]("http://ubuntuforums.org/member.php?u=717250"), the solution worked on my PC as well :)

(yes, it was "keep", but had to change it to the actual resolution)

---

