---
title: "Updating to Feisty herd 4"
date: 2007-02-18
forum: General Help
---

### Post by chadders on 2007-02-18
How do I go about updating to Feisty Herd 4 (or any other testing version at that) using apt-get? I know I can upgrade the OS by going $apt-get install dist-upgrade or something to that effect, but that will only upgrade to the latest Edgy not to Feisty. Any tips?

---

### Post by RAOF on 2007-02-18
Running
```
gksudo "update-manager -c -d"
```
should do it.  But it's not guaranteed to work, of course.  It's likely to break **something** :)

---

### Post by chadders on 2007-02-18
Thanks :P, I'm still trying to work out if I want to upgrade or not, but it's good knowing how to do it. I think there is a strong chance it will break beryl.

---

### Post by RAOF on 2007-02-18
> **chadders said:**
> ...I think there is a strong chance it will break beryl.

Oh, yeah.  Very good chance there :).

However, you **do** get current Compiz in the Feisty repos :p.

---

### Post by fragos on 2007-02-19
I just tried a clean install of Herd 4 in a spare partition and got into real trouble when installing nvidia-glx.  I plan to wait at least until the RC before considering an upgrade.

---

### Post by tubasoldier on 2007-02-19
> **fragos said:**
> I just tried a clean install of Herd 4 in a spare partition and got into real trouble when installing nvidia-glx.  I plan to wait at least until the RC before considering an upgrade.

Same here, but of course I have never had good luck with the nvidia-glx out of the repositories. After a quick install of the Nvidia driver from the command line, I'm up and running. So far so good.

---

