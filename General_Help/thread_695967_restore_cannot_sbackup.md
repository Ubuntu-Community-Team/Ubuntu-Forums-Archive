---
title: "restore cannot sbackup"
date: 2008-02-13
forum: General Help
---

### Post by pjvolders on 2008-02-13
Hi, I used simple backup to make backups of my home folder to my external hard disk. I formatted my hard drive feeling save with the backups, but now, I can't restore then! When I try to restore folder by folder, some folders work, but most don't. When I use the terminal, i get this error:

```
peejay@peejay-laptop:~$ gksu simple-restore-gnome
home/peejay/Documenten
  File "/usr/sbin/simple-restore-gnome", line 409, in restore
    self._do_restore( self.src, self.src )
  File "/usr/sbin/simple-restore-gnome", line 402, in _do_restore
    r.restore( tdir, src, dst )
  File "/usr/share/sbackup/srestore.py", line 97, in restore
    if os.path.exists(dst) and not filecmp.cmp(src, dst):
  File "/usr/lib/python2.5/filecmp.py", line 43, in cmp
    s1 = _sig(os.stat(f1))
OSError: [Errno 2] File or folder does not exist: '/home/peejay/Documenten/tmpYqYJ2C/home/peejay/Documenten/'
```

I do see a tmp****** folder wich i can only open with sudo nautilus, but it's empty...
Who can help me?

cheers,
PJ

---

### Post by pjvolders on 2008-02-13
solved, backup files were corrupt. Don't know why though...

---

