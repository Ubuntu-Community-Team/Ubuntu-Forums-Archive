---
title: "Can't delete a folder created with ntfs-fuse"
date: 2006-07-08
forum: General Help
---

### Post by linjiaoyang on 2006-07-08
I create a folder on an ntfs partition with ntfs-fuse, and now I can't delete it, either from Ubuntu or Windows, and everytime I boot it does the file system something check... What is the hardcore way to delete it?

---

### Post by vem0m on 2006-07-09
try loading ur file browser with sudo in terminal and atempt deletion

---

### Post by Anduu on 2006-07-09
Try this...

Go to System>Preferences>File Management>Behavior tab and check the box that says "Include a Delete command that bypasses trash"

Now right click the folder and choose delete rather than Trash

I know for me this is the only way I can delete things from my NTFS partitions.

---

