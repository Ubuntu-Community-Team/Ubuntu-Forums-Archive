---
title: "Su Command"
date: 2006-11-18
forum: General Help
---

### Post by koulanji on 2006-11-18
I can't seem to run the superuser command (su) from the termainal. Whenever I do so, I get the following error

axisaudio@axisaudio-desktop:~$ su
Password: 
su: Authentication failure
Sorry.

My root password for synaptic, and whatever else works, except in the terminal when i try to login as a superuser. any help would be appreciated.

I'm running edgey eft Thanks.

---

### Post by 900i on 2006-11-18
It's "sudo command".  The root user account is disabled in Ubuntu.

---

### Post by taurus on 2006-11-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2006-11-18
If you want to log in as root user, do ```
sudo -s
``` but you shouldn't have to. Read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

