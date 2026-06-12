---
title: "console command hangs with no way to stop it"
date: 2017-10-16
forum: General Help
---

### Post by marchello_lippi2 on 2017-10-16
Hi all, 
How do I deal with situation when console command hangs with no way to stop it? 

For example, I ran 
```
scanimage -L
```
ok, that was my fault that I did it when usb scanner was not plugged in. 
I plugged in after I ran the command.. 

Now it hangs and killall does not help.

Is there any way to stop it without reboot?
Thanks ahead. 

```
$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
```

---

### Post by marchello_lippi2 on 2017-10-16
upd: ctrl+c does not help as well
either closing that console window and trying in another one
tried to plug usb scanner into another usb port, did not help.

---

### Post by marchello_lippi2 on 2017-10-16
upd: The process was in "D" mode as shown by ps aux, that's why even "kill -9" did not help. Reboot did help.

---

### Post by 1clue on 2017-10-16
sudo kill -9?

---

### Post by marchello_lippi2 on 2017-10-16
> **1clue said:**
> sudo kill -9?
This did not work for processes marked "D" in ps aux. Only reboot helped in my case.

---

### Post by ajgreeny on 2017-10-16
Perhaps Ctrl+D would have done so, though that may depend on whether the process requires the terminal itself to be open or not.

Ctrl+D usually closes the both terminal and any process running in it, but **scanimage** is not a command I have needed to use.

---

