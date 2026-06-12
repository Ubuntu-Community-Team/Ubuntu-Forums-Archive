---
title: "mount floppy with full permissions"
date: 2007-06-30
forum: General Help
---

### Post by Elvis1985 on 2007-06-30
Hi,

I am using Ubuntu 7.04 and am trying to mount a floppy with full permissions.
I use a website that stores an authentication key on a floppy, but on first time access the floppy needs to have write permissions for the floppy.
My error message is the same as when in windows when I insert the floppy in read-only mode.


Here is what I get when I type ls -l when the floppy is not mounted:

drwxrwxrwx 2 root root 4096 2007-06-30 18:48 floppy

which should allow a website to write to this folder, right?
Now, as soon as I mount my floppy drive it changes to this:

drwxr-xr-x 2 elvis elvis 4096 2007-06-30 18:48 floppy

and all permission changes I try to make to the dir won't have any effect.
I can create directories or files from a command line terminal, but not through the GUI.
I also cannot change the permissions through the properties menu in the graphical file browser.

In my /etc/fstab file this is the line for the floppy:

/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0


Now my question is: how do I mount this floppy drive, so that it has full permissions?


Any help would be greatly appreciated!

---

### Post by Elvis1985 on 2007-07-01
*bump*
sorry, but still trying to resolve the problem...

---

### Post by sja42 on 2007-07-02
I have the same problem.  I need to format and then write to a floppy.  Feisty doesn't let me do it.

Can no one help?

---

