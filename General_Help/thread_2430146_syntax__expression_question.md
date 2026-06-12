---
title: "syntax / expression question"
date: 2019-10-28
forum: General Help
---

### Post by croyle on 2019-10-28
hi everyone,
I am not sure exactly what the correct term for this is that is why I used the names I did in the title of this post.  I came across two values while researching udev rules and was hoping someone could tell me what they mean?  Or what there called so I can research them more.  I am familiar with wildcards *[]? but not these %k and %s they seam to have something to do with file systems and also got lots of php errors when I tried searching them but I think that has more to do with the search bar reading them.  Well any names or really anything would be great.
Thank you,
Jason

---

### Post by cruzer001 on 2019-10-28
This may shed some light on the subject

[http://man7.org/linux/man-pages/man1/date.1.html](http://man7.org/linux/man-pages/man1/date.1.html)

---

### Post by TheFu on 2019-10-28
```
$ man udev
```
explains.

```
       $kernel, %k
           The kernel name for this device.

       $attr{file}, %s{file}
           The value of a sysfs attribute found at the device where all keys
           of the rule have matched. If the matching device does not have such
           an attribute, and a previous KERNELS, SUBSYSTEMS, DRIVERS, or ATTRS
           test selected a parent device, then the attribute from that parent
           device is used.

           If the attribute is a symlink, the last element of the symlink
...
```

I can't imagine what php has to do with anything.  Nobody would ever use php for a udev need.

---

### Post by Holger_Gehrke on 2019-10-28
Those are string substitutions. You can find a list of the existing substitutions and their meanings at [https://www.freedesktop.org/software/systemd/man/udev.html](https://www.freedesktop.org/software/systemd/man/udev.html) just before the end of the document.

Holger

---

