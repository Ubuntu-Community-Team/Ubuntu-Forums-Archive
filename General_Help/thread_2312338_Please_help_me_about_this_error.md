---
title: "Please help me about this error"
date: 2016-02-03
forum: General Help
---

### Post by mark265 on 2016-02-03
I updated my system to Ubuntu 15.10, however after trying to install (which are not installed at all) arc theme, I cannot update anymore and have this message

```
E: Malformed line 1 in source list /etc/apt/sources.list.d/arc-theme.list (dist)
E: The list of sources could not be read

here is my source list

# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily restricted universe main multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates restricted universe main multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security restricted universe main multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
```

thanks in advance

---

### Post by deadflowr on 2016-02-03
You need to post the output for the file in question.
/etc/apt/sources.list is one file, but
/etc/apt/sources.list.d/arc-theme.list is an entirely different file.
Post the output for that,
try
```
cat /etc/apt/sources.list.d/arc-theme.list
```

---

### Post by mark265 on 2016-02-05
here is the output

deb [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10//](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10//)
deb [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/) /
deb [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/) /

---

### Post by deadflowr on 2016-02-05
Is that how they look?
If so, you might notice one of the lines is not like the others.

You might try a manual edit:
```
sudo nano /etc/apt/sources.list.d/arc-theme.list
```
and then change the first line, by simply moving the second / at the end one space over.
Just like the other two lines show.
From
 ```
[COLOR=#000000]deb [/COLOR][http://download.opensuse.org/reposit...Ubuntu_15.10//]("http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10//")
```
To
```
[COLOR=#000000]deb [/COLOR][http://download.opensuse.org/reposit...Ubuntu_15.10/]("http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10//") /
```
Then save with ctrl +X then Y for yes and then enter to save and exit.

See how that works.

---

