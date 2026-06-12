---
title: "trash size information"
date: 2007-11-25
forum: General Help
---

### Post by herorev on 2007-11-25
I need more disk space, and my trash can has over 50GB of data. But I don't want to delete everything, as that would defeat the purpose of having a trash can. I want to learn what's taking up so much space and just delete it.

This seems like a very simple task, but I can't figure out a way to do it. Konqueror's "File Size View" (FSView) would be perfect, but it doesn't work with the trash can. I can't use command line tools to get a listing of directory sizes because they don't work with the trash: protocol. I can't just browse to the .Trash directories, because I have a *lot* of partitions and it would be very time consuming to browse to all of them.

Are there any tools I can use to learn what's taking up so much space?

---

### Post by nick_h on 2007-11-25
Command line tools should work in .Trash - there is nothing special about it.  Try:
```
ls -lS .Trash/
```
Nautilus can list the .Trash directory and order by size.  You just have to enable the hidden files option.

---

### Post by foxholeunder on 2007-11-25
As long as your drive/partitions are all owned by you the tray icon for Trash should list all items and their file size. From the command line you will only see items for the .Trash folder residing in the partition you are currently in and will have to manually explore each one. But the GUI view for Trash should show all .Trash folders lumped into one view that you own. 

You have to own all of the .Trash folders to see everything residing in Trash though. Else you will just see what you own.

EDIT:
You will need to enable detailed view in in the GUI Trash view to see file sizes listed.

---

