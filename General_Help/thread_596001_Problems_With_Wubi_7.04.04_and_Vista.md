---
title: "Problems With Wubi 7.04.04 and Vista"
date: 2007-10-29
forum: General Help
---

### Post by jusael on 2007-10-29
I tried to install Wubi on Windows Vista Ultimate on drive C: which is where Vista is installed, but when I choose Wubi Ubuntu from the boot menu after reboot I get some kind of error saying that it can't find menu.lst. It displays a menu where there are choices for grub/menu.lst or something similar, but none of them seem to work. One of them appears to print something similar to "boot find '/grub/menu.lst'" endlessly after I select it.

Previously I tried installing Wubi on an external USB hard drive, but I got an error saying that Windows couldn't be found after selecting Wubi Ubuntu from the boot menu. I uninstalled that install through Wubi's uninstaller. However, after the second time I installed Wubi, there appears to be two "Wubi Ubuntu" choices available in addition to Vista in the boot menu. The first produces the previous effect, and the other the one I described earlier.

I'm completely new to Linux things so I have no idea what is wrong.

---

### Post by ago on 2007-10-29
Can you try with wubi 7.10 rev381+?

---

### Post by ago on 2007-10-29
[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

Uninstall any previous version first and run chkdsk /r

---

### Post by jusael on 2007-10-29
Thanks, I will try Wubi 7.10. the first thing tomorrow. By the way, can Wubi Ubuntu be installed on an external USB hard disk? It would be more convenient for space reasons, but I can't seem to select that drive as a boot device from my BIOS Setup if that matters.

---

### Post by ago on 2007-10-29
> **jusael said:**
> Thanks, I will try Wubi 7.10. the first thing tomorrow. By the way, can Wubi Ubuntu be installed on an external USB hard disk? It would be more convenient for space reasons, but I can't seem to select that drive as a boot device from my BIOS Setup if that matters.

It should, but I haven't tested that myself

---

### Post by jusael on 2007-10-30
I installed Wubi 7.10 on my other internal hard disk and was able to get as far as into the graphical Ubuntu installer. However, I ran into the same problem as described in the other thread here where the installer hangs at various % and freezes. I'll be following that thread from now on.

---

