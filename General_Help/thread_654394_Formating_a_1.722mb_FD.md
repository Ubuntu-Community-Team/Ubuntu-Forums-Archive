---
title: "Formating a 1.722mb FD"
date: 2007-12-31
forum: General Help
---

### Post by Masteroc on 2007-12-31
Hey guys, i need to format a floppy for 1.722mb of space. How do i do this, i ran the command fdformat "/dev/fd0u1722" but it said something like: unknown path or filename. Is there any other way to format a floppy for 1.722mb?

Thanks

---

### Post by foolsh on 2007-12-31
```
fdformat "/dev/fd0u1722"
```

does not exist is that a typo?

```
fdformat /dev/fd0
```

should work

---

### Post by Masteroc on 2007-12-31
fdformat /dev/fd0 will format a floppy for 1.44mb, but like the title stated, im trying to format a floppy for 1.722mb. fdformat /dev/fd0u1722 does or did exist, it worked with a lot of the older distros. Im just trying to see if ubuntu has a command for formating a floppy for 1.722mb.

Thanks

---

### Post by -grubby on 2007-12-31
from the man page:
```
    The  generic  floppy  devices, /dev/fd0 and /dev/fd1, will fail to work
       with fdformat when a non-standard format is being used, or if the  for&#8208;
       mat  has  not been autodetected earlier.  In this case, use setfdprm(8)
       to load the disk parameters.
```

---

### Post by Masteroc on 2007-12-31
Thanks nathangrubb, but since i am a bit nubish when it comes to linux, how would i use that command?

---

