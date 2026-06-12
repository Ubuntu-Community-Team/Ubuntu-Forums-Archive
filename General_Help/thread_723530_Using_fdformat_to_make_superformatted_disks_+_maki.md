---
title: "Using fdformat to make superformatted disks + making files bootable"
date: 2008-03-13
forum: General Help
---

### Post by Yes on 2008-03-13
Is it possible to use fdformat to make a superformatted (1.77 MB) floppy?  I know about superformat, but unfortunately I can't use that.

Also, I read somewhere about putting img files on a partition and making the partition bootable.  Then, the BIOS would boot from the img files instead of the normal OS on the partition.  Is that at all possible, and how would I go about doing that?

Thanks!

---

### Post by the-edmeister on 2008-03-13
I have done it on Windows using a program I got from here. (I'm new to Linux.)
[http://www.serverelements.com/naslite.php](http://www.serverelements.com/naslite.php)
Scroll to the bottom of that page for Linux instructions.
```
fdformat /dev/fd0u1722

``` For a 1722 kB floppy.

Hope that is helpful.


Ed

---

### Post by Yes on 2008-03-14
Cool, that did it.  Thanks!

---

