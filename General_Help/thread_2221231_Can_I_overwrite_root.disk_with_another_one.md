---
title: "Can I overwrite root.disk with another one?"
date: 2014-05-01
forum: General Help
---

### Post by emptycoder on 2014-05-01
I'm using Ubuntu 12.04 via wubi and I had some problems so I thought of copying root.disk and remove wubi and install Ubuntu back again (with same disk size) then overweight root.disk. would that work?

---

### Post by oldfred on 2014-05-01
Your 12.04 is the last offically supported wubi.
Wibi does not work with gpt partitioned drives which all new UEFI systems are.

You should be able to copy wubi's root.disk back in a new install and have your old install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

But if you like Ubuntu, it may be time to do a full partitioned install:
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

---

### Post by emptycoder on 2014-05-15
So sorry for my late reply, I want to thank you for your help, many thanks :)

---

