---
title: "Can't see trash in root after sudo Nautilus"
date: 2013-03-25
forum: General Help
---

### Post by botot on 2013-03-25
Hi,

I did a pretty stupid thing to run "sudo Nautilus", and deleted about 160GB of files in it...
And then I can't reclaim the space in that HD. Later I tried to use "gksudo Nautilus" to see the trash but got an error message: "The folder contents could not be displayed. Sorry, could not display all the contents of "trash": Operation not supported".

Is there any way around this to get the hard disk space back?

Thanks a lot for helping!

---

### Post by CatKiller on 2013-03-26
You can use something like baobab to establish whether the files are in root's Trash or your own (or just delete them both). Use **rm** on the command line in the appropriate place to remove them. You'll need the **-r** option. I believe the user's trash is in ~/.local/share/Trash and root's is /root/.local/... There will also be a Trash folder in the root directory of any other attached filesystems.

---

