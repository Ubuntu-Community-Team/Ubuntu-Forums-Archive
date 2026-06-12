---
title: "[SOLVED] New user help with dpkg error please"
date: 2008-06-25
forum: General Help
---

### Post by ednap on 2008-06-25
Just installed Ubuntu to an old laptop and had a lock-up when installing updates via update manager.

After reboot I am now getting the following error when I run update manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

When I open a terminal window and type in dpkg --configure -a Ireceive an error stating super user status is required.

When I type su I am asked for a password but the user password I set during initial installation is rejected.

Any help appreciated.

Thanks.

Ed

---

### Post by lisati on 2008-06-25
[LIST=1]
[*]Go to "Applications"->"Accessories"->"Terminal"
[*]Type in ```
sudo dpkg --configure -a
``` You might get asked for a password - type it in as usual, and don't worry if it doesn't show, this is normal and is a security precaution
[/LIST]

---

### Post by dexter.deepak on 2008-06-25
try "sudo dpkg --configure -a" (without quotes)
in ubuntu, we dont use su .

---

### Post by lizzard on 2008-06-25
```
sudo dpkg --configure -a
```should do it.
The "su" command would change to the root account which is disabled by default in Ubuntu. To run commands with root privileges you need to use "sudo" which will prompt for your user password.

---

### Post by ednap on 2008-06-28
Thanks managed to sort it out :-)

---

