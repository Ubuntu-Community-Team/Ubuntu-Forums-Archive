---
title: "Damaged txz archive - extract as much as possible"
date: 2013-05-21
forum: General Help
---

### Post by Bliepo32 on 2013-05-21
Hey everyone,

A few days ago, I made a back-up of my harddisk using tar since it was beginning to fail. The command I used was along the lines of "tar cvpJf backup_sdb1.txz /media/sdb1/". Now I tried to extract the archives, but I get IO errors like these (translated myself, so might be incorrect):
```
xz: (stdin): Read error: Input-/outputerror
tar: Unexpected end-of-file in archive
tar: Unexpected end-of-file in archive
tar: Error is not recoverable: exiting now
```

I simply want tar to try as much as possible, even if files are damaged. Is there a way to do this? Or did I simply lose almost all of my data?

---

### Post by dino99 on 2013-05-21
the 'v' is scary, as it return unwanted errors; and saving the absolute path is not the best idea.
[http://askubuntu.com/questions/78043/sudo-tar-cvpzf-exiting-with-failure-due-to-previous-error](http://askubuntu.com/questions/78043/sudo-tar-cvpzf-exiting-with-failure-due-to-previous-error)

---

### Post by Bliepo32 on 2013-05-21
> **dino99 said:**
> the 'v' is scary, as it return unwanted errors; and saving the absolute path is not the best idea.
[http://askubuntu.com/questions/78043/sudo-tar-cvpzf-exiting-with-failure-due-to-previous-error](http://askubuntu.com/questions/78043/sudo-tar-cvpzf-exiting-with-failure-due-to-previous-error)

I already made the back-up and that went fine. But **extracting** the back-up is giving me errors.

---

### Post by Bliepo32 on 2013-05-27
BUMP
Anyway to recover the content of this archive at all?

---

