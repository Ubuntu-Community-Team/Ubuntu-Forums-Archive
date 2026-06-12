---
title: "Need help decyphering an error message"
date: 2006-11-13
forum: General Help
---

### Post by marbig on 2006-11-13
After downloads I get an error message:```
W: Duplicate sources.list entry http://au.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://au.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-
i386_Packages)
```Anyone any clues what this is?

---

### Post by nikhilk on 2006-11-13
I believe the problem is what the error message says "Duplicate sources.list entry". You have probably inadvertently duplicated an entry in the "sources.list" file. Just open the file and look for any signs of duplicate entries.
If you are not comfortable with that, post the contents of "sources.list" file here, someone will help you out.

---

### Post by marbig on 2006-11-13
Hi nikhilk. thanks for your reply. I can't seem to find any duplicates in this list.```

deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by koenn on 2006-11-13
> *deb* [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **edgy-security** main restricted **universe** multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
*deb* [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **edgy-security** **universe**
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

and likewise for deb-src

---

### Post by koenn on 2006-11-13
and here's an other one: 
> 
deb [http://**au.archive](http://**au.archive)**.ubuntu.com/ubuntu/** edgy** main restricted **universe** multiverse


## Major bug fix updates produced after the final release of the
## distribution.
.....

## Uncomment ..; in
##  WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://**au.archive](http://**au.archive)**.ubuntu.com/ubuntu/ **edgy** [B]universe
[/B]

---

### Post by nikhilk on 2006-11-14
First make a backup of your "sources.list" file to be safe. Then just delete the duplicate entries which "koenn" has kindly pointed out, and you should be fine.

---

### Post by marbig on 2006-11-14
All done, Thanks all.

---

