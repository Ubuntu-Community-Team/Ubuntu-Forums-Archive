---
title: "File permissions"
date: 2020-10-25
forum: General Help
---

### Post by oakridge on 2020-10-25
It is a probably a good while since I posted but I let myself be lured away by Windows 10.  I have seen the error of my ways and here I am again.

For the past few years I have been editing may very large collection of audio and e-books.  My sight is very poor and it is much easier for me to read books on my PC than on the printed page.  The files are in various forms - First Name, Title, Numbered, etc. but I want to consolidate them all into surname order.  For a while this Autumn I have been using Windows but it has started being silly like jumping back to the first entry in the directory when needing an item lower down. So I decided to return to Ubunto which was better at this job anyway and 'there's the rub'.  Microsoft has locked the files so I am unable to edit them in Ubuntu.  I have changed the permissions both in Microsoft and Ubuntu but to no avail.

Can you help please?

---

### Post by dinkidonk on 2020-10-25
You might want to supply information about which file types causes the problem and how exactly they are stored.

---

### Post by The Cog on 2020-10-25
When you say "edit" the files, are you just trying to rename them? That may be a different problem to editing the files themselves. The first thing that comes to my mind is that to rename a file, you need write permissions to the directory that contains them (in fact, all you are doing is editing the directory entry). 

Secondly, if the files are on an NTFS filesystem, this may have been mounted read-only unless Windows was shut down properly.

So it would help if you could post the permissions of one file you are having trouble with, and the directory that contains it, and the way its disk is mounted:
```
ls -l <filename>
ls -ld <containing directory>
mount | grep -v snap
```

---

