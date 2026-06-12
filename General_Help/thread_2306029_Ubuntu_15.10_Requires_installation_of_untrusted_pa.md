---
title: "Ubuntu 15.10 Requires installation of untrusted packages"
date: 2015-12-11
forum: General Help
---

### Post by jr223 on 2015-12-11
Howdy,

It seems I now have an issue with running updates through software centre.
When I try to do the upgrade I recieve the followning message:

[I]Code:
Ubuntu 15.10 Requires installation of untrusted packages
[/I]

I click ok since I can't do anything else and then open terminal and run
sudo apt-get update all goes fine except for the end of the update where I have the following error message about missing SSH keys.

[I]Code:
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily-security/universe Translation-en_CA
Fetched 607 kB in 3s (179 kB/s)          
Reading package lists... Done
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 241FE6973B765FAE
[/I]

I have tried the following without any success.
[I]sudo apt-get clean
sudo apt-get update
[/I]
Also 
[I]sudo mv lists lists.old
sudo mkdir -p lists/partial
[/I]
And
[I]sudo apt-get update --fix-missing
sudo apt-get clean
sudo apt-get update
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05
sudo apt-get update
[/I]

Still I have no luck I even edited my sources list no change.
Please assist in helping fix this.
Although I did run a successful update through synaptic, but what I really need is to fix this issue through software update.
Please see my sources.list below.

[I]# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-security restricted main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


[/I]

---

### Post by oldos2er on 2015-12-11
You need to run the apt-key command for each missing key, so ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 241FE6973B765FAE

sudo apt-get update
```

---

### Post by jr223 on 2015-12-13
Hi odos2er

Thanks for the help, I ran this but for some reason it looks like there is some complaining about the keys not being available.
This is Willy so they should?
Please see output below after running the 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 241FE6973B765FAE
sudo apt-get updatefrom 


Reading package lists... Done
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) wily-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 241FE6973B765FAE

Any other suggestions?
Thanks

---

### Post by fangorn2 on 2016-02-17
I personally unchecked the 'Unsupported updates (trusty-backports)' in the tab 'Updates' of the software sources in Ubuntu software center and it worked.
Open Ubuntu Software Center, go to 'edit > Software sources' and then go to the tab 'Updates' and uncheck 'Unsupported updates (trusty-backports)'.

---

