---
title: "Recycle Permissions"
date: 2008-05-01
forum: General Help
---

### Post by Clayton South on 2008-05-01
Hi Everyone,

Here's my problem: In Hardy I can't empty the recycle bin because a folder inside can't be removed. I tried altering the permissions of the file, but they didn't seem to take effect and now my recycle bin isn't emtpy and seemingly can't be emptied.

How do I fix this so that I can delete the file?

Thanks!

-Clayton South

---

### Post by ashikahamed on 2008-05-01
Try removing it from command line.
sudo rm -r "path to the folder".The location of trash folder in Hardy is '~/.local/share/Trash/files/'
[COLOR="Red"]PLEASE BE CAREFUL WHILE USING 'rm'[/COLOR].

---

### Post by Clayton South on 2008-05-01
> **ashikahamed said:**
> Try removing it from command line.
sudo rm -r "path to the folder".The location of trash folder in Hardy is '~/.local/share/Trash/files/'
[COLOR="Red"]PLEASE BE CAREFUL WHILE USING 'rm'[/COLOR].

This works great! Thanks!

-Clayton South

---

