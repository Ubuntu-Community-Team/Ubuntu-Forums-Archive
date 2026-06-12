---
title: "Ubuntu Startup Failure"
date: 2007-06-09
forum: General Help
---

### Post by icon_msr on 2007-06-09
I am using Windows XP Home and after using Wubi to install Ubuntu, I am experiencing problems starting Ubuntu. When I boot up after the Ubuntu splash screen, the following error occurs:

Fsck died with exit 8

File system check failed,

and later in the command lines it asks me to manually type, "apt-get install apt" (but it fails). What can I do to solve this problem and use Ubuntu successfully?

Thanks

---

### Post by ago on 2007-06-09
That's usually due to a hard reboot that has corrupted the filesystem. At the moment wubi does not tolerate hard reboots too well. You can recover the data but it's probably easier to reinstall

---

