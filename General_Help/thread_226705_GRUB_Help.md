---
title: "GRUB Help"
date: 2006-07-31
forum: General Help
---

### Post by Karant on 2006-07-31
I couldn't find a truly appropriate section for this question, but, how do I make Windows XP the default on GRUB Boot-loader? So instead of it automatically booting off Ubuntu if I leave it for 10 seconds, it'll boot off Windows XP. Thanks.

---

### Post by H.E. Pennypacker on 2006-07-31
You need to edit the GRUB menu.  Either edit the menu manually, or use a GUI like this one:

[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

---

### Post by teasum on 2006-07-31
The easiest method would be to change this section of your menu.lst file:


```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

The default is 0, which tells GRUB to boot the top entry in the list.  You can simply change this number to point to the Windows entry in your list (i.e. if windows is the 5th entry, you would change this to "default  4" since GRUB counts from 0).  

Or, instead of GRUBconf, you could use Gnome System Tools: [http://www.gnome.org/projects/gst/index.html](http://www.gnome.org/projects/gst/index.html).

Good luck.

---

