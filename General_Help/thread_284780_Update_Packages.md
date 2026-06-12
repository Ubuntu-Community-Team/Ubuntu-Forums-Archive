---
title: "Update Packages"
date: 2006-10-26
forum: General Help
---

### Post by sv452 on 2006-10-26
Good day,

I would like to know how can i update packages without upgrading to edgy? there is quite a few programs in edgy that is newer versions of existing ones in dapper... or since dapper is lts will the repos be updated with new updates ??????

this is all a wee bit confusing ... mind if someone explains how the structure of updating works regarding new releases and repos of existing releases...

kind regards,

SV452  :confused:

---

### Post by frodon on 2006-10-26
If you don't change anything you will stay on dapper and won't be asked to update to edgy.
If you wish to update follow thse instructions :
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

BTW, edgy will be released to day so just wait the official release to start the ugrade.

---

### Post by sv452 on 2006-10-26
thanx for the reply.

so what if i don't want to upgrade to edgy but want newer versions of software ?? i can download the sources and compile them but that is most of the time out of the question...

will the packages in dapper's repos get updated ??

SV452

---

### Post by pay on 2006-10-26
I think that a backports repository will be added but other than that no. Dapper will still use gnome 2.14 and xorg 7.0 and kernel 2.15.X...

---

### Post by Titus A Duxass on 2006-10-26
To update software use aptitude.

sudo aptitude update - this will ensure that your sources.list is upto date.

sudo aptitude upgrade - this will install any available upgrades.

---

### Post by sv452 on 2006-10-26
> **Titus A Duxass said:**
> To update software use aptitude.

sudo aptitude update - this will ensure that your sources.list is upto date.

sudo aptitude upgrade - this will install any available upgrades.

will that not essentially update my dapper to edgy ????

---

### Post by pay on 2006-10-26
No "sudo apt-get upgrade" won't upgrade to edgy, to do that you need an edgy sources.list so aslong as you haven't added edgy sources it won't upgrade to edgy;)

---

### Post by sv452 on 2006-10-26
awesome

i'll give it a go and see ...

thanx

---

