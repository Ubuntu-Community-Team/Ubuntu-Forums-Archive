---
title: "show files of one folder into another folder in read-only mode"
date: 2012-10-16
forum: General Help
---

### Post by ubh on 2012-10-16
I need to be able to **read-only** files of /media/[COLOR=Orange]folder/[/COLOR] into /home/username/[COLOR=Cyan]folderwithanothername/[/COLOR].

I tried with```
ln -s  /media/folder/ /home/username/folderwithanothername/
```and the hierarchy is /home/username/[COLOR=Cyan]folderwithanothername/[/COLOR][COLOR=Orange]folder/[/COLOR], but I want the files to be shown directly under /home/username/[COLOR=Cyan]folderwithanothername/[/COLOR].
Oh, I also need this thing to be permanent.

---

### Post by LewisTM on 2012-10-16
I assume you want to make the filesystem readonly and make it available in another folder.

This can be accomplished with this entry in /etc/fstab
```
/media/folder /home/username/folderwithanothername none bind,ro 0 0
```
Also make sure the (empty) target folderwithanothername exists.

That's it! Cheers!

---

### Post by ubh on 2012-10-17
That's just exactly what I was looking for, but... there's a "but": with your command I got folderwithanothername in read-write mode and I needed in read-only.
The solution I've found is removing entry from fstab and adding a "double mount" in rc.local like in this [Arch Linux thread.]("https://bbs.archlinux.org/viewtopic.php?pid=895731#p895731")

P. S.: why can't I change the thread title adding to it the tag [SOLVED]? Where am I wrong?

---

