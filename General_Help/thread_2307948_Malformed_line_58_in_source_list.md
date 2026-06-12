---
title: "Malformed line 58 in source list"
date: 2015-12-29
forum: General Help
---

### Post by gotitsimple on 2015-12-29
Hello,

I am having a heck of a time trying to do anything when I try to use the software center or to manually update software.
I get this message -  Malformed line 58 in source list 
Having found the title already in the thread, I got this far,but don't know what I am looking for....


```
# deb cdrom:[Ubuntu-GNOME 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty multiverse
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security main restricted
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) trusty-proposed main multiverse restricted universe
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://apt.flirc.tv/arch/i386](http://apt.flirc.tv/arch/i386) binary
# deb-src [http://apt.flirc.tv/arch/i386](http://apt.flirc.tv/arch/i386) binary
```

[B]any help would be greatly appreciated.
Thanks,Sean (the 2 year noob)[/B]

---

### Post by slickymaster on 2015-12-29
Try the following, open the terminal an run```
sudo nano /etc/apt/sources.list
```This will open your sources list in Nano with root privileges, then edit your line 58 so it reads like this```
deb http://apt.flirc.tv/arch/i386 binary/
```Save and close and afterwards run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by matt_symes on 2015-12-29
Hi

The offending line is this one.

```
deb http://apt.flirc.tv/arch/i386 binary
```

It's missing a **/** after binary. ie it should be **binary/**.

OPen a terminal and *copy and paste* this command into it. It'll add a / after the word **binary** to the correct entry.

```
sudo sed -i 's_.*flirc.*$_&/_' /etc/apt/sources.list
``` 

The type

```
sudo apt-get update
```

You'll get this warning......

```
Reading package lists... Done
W: The repository 'http://apt.flirc.tv/arch/i386 binary/ Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

If you *trust the source* then type.

```
sudo apt-get install flirc
```

**EDIT:**

Ninja'ed :)

Kind regards

---

### Post by gotitsimple on 2016-01-09
Thank you so very much.  I actually had the / that was needed, but the other commands you suggested must have done the trick.  I am now able to update, now if I could only recover my lost "documents" option in my files, I would be a happy camper.
Thanks again, SMP

---

### Post by matt_symes on 2016-01-10
Hi

> **gotitsimple said:**
> Thank you so very much.  I actually had the / that was needed, but the other commands you suggested must have done the trick.  I am now able to update, now if I could only recover my lost "documents" option in my files, I would be a happy camper.
Thanks again, SMP

I'm glad it's fixed for you.

You may want to raise a new thread about your missing documents option.

I have jailed your duplicate post for you.

Kind regards

---

