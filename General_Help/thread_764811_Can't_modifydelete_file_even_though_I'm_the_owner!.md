---
title: "Can't modify/delete file even though I'm the owner!"
date: 2008-04-24
forum: General Help
---

### Post by svivian on 2008-04-24
I was just editing a file in KATE and got the message:
[b]The document could not be saved, as it was not possible to write to file:///home/scott/www/MMC/admin/events/edit.php.
Check that you have write access to this file or that enough disk space is available.[/b]

I have plenty of disk space and no problems saving other files. For some reason the permissions have changed in a weird way. I can't even do anything with sudo!

However, I ran **ls -l** on the folder and everything looks OK to me:
```
-rw-r--r-- 1 scott scott 2923 2008-04-24 13:15 add.php
-rw-r--r-- 1 scott scott 4194 2008-04-24 13:19 edit2.php
-rw-r--r-- 1 scott scott 4173 2008-03-17 20:12 edit.php
```
(*edit2.php* is a copy of *edit.php*, which I can write to fine, *add.php* is fine too.

I had a similar problem before, which was the beginning of a whole heap of filesystem problems. I booted in "safe mode" and no file system problems were reported.

Any ideas what the problem could be?

---

### Post by gsmanners on 2008-04-24
Make sure the parent folders are also +w (that one gets me a lot).

---

### Post by svivian on 2008-04-24
Yep, parent folders are fine. As I said, I can edit one file in the folder but not the other. And I can create new files, etc.

---

