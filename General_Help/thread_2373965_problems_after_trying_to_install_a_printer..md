---
title: "problems after trying to install a printer."
date: 2017-10-11
forum: General Help
---

### Post by nancyrowina on 2017-10-11
sorry to start another thread but because this is a totally different problem thought it was necessary, if it's not allowed feel free to merge it.
 
ever since i tried to install a printer i've had an error, and while getting a pastebin link for another problem saw this;

```
$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libgcc1:i386 : Depends: libc6:i386 (>= 2.2.4) but it is not installed
 lsb-core : Depends: libc6:i386 or
                     libc6-i386 but it is not installed
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.
nancy@nancy-Latitude-D430:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



```

can anyone please tell me what it is i need to install to correct this? Thanks.

---

### Post by howefield on 2017-10-11
Thread moved to the "*General Help*" forum.

---

