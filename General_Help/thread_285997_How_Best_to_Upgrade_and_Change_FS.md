---
title: "How Best to Upgrade and Change FS?"
date: 2006-10-27
forum: General Help
---

### Post by Ubuntist on 2006-10-27
I've been using the Reiser file system, but I want to change to ext3 because 1) I've learned that Windows XP can be made to read and write ext3 and 2) I'm a little worried about long-term support for Reiser, given recent events.

I also want to upgrade from Dapper to Edgy.

What I'm planning to do is[LIST=1]
[*]Make a tar back-up of my files;
[*]Reformat my Ubuntu partitions in ext3;
[*]Do a clean install of Edgy; and
[*]Restore my files from the tar back-up.[/LIST]I'd really like to hear from someone more knowledgable than myself that there's an easier way to upgrade to Edgy and change to ext3.  Anybody?

---

### Post by x64Jimbo on 2006-10-27
You'll still want to back up your data, but there is a way to convert filesystems.
ConvertFS:
[http://freshmeat.net/projects/convertfs/](http://freshmeat.net/projects/convertfs/)

---

### Post by Ubuntist on 2006-11-01
Thanks very much!

---

