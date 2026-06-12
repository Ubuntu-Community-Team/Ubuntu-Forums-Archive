---
title: "Ubuntu and windows sharing permissions"
date: 2024-07-12
forum: General Help
---

### Post by marklyn on 2024-07-12
I'm having an issue with Windows or Ubuntu permissions and can't remember the fix for this that I found a couple of years ago.
I have a Windows 11 drive shared (everyone).
In Ubuntu I can use file to connect to the drive (permanent connection).  In Ubuntu file I can see files, folders, etc.
But I can't write something new to the shared drive.
I seem to remember there was some file in ubuntu that I had to modify or add some lines to that allowed this.
Can anyone point me in the right direction to a document that has instructions for this?
This time I'll document this for future needs :)

---

### Post by currentshaft on 2024-07-12
You likely need to install ntfs-3g and fuse packages to access Windows filesystems.

---

### Post by marklyn on 2024-07-12
Thanks.  I'm going to keep looking.  So I can 'access' the shares, just can't write new stuff to them.
 It was something fairly simple I believe, editing a file or something.  If I can't find it, I'll investigate the path you mentioned.
Do you happen to have a link I can check out for the solution you mentioned.  I'll google it but sometimes I go down the wrong rabbit hole with so many results.

---

### Post by #&amp;thj^% on 2024-07-12
Perhaps this? [https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)

---

### Post by Morbius1 on 2024-07-12
What is missing from your original post is where this Windows 11 machine is located.

Are you trying to connect to and write to a SMB share on a **separate** Win11 box somewhere on your local lan?

Are you trying to connect to a Windows 11 partition on the **same machine** in a Linux / Windows dual boot?

Or is this a redo of your Win11 host running **VMWare** with Ubuntu as a VMWare guest that you had a few years ago.?

---

