---
title: "Error in apt"
date: 2017-08-11
forum: General Help
---

### Post by Azyx on 2017-08-11
I get this error-message in synaptic. How do I fix it?

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4

```

/Cheers Azyx

---

### Post by oldos2er on 2017-08-11
You're running 16.04?

If you have the partner repository enabled in /etc/apt/sources.list you shouldn't need any of those xenial-partner files in /etc/apt/sources.list.d/

---

### Post by Azyx on 2017-08-12
Yes running 16.04. How do I remove them? Manual from terminal? I made an upgrade from 14.04, so there are also some trusty files also.

```
Azyx@Datorn:/etc/apt/sources.list.d$ ls
alexmurray-indicator-sensors-daily-trusty.list              ubuntugis-ubuntugis-unstable-trusty.list
alexmurray-indicator-sensors-daily-trusty.list.distUpgrade  ubuntugis-ubuntugis-unstable-trusty.list.distUpgrade
alexmurray-indicator-sensors-daily-trusty.list.save         ubuntugis-ubuntugis-unstable-trusty.list.save
alexmurray-indicator-sensors-trusty.list                    videolan-master-daily-trusty.list
alexmurray-indicator-sensors-trusty.list.save               videolan-master-daily-trusty.list.distUpgrade
rvm-ubuntu-smplayer-xenial.list                             videolan-master-daily-trusty.list.save
rvm-ubuntu-smplayer-xenial.list.save                        x2go-stable-trusty.list
strukturag-libde265-trusty.list                             x2go-stable-trusty.list.save
strukturag-libde265-trusty.list.distUpgrade                 xenial-partner.list
strukturag-libde265-trusty.list.save                        xenial-partner.list.save

```

/Cheers

---

### Post by vasa1 on 2017-08-12
In Synaptic Manager, click on *Settings*, *Repositories* and disable whatever is troubling you.

---

### Post by Azyx on 2017-08-23
> **vasa1 said:**
> In Synaptic Manager, click on *Settings*, *Repositories* and disable whatever is troubling you.

Thanks. Yes there was also dubbel entys in synaptic. Little strange, when I remove one anothar simmilar also get unchecked, but I checket that again, and now i work :)

---

