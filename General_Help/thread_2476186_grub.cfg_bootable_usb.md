---
title: "grub.cfg bootable usb"
date: 2022-06-19
forum: General Help
---

### Post by Disabled20241022 on 2022-06-19
Hi guys!
I have a bootable USB running grub with a theme but i have a new laptop now which has a 4k screen (Dell XPS 17 laptop) and my grub menu is tiny and i do not know how to adjust it to my resolution.

This is what i have in the grub.cfg
```
insmod gfxtermterminal_output gfxterm
loadfont /boot/grub/themes/Slaze/dejavu_sans_12.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_14.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_16.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_24.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_32.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_48.pf2
loadfont /boot/grub/themes/Slaze/terminus-12.pf2
loadfont /boot/grub/themes/Slaze/terminus-14.pf2
loadfont /boot/grub/themes/Slaze/terminus-16.pf2
loadfont /boot/grub/themes/Slaze/terminus-18.pf2
insmod jpeg
insmod png
theme=/boot/grub/themes/Slaze/theme.txt
export theme


default=0
```

Keep in mind that it is a bootable USB grub menu and commands to install grub from linux do not work there.

---

### Post by sudodus on 2022-06-19
In the grub menu of mkusb (when not cloning) I get fair sized text with

```

set gfxmode=800x600

```

If you install [mkusb](https://help.ubuntu.com/community/mkusb), you find its whole configuration at **[FONT=Courier New]/usr/share/mkusb/grub.cfg[/FONT]**, and it is FOSS, so you can borrow from it :-)

---

### Post by Disabled20241022 on 2022-06-19
even with 3840x2400 (16:10) ?

---

### Post by dragonfly41 on 2022-06-19
You could also try [rEFInd]("https://www.rodsbooks.com/refind/installing.html") which is a GUI. It runs in parallel.
You can define your own [custom theme]("https://www.rodsbooks.com/refind/themes.html") in refind.conf.

---

### Post by sudodus on 2022-06-19
> **ayudha said:**
> even with 3840x2400 (16:10) ?

It works for me with 3840x2160. I suggest that you try. You may or may not like it. Maybe you will prefer another and slightly higher resolution.

---

