---
title: "[SOLVED] Mounting Windows Partition"
date: 2008-02-20
forum: General Help
---

### Post by dstein on 2008-02-20
Hello. Can someone please explain to me why on [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows),

when mounting a windows partition, we type:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

when the following seems to work as well:

/dev/hda1 /media/hda1 ntfs defaults 0 0

I guess that I am asking what nls=utf8,umask=0222 does and why? Thanks.

---

### Post by freelinuxhelp on 2008-02-20
NLS = Native Language Support
Lets you display filenames with native language characters from the Microsoft FAT file system family or from JOLIET CD-ROMs correctly on the screen, you need to include the appropriate input/output character sets for it to work.

umask is a way to set default permissions for the device.

---

### Post by Nameless_one on 2008-02-20
I am surprised that defaults work fine for you! Without the permission mask, I can't even cd to the windows partition.

---

### Post by dstein on 2008-02-21
They actually may not work properly. However, an icon formed on my desktop that said Windows XP, which is why I believed it worked.

---

### Post by freelinuxhelp on 2008-02-21
Test it whenever you get a chance. and let us know if we need to keep working on this.

---

### Post by freelinuxhelp on 2008-03-08
Did everything work out for you?

---

### Post by dstein on 2008-03-08
Everything worked perfectly. Thanks again!

---

### Post by freelinuxhelp on 2008-03-08
Good deal. :-)
Please mark the thread as solved when you get a chance. It's under thread tools.

---

