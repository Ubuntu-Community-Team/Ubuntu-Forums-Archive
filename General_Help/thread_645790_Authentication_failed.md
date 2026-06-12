---
title: "Authentication failed"
date: 2007-12-20
forum: General Help
---

### Post by Charkel on 2007-12-20
Hello, I get a yellow box saying "Authentication failed" when I try to login.

I have tried to change the password of the user using "passwd *username*" and it tells me that it succeed. But afterwards I can't login with ctrl + D either. What's wrong? :S

---

### Post by Charkel on 2007-12-20
No one knows? I would really like to get my laptop working again :S

---

### Post by taurus on 2007-12-20
When you are at the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in with your username and password.  Then, post the output of this command here.

```
df -h
```

---

### Post by Charkel on 2007-12-21
> **taurus said:**
> When you are at the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Log in with your username and password.  Then, post the output of this command here.

```
df -h
```

Filesystem    Size    Used    Avail    Use%    Mounted on
/dev/sda1    15G    2.16G    502M   16%    /
varrun       502M    16K      502M    1%    /var/run
varlock       502M    0      502M    0%    /var/lock
udev          502M    64K      502M    0%    /dev
devshm      502M    0         502M    0%    /dev/shm
lrm             502M    16K      502M    1%    /lib/modules/2.6.22-14-generic/volatile
/dev/sda1    6.1G   4.0G   2.1G   66%    /media/sda1
/dev/sda2    54G    17G    38M   32%    /media/sda2

---

### Post by icheyne on 2007-12-30
[http://ubuntuforums.org/showthread.php?p=3605925](http://ubuntuforums.org/showthread.php?p=3605925)

---

### Post by 150pilot on 2008-01-04
If Authentication Failed

ctrl + alt + F2 @ login
login using your username and password
sudo vi /etc/pam.d/gdm
delete this line -  @include common-pamkeyring
:wq
reboot

Searched for two hours to figure this out as I had the same problem.

---

