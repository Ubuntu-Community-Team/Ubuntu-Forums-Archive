---
title: "CIFS VFS: Error 0xfffffff3 on  /.Trash-1000"
date: 2008-07-08
forum: General Help
---

### Post by brianafischer on 2008-07-08
Hello,

I am running Ubuntu Hardy with all updates to date.  I am attempting to rid my syslog of errors and noticed the following rrrors in /var/log/syslog:

```
toshiba kernel: [52226.003975]  CIFS VFS: Error 0xfffffff3 on cifs_get_inode_info in lookup of /.Trash-1000/files
```

I found a work-around [here]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-March/000863.html")

It looks like the user removed the .Trash-1000 directory.  I am not sure if this is the proper solution.  I have an autofs mount via CIFS to another Hardy machine named MythHD (samba share).  The MythHD machine has the following mount point:

```
/dev/sdd1 on /myth type ext3 (rw) []
```

/myth/.Trash-1000 is giving this error on my local system (Toshiba).  My intuition tells me that if I delete the "/myth/.Trash-1000" directory that the trash bin won't work for the /myth mount.

Any advice on how to properly correct this issue?

Thanks in advance

---

### Post by brianafischer on 2008-07-20
Any help here?

---

