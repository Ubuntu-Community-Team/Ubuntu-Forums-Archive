---
title: "ubuntu-software apps got removed by itself"
date: 2018-12-10
forum: General Help
---

### Post by nrrz04 on 2018-12-10
Hi
 I have installed ubuntu 18.04LTS a week ago. It worked fine for some days .Then I suddenly realize that 3 of the apps(ubuntu-software,software and properties and updater app) has removed by itself. While seeking help online I found the solution to reinstall them by executing “sudo apt install ubuntu-software”on terminal. After  having executed this the apps are back again. I am sure I did not remove it by myself .I am posting this to the forums to ask if somebody know how this could have happened by itself or has come across the similar problems. is this a bug ?
 Some information that might help:
 1.downloaded the ISO from ubuntu official website and set up installation by rufus as indicated in website
 2.never ran dist-upgrade and auto-remove
  Thanks in advance!

---

### Post by freemedia2018 on 2018-12-10
There was a bug in software center dating all the way back to 2012 where during Ubuntu installation, it could uninstall itself.

More recently it is reported that installing xml-copy-editor could cause software center to uninstall: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1081838](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1081838)

You could also uninstall your desktop by clicking on an apturl: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1110188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1110188) so the real trick isn't for software center to get uninstalled, but for it to stay once you've installed it. Don't feel bad, this time around it really might not be the user to blame.

---

### Post by nrrz04 on 2018-12-11
Very informative!
thank you very much for taking a look and giving your time!

---

### Post by ra7411 on 2018-12-11
I've got 2 Ub 18.04 machines, and in both machines, PulseAudio equalizer has somehow become uninstalled, more than once in the case of one machine. Really odd.

---

