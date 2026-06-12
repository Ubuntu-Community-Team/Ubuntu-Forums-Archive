---
title: "Gutsy &gt;&gt; S2disk broke"
date: 2007-10-18
forum: General Help
---

### Post by wastedfluid on 2007-10-18
Hello.

Acer 5100, running 7.10 Gutsy.

```

wastedfluid@fluid:~$ sudo s2disk
s2disk: Could not stat the resume device file. Reason: No such file or directory
wastedfluid@fluid:~$



```

/etc/uswsusp.conf + /etc/fstab

```

wastedfluid@fluid:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform

wastedfluid@fluid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=580d2a5b-d2e9-4fab-ae70-9a4484567c8a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=681b2d44-05a8-4350-803a-e788cc47e8ba /home           ext3    defaults        0       2
# /dev/hda5
UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f none            swap    sw              0       0
/dev/hdb        /media/

```

Any idea where to start?

Had a thread in Development, but it's closed now.

Voila.

thanks!!

---

### Post by wastedfluid on 2007-10-19
Anyone?

Bump :/

---

### Post by twright on 2008-03-04
in both files change UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f to /dev/hda5

---

