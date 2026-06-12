---
title: "Delete corrupt file-folder from NTFS External disk"
date: 2018-07-11
forum: General Help
---

### Post by 1nikolas2 on 2018-07-11
Hello everyone. I had a file on my external HDD which was called install.txt. Now for some reason this file is corrupted and it appears as a folder. I don't need that file anymore so I want to delete it. It's not actually a folder because when I delete it as folder with rm -R it says "No such file or directory". When I delete it with rm it says that it's a folder. I can't rename, move or delete using the gui (I get "No such file or directory"). How do I get rid of that file? 


Some useful screenshots:

[IMG]https://i.imgur.com/t84meK9.png[/IMG]

[IMG]https://i.imgur.com/cyE7CKb.png[/IMG]

[IMG]https://i.imgur.com/xZnlOa3.png[/IMG]

---

### Post by col48 on 2018-07-11
Perhaps you can move it?

So Create a new folder (I'll call it todel).  Move install.txt into it, then try deleting todel.

---

### Post by 1nikolas2 on 2018-07-11
> **col48 said:**
> Perhaps you can move it?

So Create a new folder (I'll call it todel).  Move install.txt into it, then try deleting todel.


I can't move, rename or delete:

```
nikolas@Nick-Ubuntu:/media/nikolas/Nick HD$ mv install.txt Test
mv: cannot move 'install.txt' to 'Test/install.txt': No such file or directory

```
Anyway thanks for your reply

---

### Post by vanadium on 2018-07-11
Have the ntfs file system checked, preferably by connecting it to a Windows machine and running the drive checking tools. Preferably, attempt to remove the file/folder in Wiindows right after checking it there.

If you don't have Windows, try checking the file system with ntfsfix: after that you may be able to delete the file/folder.

---

### Post by dragonfly41 on 2018-07-11
This is a hunch. Since the file is in ntfs folder I note that the filepath contains a space.
/media/nikolas/Nick HD

Can you use quotations in your filepath or alternatively change pathname to
/media/nikolas/Nick_HD

---

### Post by 1nikolas2 on 2018-07-11
> **vanadium said:**
> Have the ntfs file system checked, preferably by connecting it to a Windows machine and running the drive checking tools. Preferably, attempt to remove the file/folder in Wiindows right after checking it there.

If you don't have Windows, try checking the file system with ntfsfix: after that you may be able to delete the file/folder.

ntfsfix didn't work. Windows did read the file as txt but as soon as I opened it it got deleted. I didn't think that windows would work that's why I didn't try. Thank you!

---

### Post by 1nikolas2 on 2018-07-11
> **dragonfly41 said:**
> This is a hunch. Since the file is in ntfs folder I note that the filepath contains a space.
/media/nikolas/Nick HD

Can you use quotations in your filepath or alternatively change pathname to
/media/nikolas/Nick_HD

It doesn't matter. Both Ubuntu and Debian on Rasbpberry pi can read this name

---

### Post by col48 on 2018-07-11
Perhaps knowing the permissions according to Ubuntu may illuminate?  Frankly, it's beyond me.

In a Terminal,
ls -al /media/nikolas/Nick HD
(you'll have to esc the space in the folder name using \)
and post the result.

---

### Post by vanadium on 2018-07-12
> **1nikolas2 said:**
> ntfsfix didn't work. Windows did read the file as txt but as soon as I opened it it got deleted. I didn't think that windows would work that's why I didn't try. Thank you!
The issue is that the ntfs file system format is proprietary. The only tools that can check an ntfs partition perfectly are windows tools. ntfsfix can do some repair under linux, but not with the depth Windows can.

---

### Post by yancek on 2018-07-12
> I didn't think that windows would work that's why I didn't try

That seems a little bizarre to me.  If you want to make changes of any kind on an ntfs filesystem, first use windows.  You don't really need to worry about the reverse as a default windows won't read Linux.
If there is corruption of any king on an ntfs (or other) windows filesystems, the first step is to use windows.  The only time you try any Linux is if your windows will not boot.

ntfsfix is 'usually' available on 'most' Linux systems and 'usually' will be able to make some 'minor' repairs and there is no reason to expect more.

---

