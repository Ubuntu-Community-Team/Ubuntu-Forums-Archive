---
title: "Font Too Small In Boot Screen"
date: 2015-06-29
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-06-29
Hello,

The font is too small in my boot menu 14.04 LTS.

Thanks, Hannibal

---

### Post by Bashing-om on 2015-06-29
coljohnhannibalsmith; Hi !

If you like the GUI resolution.perhaps set in "/etc/default/grub" to match ?
```

xdpyinfo  | grep dimensions

```

and edit " /etc/default/grub" line : " #GRUB_GFXMODE=640x480 " to match ( removing the starting comment character) .
And then of course propagate the change:
```

sudo update-grub

```

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2015-06-29
> **coljohnhannibalsmith said:**
> Hello,

The font is too small in my boot menu 14.04 LTS.

Thanks, Hannibal

I know what you mean - my screen is 1920x1080 and the default text is too small in the grub menu. Here's what I do: To make it larger, I edit the file and line Bashing-om refers to in post #2 and change the value to a lower resolution. To see the resolutions that are supported, when the grub menu is onscreen, type 'c' for command line and type the command vbeinfo. To return to the grub menu, press ESC. 

Only use the dimensions displayed, like 800x600. I edit /etc/default/grub with nano, the terminal text editor, and set mine to 800x600 which is perfect for me. Remove the #. Then, sudo update-grub to incorporate the change into grub.cfg and reboot.

Note that this resolution only affects the grub menu.
I hope this helps.

---

