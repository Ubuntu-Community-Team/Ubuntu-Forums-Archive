---
title: "Symbolic Folder"
date: 2013-02-20
forum: General Help
---

### Post by cclloyd9785 on 2013-02-20
How can I create a symbolic folder, where the files in that folder is actually somewhere else.

EX: 

I want a folder at /Backups/Michael

but that Michael folder is actually at /media/michael/Backups/Backups/Michael

Because I'm trying to host a time machine backup disk for my macs but I get an error.  The only time I've been able to get it to work is when it was on the same hard drive as Ubuntu, so I am hoping this will work.

---

### Post by The Cog on 2013-02-20
You make a symlink to a folder the same way as you would to a file:
```
ln -s realName linkName
ln -s /media/michael/Backups/Backups/Michael /Backups/Michael
```

---

### Post by Durr on 2013-02-20
A regular symbolic link will work for a directory. In your case, the command would be:
```
ln -s /media/michael/Backups/Backups/Michael/ /Backups/Micheal
```Where the first folder is the actual location and the second is the link you want.

---

### Post by steeldriver on 2013-02-20
you could also consider using a bind mount

---

