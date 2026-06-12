---
title: "Filezilla will not start / hangs on startup using Ubuntu 12.04"
date: 2013-03-01
forum: General Help
---

### Post by deefactorial on 2013-03-01
I'm running Ubuntu 12.04 Filezilla will not start. process is started in system monitor. But will not show up in system tray or window. I filed a bug with filezilla but no one has replied.[http://trac.filezilla-project.org/ticket/8374](http://trac.filezilla-project.org/ticket/8374)

[ATTACH=CONFIG]239569[/ATTACH]


 Any help would be great.
Thanks

---

### Post by deefactorial on 2013-03-01
I found the problem. It was related to a hanging nfs connection 
strace filezilla 
showed this line:
lstat("/mnt/eeepc", ^C <unfinished ...>

umount -l /mnt/eeepc 
fixed it.
Thanks.

---

