---
title: "[SOLVED] Resizing NTFS partition with gparted"
date: 2007-08-25
forum: General Help
---

### Post by Man_Beach on 2007-08-25
The gparted documentation says that you should reboot after resizing an NTFS partition :

> Resizing NTFS partition impose you to reboot the system !
DON’T DO any other operations on this partition before the reboot,
otherwise you will get errors. After the boot-up Windows logo,
the system will show a special screen, and a message
asking about drive consistency : Checking file system on c :

There are various Windows XP screens shown, talk of AUTOCHK etc...

But I haven't got Windows XP! Why I want the NTFS partition can be found here -

[http://ubuntuforums.org/showthread.php?t=532388]("http://ubuntuforums.org/showthread.php?t=532388")

Has anyone found this to be an issue or am I worrying too much?

---

### Post by Happy_Man on 2007-08-25
That's just because Gparted assumes you are resizing an XP partition. It doesn't know that it is just storage. Ignore the message, and move on.

---

### Post by Man_Beach on 2007-08-25
Thanks. Just wanted to make sure before I started...

---

