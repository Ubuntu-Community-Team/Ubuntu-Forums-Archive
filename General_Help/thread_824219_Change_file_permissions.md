---
title: "Change file permissions"
date: 2008-06-09
forum: General Help
---

### Post by lloydlloyd on 2008-06-09
I have recently done a reinstall of Ubuntu. I backed things up onto an external harddrive and then reinstalled and transferred the files back into my home directory. the only problem now is that any of the files I have transferred are restricted to the root user. ie I can open them as my regular login, but can't make changes. I was wondering if there was a way of changing a big group of files to be fully usable/changeable by my regular account. 
I have a pile of documents that I want to be able to just get access to.
I have hit alt+f2 and typed in gksudo nautilus to get access to a couple of them, but it doesn't seem to transfer the permissions to ALL the files in a folder, for example.

Any help would be greatly appreciated.

lloydlloyd.....

---

### Post by ibutho on 2008-06-09
You can use the chown command in a terminal e.g.
```
chown -R someuser:somegroup /path/to/dir
```

---

### Post by bluepowder7 on 2008-06-09
in terminal, use the chown command.  typing "man chown" gives you the manual, and an example on how to set the permissions.

---

