---
title: "cp Terminal Error"
date: 2013-09-11
forum: General Help
---

### Post by Cos_Marchy on 2013-09-11
Hi guys, 

When I try and copy a file using the terminal using this:

> cp -r /usr/lib/python2.7/config/libpython2.7.a ~/src/Crosstool/co/lib

I get this error: 

> cp: not writing through dangling symlink

does anyone know what I am doing wrong?

---

### Post by ajgreeny on 2013-09-11
Can you show the output of ```
ls -l /usr/lib/python2.7/config/libpython2.7.a
``` and ```
ls -l ~/src/Crosstool/co/lib
``` I suspect one of those pathways just points to a symlink.

---

### Post by Cos_Marchy on 2013-09-12
Thanks for your reply ajgreeny,

The outputs are as follows

```
ls -l /usr/lib/python2.7/config/libpython2.7.a
>>
*-rwxrwxrwx 1 root root 17439192 Apr 10 07:28 /usr/lib/python2.7/config/libpython2.7.a*
```

 and 

```
ls -l ~/src/Crosstool/co/lib
>>
*lrwxrwxrwx 1 cosmarchy cosmarchy 31 Sep 11 20:32 libpython2.7.a -> python2.7/config/libpython2.7.a*

```

Does this help?

Thanks

---

### Post by ajgreeny on 2013-09-12
I think it may, but I have to admit I have a different output to those on my machine and do not get the >> which suggests the second one is a link, not the actual file.  The l in the permissions list **lrwxrwxrwx **is for link.

I have no idea how you can solve this I'm afraid.

---

