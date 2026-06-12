---
title: "Unable to update and upgrade"
date: 2018-04-04
forum: General Help
---

### Post by Doulos1 on 2018-04-04
I am now on a 2-core VDS with Ubuntu 16.04 but unable to upgrade the latest security updates.  It was working flawlessly yesterday before I up'd it from a 1-core to a 2-core. I tried several times and each time get the following.... Any help would be appreciated...```
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-116-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

7 packages can be updated.
7 updates are security updates.


root@doulos:~# sudo apt-get update && apt-get upgrade
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:4 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
root@doulos:~#
```
Any help would be appreciated...

---

### Post by oldos2er on 2018-04-04
Try ```
sudo apt full-upgrade
```

---

### Post by monkeybrain20122 on 2018-04-04
Why do you run as root and then use sudo??  running your session as root is not recommended. Where did you get the info that there are updates (the 4th and 5th line)?

---

### Post by wildmanne39 on 2018-04-04
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by Doulos1 on 2018-04-05
> **oldos2er said:**
> Try ```
sudo apt full-upgrade
``` No.  Actually forgot that one.> **monkeybrain20122 said:**
> Why do you run as root and then use sudo??  running your session as root is not recommended. Where did you get the info that there are updates (the 4th and 5th line)?Habit.  I logged in as root by mistake and just never switched.

All is good, now. Thanks for the tips.

---

