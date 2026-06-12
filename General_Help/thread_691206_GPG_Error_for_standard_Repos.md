---
title: "GPG Error for standard Repos"
date: 2008-02-08
forum: General Help
---

### Post by gdi2k on 2008-02-08
I'm getting GPG errors when reloading my repos. These are standard Ubuntu repos. I've added a few others manually, along with keys, and they all work fine. It's the Ubuntu ones that are failing: 

```
W: GPG error: http://security.ubuntu.com gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ae.archive.ubuntu.com gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Here's my sources.list:
```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ae.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ae.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ae.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://free.nchc.org.tw/ubuntu feisty main restricted universe multiverse
deb http://free.nchc.org.tw/drbl-core drbl stable
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://www.virtualbox.org/debian gutsy non-free
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
```

Any ideas?

---

### Post by jan quark on 2008-02-08
if you switch the server does this problem occur too?

---

### Post by gdi2k on 2008-02-08
Thanks for your respose. 

No, the problem does not occur if I select the UK server. 

The AE (United Arab Emirates) servers were automatically selected based on my chosen location during installation. Presumably there aren't actually any servers in the UAE, so they must automatically resolve to geographically closer servers? 

I can live with using the UK server, but maybe I should file a bug report about the AE server issue?

---

