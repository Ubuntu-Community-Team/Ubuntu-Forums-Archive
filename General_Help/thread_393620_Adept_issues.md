---
title: "Adept issues"
date: 2007-03-25
forum: General Help
---

### Post by mrbones on 2007-03-25
I have an issue, Adept will not allow me to open it after I loaded the source for the 7.04 upgrade... it states it is an unknown listing, and will not alow it to open... Anyone have a good way to correct this? and does it have to be in the Terminal? and how do I make the file writable not just readable?

---

### Post by aysiu on 2007-03-26
Can you post the output of these terminal commands? ```
cat /etc/apt/sources.list
sudo aptitude update
```

---

### Post by mrbones on 2007-03-26
[http://kubuntu.org/~jriddell/tmp/archive-edgy-dist-upgrade-kde356-i386/](http://kubuntu.org/~jriddell/tmp/archive-edgy-dist-upgrade-kde356-i386/)

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
bones@bones-desktop:~$     

And after sudo aptitude update...

bones@bones-desktop:~$ sudo aptitude update
Password:
E: Type 'http://kubuntu.org/~jriddell/tmp/archive-edgy-dist-upgrade-kde356-i386/' is not known on line 1 in source list /etc/apt/sources.list
E: Type 'http://kubuntu.org/~jriddell/tmp/archive-edgy-dist-upgrade-kde356-i386/' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
bones@bones-desktop:~$

---

### Post by aysiu on 2007-03-26
Yeah, that first line is messed up. Just get rid of it. ```
kdesu kate /etc/apt/sources.list
``` will allow you to edit that file. Delete the first line, save, and exit. Then load up Adept again.

---

### Post by mrbones on 2007-03-26
Thanks, that did it... now do you know of a safer way to begin a migration to 7.04?

---

### Post by aysiu on 2007-03-26
> **mrbones said:**
> Thanks, that did it... now do you know of a safer way to begin a migration to 7.04?
I'd say the safe way would be waiting until next month when it comes out. If I'm not wrong (and I may be), Adept will just notify you about an upgrade. If not, the regular upgrade methods will work:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)

---

### Post by mrbones on 2007-03-26
thanks alot:P

---

