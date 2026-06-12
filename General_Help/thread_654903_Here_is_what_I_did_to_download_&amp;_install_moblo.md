---
title: "Here is what I did to download &amp; install moblock...what am I doing wrong?"
date: 2007-12-31
forum: General Help
---

### Post by s3a on 2007-12-31
Ok, I went on this page: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

and then, I went on terminal and typed: "sudo gedit /etc/apt/sources.list"

and then, I added "deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main" at the bottom.

and in addition, I added "gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -"

and then I typed: "sudo apt-get install moblock-nfq"

and it gave me this problem: "deniz@deniz-desktop:~$ sudo gedit /etc/apt/sources.list
deniz@deniz-desktop:~$ sudo apt-get install moblock-nfq
E: Type 'gpg' is not known on line 78 in source list /etc/apt/sources.list
E: The list of sources could not be read.
deniz@deniz-desktop:~$"

Someone please tell me what I am doing wrong!
Thanks in advance!

---

### Post by PeterJS on 2007-12-31
Well, what's on line 78 of your sources file? Something might have gotten mispiped, it happens.

---

### Post by oldos2er on 2007-12-31
The "gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -" is a command you type in the terminal. You should delete it from your sources.list.

---

### Post by s3a on 2008-01-01
> **oldos2er said:**
> The "gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -" is a command you type in the terminal. You should delete it from your sources.list.
I removed them and typed the following in this order:

1)gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B

2)gpg --export --armor 9072870B | sudo apt-key add -

(I also did #1 & 2 as 1 line and got same problem)

3)sudo apt-get install moblock-nfq

and got this message:

"deniz@deniz-desktop:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
deniz@deniz-desktop:~$ gpg --export --armor 9072870B | sudo apt-key add -
OK
deniz@deniz-desktop:~$ sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package moblock-nfq
deniz@deniz-desktop:~$"

---

### Post by oldos2er on 2008-01-01
Can you post the output of cat /etc/apt/sources.list ?

---

### Post by s3a on 2008-01-01
deniz@deniz-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
deniz@deniz-desktop:~$

---

### Post by nickoli_02 on 2008-01-01
```
sudo apt-get update
```

you'll probably have to do that after adding your new repository to sources.list in order to see the packages in the repository. Hope this helps

---

### Post by oldos2er on 2008-01-02
Remove the comment mark # from each line that begins with deb and deb-src. Then in a terminal type "sudo aptitude update".

---

### Post by jre on 2008-01-02
> **oldos2er said:**
> Remove the comment mark # from each line that begins with deb and deb-src.
Yes, you'll also need the "universe" repository, at least:
```
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
```
Together with
```
deb http://moblock-deb.sourceforge.net/debian gutsy main
```
it should work then.

> **oldos2er said:**
> Remove the comment mark # from each line that begins with deb and deb-src. Then in a terminal type "sudo aptitude update".
Yes, and afterwards "sudo aptitude install moblock-nfq"

---

