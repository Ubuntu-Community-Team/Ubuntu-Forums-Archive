---
title: "repository list problems"
date: 2006-10-25
forum: General Help
---

### Post by M!K3_$ on 2006-10-25
i am getting this message when i am trying to update my repos. 




W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)


how do i fix this
it all started when i was using easyubuntu then it said somting like
no KEY
so i tryed to fix that
i did now, i have this
and it wont let me do anything

yikes!!!](*,)

---

### Post by Kateikyoushi on 2006-10-25
There is something wrong with your sources.list.
Copy the content of the file here.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by M!K3_$ on 2006-10-25
this is it

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe






also this is kinda along the same lines,
when i try to use easyubuntu, i get this mesage after it updates the repos

Could not apply changes!
Fix broken packages first.


now, is that directly related to my 1st problem?

---

