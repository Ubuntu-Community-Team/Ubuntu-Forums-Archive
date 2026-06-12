---
title: "Synaptic repositories issue"
date: 2016-03-28
forum: General Help
---

### Post by sdjcwcba on 2016-03-28
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160323)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) vivid main[/QUOTE]

[QUOTE]gpgv:/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release.gpg: The repository is insufficiently signed by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 (weak digest)gpgv:/var/lib/apt/lists/ppa.launchpad.net_darklin20_bomi_ubuntu_dists_vivid_Release.gpg: The repository is insufficiently signed by key CBBE8C99E1693CC49F66BA5CC0FD17E37F15F99A (weak digest)The repository 'http://ppa.launchpad.net/kilian/f.lux/ubuntu vivid Release' does not have a Release file.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.Failed to fetch [http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not FoundFailed to fetch [http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not FoundSome index files failed to download. They have been ignored, or old ones used instead.
```

Hey, 

Would greatly appreicate if anyone could help with the above errors.

Thanks!

---

### Post by QDR06VV9 on 2016-03-28
This PPA is no longer(Now unmaintained) **ppa:kilian/f.lux**
So remove it from your source list

And this: [B]"The repository is insufficiently signed by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 (weak digest)"
[/B]
is a bug that should soon get sorted out.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331)

> google chrome repositories is one of the other.

It looks like  SHA1 signing keys has been deprecated :  [https://juliank.wordpress.com/2016/03/15/clarifications-and-updates-on-apt-sha1/](https://juliank.wordpress.com/2016/03/15/clarifications-and-updates-on-apt-sha1/)

Please at least add SHA2 in PPAs.

They've just got to be disabled until people that maintain them have done what they're supposed to do to comply.&#65279;

Hope this clear enough

---

