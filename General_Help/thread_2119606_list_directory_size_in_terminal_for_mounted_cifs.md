---
title: "list directory size in terminal for mounted cifs"
date: 2013-02-24
forum: General Help
---

### Post by twinturbotom on 2013-02-24
I mounted an apple time capsule in /etc/fstab as cifs type to /media/time_capsule.  I now want to look at directory file sizes to help me clean out the drive.

I usually use the command below to list human readable sizes for files and directories:

```
ls -lh
```

but all the directories show up with 0 size!  Not sure why / how to let me view directory size in terminal with ls.  Update an index?

thanks.

---

### Post by thermion on 2013-02-24
Try some of these commands while in /media/time_capsule:

[I]df -h

[/I]or

*du -hs **

---

### Post by prodigy_ on 2013-02-24
Find files and sort by file size:
```
find /media/time_capsule -depth -type f -exec stat -c "%s %n" {} \;|sort -rn|more
```

Find directories and sort by disk usage:
```
du /media/time_capsule|sort -rn|more
```

---

### Post by twinturbotom on 2013-02-24
du and find with sort works great, thanks. 
 I still don't understand why ls -l does this fir local directories and not for my mount.

---

### Post by thermion on 2013-02-24
This depends on the cifs implementation on the server. Some older versions of smbd produce this kind of behaviour when running ls or certain other tools.

---

