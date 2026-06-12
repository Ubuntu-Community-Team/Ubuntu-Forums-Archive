---
title: "Boot Crash on 7.10. unable to execute /bin/sh"
date: 2007-12-22
forum: General Help
---

### Post by azuth on 2007-12-22
Hey;

I have a constant boot error such as


init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS process (2456) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Not a directory
init: rc-default process (2457) terminated with status 255

i started my system with live cd.. tried to copy bin/sh on livecd to my primary disc.. but it said "you do not have permission to do this"

so i opened terminal and wrote

**sudo su -**

and logged as root.

but now i can see only "dash" when i "dir"

is there anyway to help me beyond "reinstall"?

---

### Post by andrewcmcardle on 2007-12-23
Hate to say it, but reinstall seems a good idea. Perhaps try booting from a live cd like [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") to see if you can salvage any files in your home directory.

---

