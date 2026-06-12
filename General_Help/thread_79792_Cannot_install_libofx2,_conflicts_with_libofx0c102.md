---
title: "Cannot install libofx2, conflicts with libofx0c102"
date: 2005-10-20
forum: General Help
---

### Post by oblib on 2005-10-20
I have just been updating everything to breezy, and it came back with this error:
```

Preconfiguring packages ...
(Reading database ... 121635 files and directories currently installed.)
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

```

So I looked in Synaptic, and sure enough, libofx0c102 is installed. From the error, it seems Synaptic will not overwrite the file opensp.dcl because libofx0c102 (0c102 from now on, and libofx2 will be just 2) is using it. 

So I marked 0c102 for removal and hit 'Apply' but it came back with the same error. It won't let me unmark 2 for installation. When I try to apply changes (remove 0c102 and install 2) it chokes on installing 2, without removing 0c102. How can I resolve this? The lib is related to gnucash I believe.

Thanks

---

### Post by oblib on 2005-10-20
Sorry, this has already been discussed
[http://ubuntuforums.org/showthread.php?t=76766](http://ubuntuforums.org/showthread.php?t=76766)

---

