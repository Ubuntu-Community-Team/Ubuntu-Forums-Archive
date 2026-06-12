---
title: "chmod doesn't work after restart?"
date: 2007-01-03
forum: General Help
---

### Post by sefir on 2007-01-03
Hi all,

I would like to remove the rwx permissions for a folder in /media/hda2, owned by root and plugdev.  I did 

```
 sudo chmod g= folder/
```

and get the appropriate

```
 drwx------ 2 root plugdev
```

but after i restart my computer, it goes back to 

```
 drwxrwx--- 2 root plugdev
```

am I doing something wrong, or is this just not allowed? 

thanks.
ps i'm on edgy btw.

---

