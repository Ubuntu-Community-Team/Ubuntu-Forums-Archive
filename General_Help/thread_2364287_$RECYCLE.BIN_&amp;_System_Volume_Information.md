---
title: "$RECYCLE.BIN &amp; System Volume Information"
date: 2017-06-21
forum: General Help
---

### Post by mac187 on 2017-06-21
Hi, i have 2 HDD

The first HDD i have made 2 partition with Ubuntu and Windows alongside
The second HDD i only have to storage my files

Problem is:

I use Ubuntu, i saw that in second HDD it was files named with these files:

$RECYCLE.BIN
System Volume Information
.Trash-1000

What are these? Can i delete them?

i made a .hidden files and added $RECYCLE.BIN and System Volume Information to the file

Then i shut down ubuntu and rebooted to Windows, and THEN after that i rebooted to Ubuntu and i saw that Another directory , then i mean it made a second folder named System Volume Information ??

How can i make it not happen everythime i switch between ubuntu and windows, can i just delete these files or is it anything else i can do with that?

Thanx for help !

---

### Post by Impavidus on 2017-06-21
When you use the graphical file manager to remove a file, it's not deleted, but moved to a trash directory on the same partition where the file already was. Windows' trash directory is named $RECYCLE.BIN, Ubuntu's trash directory is named .Trash-1000 (the number 1000 is a reference to your user ID). Those directories are created automatically. Best to leave them alone, they do no harm. Deleting them does no harm either, they will just be recreated when needed. I expect System Volume Information is something similar.

---

