---
title: "Dependency issues"
date: 2008-03-07
forum: General Help
---

### Post by Nelfstar on 2008-03-07
So I'm trying to install libc6-dev but I get this error when I apt-get install libc6-dev 

libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-8 is to be installed

Anyone able to help me out here?

---

### Post by Perfect Storm on 2008-03-07
Try reload the list first.
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by Nelfstar on 2008-03-07
Still doesn't work this is the exact error I'm getting


The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-8 is to be installed
E: Broken packages

---

### Post by Perfect Storm on 2008-03-07
Please post the output of this command:
```
cat /etc/apt/sources.list
```

---

### Post by Nelfstar on 2008-03-07
Thank you for helping me Artificial Intelligence, here is the output.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted

---

### Post by Perfect Storm on 2008-03-07
Ok. You sourcelist is disable, that's why you can't get anything.
Go to Systes tab ---> Administration ---> Software Sources
Here you can enable the whole bunch ;)

---

### Post by Nelfstar on 2008-03-07
Still won't allow me to install libc6-dev and still getting the same error message :(

---

### Post by Nelfstar on 2008-03-07
I'm refreshing the list again and now it's downloading files this time

---

### Post by Eisenwinter on 2008-03-07
Get [libc6]("http://packages.ubuntu.com/gutsy/libc6-dev") from here.

Open up terminal and type sudo dpkg -i <package name here>.

See if that lets you install,

---

### Post by Perfect Storm on 2008-03-07
> **Nelfstar said:**
> I'm refreshing the list again and now it's downloading files this time

Great!

Enjoy ^_^

---

### Post by Nelfstar on 2008-03-07
I still can't install libc6-dev I think it depends on having an earlier version of libc6 but I have version 2.7-8 and not 2.6-1

---

### Post by Perfect Storm on 2008-03-07
Ok, sounds like that an Ubuntu upgrade that went wrong.

Try with Eisenwinter link and see if you can install it manually.

---

### Post by Nelfstar on 2008-03-07
I tried manually and I still get the same error.

---

### Post by Perfect Storm on 2008-03-07
Try this: Go to synpatic Package Manager find libc6 and click re-install.
Moreover there's a "fix broken packages" in the edit tab, see if it's any good.

---

### Post by prshah on 2008-03-07
try installing build-essential first:

sudo apt-get install build-essential

Cheers,
PRShah

---

### Post by Nelfstar on 2008-03-07
Aright I forced the version back down to 2.6.1 and now I can install libc6-dev So now I should be able to compile things again and get my Audio working again, all this depended on getting libc6-dev THANK YOU so much.

Edit: fixed a typo

---

