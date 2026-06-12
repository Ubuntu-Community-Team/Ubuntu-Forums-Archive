---
title: "Touchpad frequently stops working, pressing &quot;Shut down/restart&quot; doesnt work, and more"
date: 2019-03-31
forum: General Help
---

### Post by hugopalianhp on 2019-03-31
Had none of these problems while using Debian. Furthermore using the command # shutdown -h now
doesnt work. Neither does # shutdown -r  now .

Almost 100% sure it's not a hardware issue since I had none of these problems when using Debian. Thinking that maybe possibly there's an issue with BiOS and permissions on the OS but I'm not sure, coming here to ask if anyone has any clue on what might be the problem.
Maybe it's also that I messed something up during the instillation process? Ran ubuntu before on a desktop and I remember having issues but none to do with general reliability.

All types of help appreciated. :KS

---

### Post by yetimon_64 on 2019-03-31
Not sure how you are trying to issue those commands but, try ...
```
sudo shutdown -h now
```
or
```
sudo shutdown -r now
```

Ubuntu locks the root account by default normally and the sudo command is used for privilege escalation in Ubuntu.
The password asked for is for the user account with admin rights, your user account name (if the only user.)

What release of ubuntu are you on and what desktop environment are you using ?

> Maybe it's also that I messed something up during the instillation  process? Ran ubuntu before on a desktop and I remember having issues but  none to do with general reliability.
What installation media/method used to install?

More details of what, and how, you are trying to install may help here. Regards, yeti.

---

