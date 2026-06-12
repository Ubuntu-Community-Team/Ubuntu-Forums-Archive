---
title: "deleting ldlinux.sys"
date: 2021-04-19
forum: General Help
---

### Post by JamButty on 2021-04-19
Sorry for the very basic question, but I am confused.
I inadvertently put system boot files onto an external backup disk and I want to delete them (I screwed up exactly like this guy [https://askubuntu.com/questions/1247079/permissions-how-do-i-delete-files-from-an-external-drive-that-requires-root-pe](https://askubuntu.com/questions/1247079/permissions-how-do-i-delete-files-from-an-external-drive-that-requires-root-pe))

I thought sudo should make ownership issues moot. Most I can delete e.g.:
```
$ ls /media/fred/Backups2/pics
blue-lowerleft.png   debian.jpg          red-upperleft.png
blue-lowerright.png  logo-50.jpg         red-upperright.png
blue-upperleft.png   red-lowerleft.png   TRANS.TBL
blue-upperright.png  red-lowerright.png
fred@fred-Inspiron-3847:~$ sudo rm -rf /media/fred/Backups2/pics
[sudo] password for fred: 
fred@fred-Inspiron-3847:~$ ls /media/fred/Backups2/pics
ls: cannot access '/media/fred/Backups2/pics': No such file or directory


```
but ldlinux.sys I can't touch

```
$ ls /media/fred/Backups2/ldlinux.sys
/media/fred/Backups2/ldlinux.sys
fred@fred-Inspiron-3847:~$ rm /media/fred/Backups2/ldlinux.sys
rm: cannot remove '/media/fred/Backups2/ldlinux.sys': Operation not permitted
fred@fred-Inspiron-3847:~$ sudo rm /media/fred/Backups2/ldlinux.sys
rm: cannot remove '/media/fred/Backups2/ldlinux.sys': Operation not permitted
fred@fred-Inspiron-3847:~$ sudo rm -f /media/fred/Backups2/ldlinux.sys
rm: cannot remove '/media/fred/Backups2/ldlinux.sys': Operation not permitted


```

I note that, while root is the owner, it has only read access to the file, which seems bizarre.

---

### Post by grahammechanical on 2021-04-19
Your not the first person to ask that question. May be the answer given 7 years ago will still work for you.

[https://unix.stackexchange.com/questions/166770/unable-to-delete-file-ldlinux-sys-from-a-partition](https://unix.stackexchange.com/questions/166770/unable-to-delete-file-ldlinux-sys-from-a-partition)

Information about the immutable bit. Apparently, once the immutable bit is set on a file even Root will not be able to delete the file.

[http://www.aboutlinux.info/2005/11/make-your-files-immutable-which-even.html](http://www.aboutlinux.info/2005/11/make-your-files-immutable-which-even.html)

Regards

---

### Post by JamButty on 2021-04-19
That did it, thanks!

---

