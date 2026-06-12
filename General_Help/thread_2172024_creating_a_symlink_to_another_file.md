---
title: "creating a symlink to another file"
date: 2013-09-02
forum: General Help
---

### Post by wheelie207 on 2013-09-02
I am trying to install a driver for my canon printer and it relies on a file libcupsys2 and ubuntu has gone to a different file called libcups2.
I know that I can symlink libcupsys2 >> to libcups2, but where and in what directory should I locate my symlink to libcups2.

I run Ubuntu 12.04 LTS on a desktop with 4 gigs ram and 1 TB HD...

Thanks
Harold

---

### Post by Crusty Old Fart on 2013-09-03
It should work from anywhere If you put it in:
```

/bin

```

---

### Post by deadflowr on 2013-09-03
Here's an old(closed) thread that deals with the libcupsys2 to lipcup2 problem.
[http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098)

Don't know how helpful it will be as I don't know what printer you're using.

---

### Post by wheelie207 on 2013-09-04
> **deadflowr said:**
> Here's an old(closed) thread that deals with the libcupsys2 to lipcup2 problem.
[http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098)

Don't know how helpful it will be as I don't know what printer you're using.

I looked at that link and even though I need to install drivers for MX870 canon printer, it still helpful.

Thanks

---

