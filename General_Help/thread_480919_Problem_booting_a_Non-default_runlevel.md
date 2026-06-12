---
title: "Problem booting a Non-default runlevel"
date: 2007-06-21
forum: General Help
---

### Post by mustali on 2007-06-21
I am having trouble loading a Non-default runlevel from the Kernel options in the menu.lst file. In one old post ([http://ubuntuforums.org/showthread.php?t=3550](http://ubuntuforums.org/showthread.php?t=3550)), it was suggested that the runlevel be added to the menu.lst file in the kernel line. But no matter where I put '3'  in the kernel line, the default runlevel 2 is loaded.

This is a snippet of my menu.lst for which I want runlevel 3 activated:
```

title           Ubuntu, kernel 2.6.20-16-386 Undocked
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=14b93506-80ff-41b5-b2d6-d7a69f753c1d ro quiet splash 3

```

Has anything changed recently in the way runlevels are specified in GRUB?

Any help would be appreciated. Thanks.

---

### Post by mustali on 2007-06-25
anyone?

---

