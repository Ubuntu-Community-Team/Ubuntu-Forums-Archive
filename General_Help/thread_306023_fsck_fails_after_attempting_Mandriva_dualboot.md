---
title: "fsck fails after attempting Mandriva dualboot"
date: 2006-11-24
forum: General Help
---

### Post by Jenda on 2006-11-24
Hello :)

I get this error message each bootup, with a recovery root console which I have to manually exit each time.
This has happened after I installed Mandriva and tried to share /home partitions (hda2).

> jenda@Elu:~$ cat /var/log/fsck/checkfs 
Log of fsck -C -R -A -a 
Fri Nov 24 12:01:31 2006

fsck 1.39 (29-May-2006)
/dev/hda2: clean, 29562/4643968 files, 8254944/9277537 blocks
fsck.ext3: Unable to resolve 'UUID=d9e354ef-18c9-4a5e-800d-e91e9252b2cd'
fsck died with exit status 8


Any idea what the problem could be?

---

