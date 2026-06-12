---
title: "Progress info when copy files to desktop"
date: 2017-09-18
forum: General Help
---

### Post by garvied on 2017-09-18
Good morning.

I have a doubt, when copying files between two folders using nautilus at the top of the window appears the progress of the copy ([https://goo.gl/EXkRTX](https://goo.gl/EXkRTX)), but if what I do is copy to the desktop dropping the file in the desktop does not see the copy process anywhere.
When they are large files or many files can not know the time that is missing and if it is finished.

Someone knows how to make something appear that tells how the copy goes

Using Ubuntu 17.04 64bits, nautilus GNOME nautilus 3.24.1, GNOME Shell 3.24.2

Thank you very much

---

### Post by TheFu on 2017-09-19
Use rsync.
$ rsync --progress  {source-pattern} {target}

For any non-trivial amount of data being copied anywhere, rsync is **THE** tool.

I have no idea how to do this with any GUI tool. Don't use those much.

---

### Post by vasa1 on 2017-09-19
> **TheFu said:**
> Use rsync.
$ rsync --progress  {source-pattern} {target}

For any non-trivial amount of data being copied anywhere, rsync is **THE** tool.

I have no idea how to do this with any GUI tool. Don't use those much.There's *grsync*.

---

### Post by mc4man on 2017-09-19
If you want to Dnd to the Desktop (with the notify..) then drop into the Desktop folder instead on on the Desktop which gnome-shell doesn't particularly use..

---

### Post by garvied on 2017-09-19
Thanks to everyone, grsync or rsync and I know them but I want to be able to drop a file on the desktop and see the progress of the copy. As for opening the desktop folder is what I'm doing now but I wanted to know if it's possible to do it without having to open that folder, just drop the file and have the process appear somewhere.

---

