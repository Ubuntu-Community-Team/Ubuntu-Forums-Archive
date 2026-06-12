---
title: "Terminal hanging problem"
date: 2008-05-06
forum: General Help
---

### Post by satterle on 2008-05-06
I recently ran some scripts through terminal (wine set up, winetricks, etc) and noticed two issues:

FIRST, when I ran the script the first response was:

fixme:spoolsv:serv_main (0 (nil))

What does this mean? Is this a problem?

SECOND, the winetricks script ran for about 5 minutes now and got stuck on

Backtrace:
...
10 0xb7e909c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

This behavior also happened when I reinstalled Word 2000 -- terminal hung at the "end" of the routine. I had to Ctrl-C to return to a prompt. Again, is this normal?

---

### Post by fahadsadah on 2008-05-06
Please could you post the contents of these scripts here?
Also, are you saying that you installed Microsoft Word on Ubuntu?

---

### Post by fahadsadah on 2008-05-06
Ignore this please, double posting

---

### Post by satterle on 2008-05-06
the two commands run:

wine /media/cdrom/setup.exe -- this to reinstall MS Word from the disc

sh winetricks corefonts -- after saving the winetricks script. see [http://www.linuxforums.org/forum/wine/111138-fonts-wine.html](http://www.linuxforums.org/forum/wine/111138-fonts-wine.html)

---

