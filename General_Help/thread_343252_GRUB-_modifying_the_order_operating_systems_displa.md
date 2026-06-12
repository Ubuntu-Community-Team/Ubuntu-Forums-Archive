---
title: "GRUB- modifying the order operating systems displayed in"
date: 2007-01-21
forum: General Help
---

### Post by trout227 on 2007-01-21
Hi,
Is it possible to modify the order that operating systems appear in in GRUB. I'm running version 0.97. The reason I want to do this is because currently Ubuntu is at the top of the list and so after 30 seconds automatically boots into ubuntu, but I would like Windows to be at the top of the list so it boots automatically into that (I'm not the only person using this computer and they don't want to use ubuntu :-s)
Thanks,
Trout

---

### Post by JamieC on 2007-01-21
Open a new terminal window and type the following:
```

sudo vim /etc/X11/xorg.conf

```

You will see sections for each operating system, order them as appropriate and append the line 'savedefault' to the Windows entry, removing it from the Ubuntu one. Paste the file here if you need assistance.

---

### Post by trout227 on 2007-01-21
I'm a bit of a beginner, how do you open a terminal window?
Thanks,
Trout

---

### Post by JamieC on 2007-01-21
Applications -> Accessories -> Terminal (or CTRL + ALT + F2). 

I'd advise the first one...

---

### Post by trout227 on 2007-01-21
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"

---

### Post by JamieC on 2007-01-21
Sorry, I'm going totally mad here. The command you need is actually:
```

sudo vim /boot/grub/menu.lst

```

The command I gave was for your X server configuration, I'm so wrapped up in editing my own at the minute!

---

### Post by trout227 on 2007-01-21
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by JamieC on 2007-01-21
Use the following:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider, added to separate the menu items below from the Windows
# one.
title Other operating systems:
root

title Ubuntu, kernel 2.6.15-27-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


By the way, you've got two kernel versions, if you know that the newer version 2.6.15-**27**-386 is working then you can remove version 2.6.15-**26**-386 using the 'Synaptic Package Manager'.

---

### Post by trout227 on 2007-01-21
so what do i do paste that into the terminal?

---

### Post by JamieC on 2007-01-21
In terminal run the following command (gedit is a text editor, a little easier to use that vim):
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```

When the editor opens remove the section of code you pasted here, and replace it with the section of code I gave you. Then save the file.

---

### Post by trout227 on 2007-01-21
It works. Thank you for your help :D

---

### Post by JamieC on 2007-01-21
You're very welcome, glad you've got it working.

If you're not that experienced I'd advise leaving the older kernel present for now.

---

### Post by dave.goodfellow on 2007-01-23
> **JamieC said:**
> In terminal run the following command (gedit is a text editor, a little easier to use that vim):
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```

When the editor opens remove the section of code you pasted here, and replace it with the section of code I gave you. Then save the file.

Thanks for the above.
Worked for me

---

