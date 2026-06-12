---
title: "Error log? Why did a program crash?"
date: 2019-03-12
forum: General Help
---

### Post by iamtheeggman2 on 2019-03-12
Hi,

Not long after booting into the desktop a popup error message tells me that a program encountered a problem, that it is not the terminology used but I don't have that message in front of me as I write this.  Anyway as far as I know I have not installed any software on the computer as I don't have access to the Internet. However I have tried to use a couple of WiFi devices. So possibly it is trying to use any software already on the machine. 

But anyway, it's frustrating to have this error message and not even know what program is crashing? Where do you find it? I tried looking for logs but I found none.

Thanks in advance

---

### Post by dragonfly41 on 2019-03-12
If you see any crash error logs in /var/crash .. delete them.

---

### Post by deadflowr on 2019-03-12
Look in /var/crash.
That's the location for crash reports.
Typically it'll list the name of the crashed program in the title.

---

### Post by iamtheeggman2 on 2019-03-16
Hi it has one file and it says

_usr_sbin_lightdm. 0 crash

Also it won't let me delete it.

---

### Post by speartip on 2019-03-16
> **iamtheeggman2 said:**
> Also it won't let me delete it.

You need to have elevated privileges to remove root files.
Open a terminal & type,
```
cd /var/crash
```
then:
```
sudo rm *nameoffile*
```
replacing nameoffile with the file you wish to delete.
See if your problem now disappears.

---

