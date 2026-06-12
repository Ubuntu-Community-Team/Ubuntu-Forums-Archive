---
title: "Auto Shutdown and Power-On utilities for Intel NUC"
date: 2017-12-26
forum: General Help
---

### Post by mpspot on 2017-12-26
Hi 
I have an Intel NUC running Ubuntu 16.04
I would like to schedule it to Automatically Power On and turn off each day/night.
I am using qshutdown to attempt the power down however that fails when trying to schedule it for some reason.
And the Intel NUC BIOS settings for auto Power-On no longer work either (confirmed on an Intel Forum).
Does anyone know of any GUI utilities for me to use as I am not familiar with scripting yet.
Thanks.

---

### Post by leunam12 on 2017-12-27
Maybe the reason qshutdown is not working is because you have not changed your sudoers file
to allow shutdown without password. If qshutdown never asks for a password then go to the
terminal and type: ```
sudo visudo
```
then go to the end of the file and type ```

yourusername ALL=(ALL) NOPASSWD: /sbin/shutdown
```
save it and close. Log out and log back in or reboot and qshutdown should work.

---

### Post by mpspot on 2017-12-27
Thanks. I’ll try.

---

