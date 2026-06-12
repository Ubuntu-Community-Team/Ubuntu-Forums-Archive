---
title: "Vlc Broken Dependencies"
date: 2014-12-19
forum: General Help
---

### Post by sasafrass452 on 2014-12-19
Synaptic said vlc is upgradable, but there are broken dependencies. Some packages that it depends on don't even exist! I have uninstalled vlc, but of course it can't be reinstalled because of the broken dependencies. If there's nothing I can do myself, the devs need to fix this ASAP!

---

### Post by llamabr on 2014-12-19
> **sasafrass452 said:**
> the devs need to fix this ASAP!

Exactly! In the meantime, paste the output of the error you're getting here, and we can maybe help you troubleshoot it.

---

### Post by sasafrass452 on 2014-12-19
The package vlc-nox is only part of the problem, but here's what it says. Some of the broken dependencies have broken dependencies, so it's a multi-package issue....

vlc-nox:
 Depends: libavcodec54 but it is not going to be installed or
     libavcodec-extra-54 but it is not going to be installed
 Depends: libavformat54 but it is not going to be installed
 Depends: libdvbpsi8 (>=1.0.0) but it is not installable
 Depends: libgnutls28 (>=3.2.10-0) but it is not installable

---

### Post by monkeybrain20122 on 2014-12-23
Can you try to install one of those dependencies and see the output errors. e.g 

```
sudo apt-get -s install libavcodec54
```

You may have added some ppas in the past and have since removed/disable them so the versions of some dependencies have been bumped up and there is no matching versions now that the ppas are removed/disabled.

---

### Post by nerdtron on 2014-12-23
> **sasafrass452 said:**
> Synaptic said vlc is upgradable, but there are broken dependencies. Some packages that it depends on don't even exist! I have uninstalled vlc, but of course it can't be reinstalled because of the broken dependencies. If there's nothing I can do myself, the devs need to fix this ASAP!

wow. I thought the VLC devs really insisted on a single VLC version only for each Ubuntu version (from their website). If you stick with the software center and the software updater you won't see any VLC upgrades.

---

### Post by sasafrass452 on 2014-12-24
> **monkeybrain20122 said:**
> Can you try to install one of those dependencies and see the output errors. e.g 

```
sudo apt-get -s install libavcodec54
```

Here's what the terminal says:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libavcodec54 : Depends: libopenjpeg2 but it is not installable
E: Unable to correct problems, you have held broken packages.

sudo apt-get -s install libopenjpeg2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenjpeg2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

> You may have added some ppas in the past and have since removed/disable them so the versions of some dependencies have been bumped up and there is no matching versions now that the ppas are removed/disabled.

I did in fact add a repo that I have since removed. Hmm....

---

### Post by CantankRus on 2014-12-24
You should re-enable the third party ppa and purge it so as to remove/downgrade the packages causing conflict.

---

### Post by monkeybrain20122 on 2014-12-24
> **nerdtron said:**
> wow. I thought the VLC devs really insisted on a single VLC version only for each Ubuntu version (from their website). If you stick with the software center and the software updater you won't see any VLC upgrades.


I think OP installed from a ppa, probably Videolan's.

---

### Post by sasafrass452 on 2014-12-24
I don't have it anymore,  & I don't remember where I found it, but I think I added it when I had trouble getting flash/icedtea installed. It was supposedly going to help, but didn't work. I finally managed to get icedtea installed on my own.

> **CantankRus said:**
> You should re-enable the third party ppa and purge it so as to remove/downgrade the packages causing conflict.

---

### Post by mc4man on 2014-12-24
Please post 
```
apt-cache policy libavcodec* libopenjpeg2
```

---

### Post by pissedoffdude on 2014-12-24
Whats the output of ```
cat /etc/apt/sources.list
apt-cache search libopenjpeg2
```

---

### Post by sasafrass452 on 2014-12-25
> **mc4man said:**
> Please post 
```
apt-cache policy libavcodec* libopenjpeg2
```

```
Installed: (none)
  Candidate: (none)
  Version table:
libavcodec-extra-53:
  Installed: (none)
  Candidate: (none)
  Version table:
libavcodec-extra-54:
  Installed: (none)
  Candidate: 6:9.16-0ubuntu0.14.04.1+fdkaac
  Version table:
     6:9.16-0ubuntu0.14.04.1+fdkaac 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
libavcodec-extra-56:
  Installed: 6:11-1
  Candidate: 6:11-1
  Version table:
 *** 6:11-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe i386 Packages
        100 /var/lib/dpkg/status
libavcodec-extra:
  Installed: 6:11-1
  Candidate: 6:11-1
  Version table:
 *** 6:11-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe i386 Packages
        100 /var/lib/dpkg/status
     6:9.16-0ubuntu0.14.04.1+fdkaac 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
libavcodec-dev:
  Installed: (none)
  Candidate: 6:11-1
  Version table:
     6:11-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe i386 Packages
     6:9.16-0ubuntu0.14.04.1+fdkaac 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
libavcodec54:
  Installed: (none)
  Candidate: 6:9.16-0ubuntu0.14.04.1+fdkaac
  Version table:
     6:9.16-0ubuntu0.14.04.1+fdkaac 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
libavcodec56:
  Installed: (none)
  Candidate: 6:11-1
  Version table:
     6:11-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe i386 Packages
        100 /var/lib/dpkg/status
libopenjpeg2:
  Installed: (none)
  Candidate: (none)
  Version table:
```

> **pissedoffdude said:**
> Whats the output of ```
cat /etc/apt/sources.list
apt-cache search libopenjpeg2
```

```
# deb cdrom:[Xubuntu 14.10 _Utopic Unicorn_ - Release i386 (20141022.1)]/ utopic main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
```

---

### Post by mc4man on 2014-12-25
Well when you used that ppa you were warned twice (top & bottom of ppa page & terminal description) not to use if planning to upgrade to a new Ubuntu release or if doing anyway to use ppa-purge. Guess you didn't pay attention there..

As far as what that may mean to your install not sure but as far as vlc try - 
open Software & Updates > Other > disable/remove any ppa's,  reload your sources, then 
```
sudo apt-get purge vlc-data
```
```
sudo apt-get update && sudo apt-get install vlc
```

(if posting results of commands ect. try > highlight the text & click on the Quote icon or code (#) to put in a box.

---

### Post by sasafrass452 on 2014-12-26
When trying to install vlc via the terminal, it says:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.2.0+ppa2.5) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.2.0+ppa2.5) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 2.2.0+ppa2.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

> **mc4man said:**
> As far as what that may mean to your install not sure but as far as vlc try - 
open Software & Updates > Other > disable/remove any ppa's,  reload your sources, then 
```
sudo apt-get purge vlc-data
```
```
sudo apt-get update && sudo apt-get install vlc
```

(if posting results of commands ect. try > highlight the text & click on the Quote icon or code (#) to put in a box.

---

### Post by mc4man on 2014-12-26
> open Software & Updates > Other > disable/remove any ppa's, reload your sources,
Did you do this?
If so then please ck. contents of /etc/apt/sources.list.d

---

### Post by mc4man on 2014-12-26
Also please run
sudo apt-get clean

---

### Post by sasafrass452 on 2014-12-27
I just checked that folder, & there are 2 files from a repo that I removed. But I can't delete those files. How do I get rid of them?

> **mc4man said:**
> Did you do this?
If so then please ck. contents of /etc/apt/sources.list.d

I tried this, but I don't think it did anything. What should I expect to happen?

> **mc4man said:**
> Also please run
sudo apt-get clean

---

### Post by mc4man on 2014-12-27
what does this show - 
```
apt-cache policy vlc-data
```

As far as the 2 files in /etc/apt/sources.list.d if they're are empty then  that's expected & fine. If not empty post the contents of one of them

---

### Post by sasafrass452 on 2014-12-28
The 2 files are empty, so all is well there.

The terminal says:

vlc-data:
  Installed: 2.2.0+ppa2.5
  Candidate: 2.2.0+ppa2.5
  Version table:
 *** 2.2.0+ppa2.5 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
     2.2.0~pre2-4build1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe i386 Packages
     2.1.5+ppa1 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages

> **mc4man said:**
> what does this show - 
```
apt-cache policy vlc-data
```

As far as the 2 files in /etc/apt/sources.list.d if they're are empty then  that's expected & fine. If not empty post the contents of one of them

---

### Post by mc4man on 2014-12-28
go back & actually do what's in post #15

---

### Post by sasafrass452 on 2014-12-28
> **mc4man said:**
> go back & actually do what's in post #15
I already did, it didn't work.

---

### Post by mc4man on 2014-12-28
Sorry - I give up - 
In post 22 it shows vlc-data as currently installed. I've asked you twice to remove it, obviously you haven't
good luck..

---

### Post by sasafrass452 on 2014-12-28
I tried the procedure before reinstalling vlc-data. I was attempting to resolve the broken dependancies, but there are missing packages that vlc requires. As I said, the procedure didn't work & I'm still unable to install vlc at the moment. I can assure you that I'm trying every suggestion given to me here, & I greatly appreciate the help!

> **mc4man said:**
> Sorry - I give up - 
In post 22 it shows vlc-data as currently installed. I've asked you twice to remove it, obviously you haven't
good luck..

---

### Post by CantankRus on 2014-12-28
Is the **mc3man/trusty-media** ppa still enabled?

Show all your sources....
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by sasafrass452 on 2014-12-29
> **CantankRus said:**
> Is the **mc3man/trusty-media** ppa still enabled?

Show all your sources....
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

The last repo (mc3man) is enabled.

/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
/etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list:deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
/etc/apt/sources.list.d/mc3man-ubuntu-trusty-media-utopic.list:deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main

---

### Post by CantankRus on 2014-12-29
Open software sources...
```
software-properties-gtk --open-tab 1
```
Disable both instances of the **mc3man-ubuntu-trusty-media** ppa
and continue on with the rest of [**_[COLOR="#B22222"]post #15[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2257379&p=13194013#post13194013")

---

### Post by sasafrass452 on 2014-12-29
I just did, & Vlc is now installed! Thankyou to all who helped!

> **CantankRus said:**
> Open software sources...
Disable both instances of the **mc3man-ubuntu-trusty-media** ppa


---

### Post by CantankRus on 2014-12-29
> **sasafrass452 said:**
> I just did, & Vlc is now installed! Thankyou to all who helped!
Ok, good.
I hope you now understand **mc4man's** frustration
who's apparently "gone fishing".

---

### Post by sasafrass452 on 2014-12-29
Should I just remove that repo? It's there by default, so I assumed it was needed.

> **CantankRus said:**
> Ok, good.
I hope you now understand **mc4man's** frustration
who's apparently "gone fishing".

---

### Post by CantankRus on 2014-12-29
It's not there by default.
You added it and it is only for trusty while you're running utopic.

If you upgraded from 14.04 to 14.10 here's the relevant message from the ppa...
> *Please note that if using this ppa I would *not* try upgrading to 14.10/15.04, ect. Do a fresh install instead. 
The intent here is just for users wishing to stay on 14.04*

If upgrading anyway use ppa-purge first -
sudo ppa-purge ppa:mc3man/trusty-media
So yes remove it.

---

### Post by sasafrass452 on 2014-12-29
That's odd.... I don't remember adding it myself, but then again, I don't remember the one I did add but thought I removed. *shrugs* I'll remove it, then.... BTW, I'm using Xubuntu with a clean installation of 14.10.

> **CantankRus said:**
> It's not there by default.
You added it and it is only for trusty while you're running utopic.

If you upgraded from 14.04 to 14.10 here's the relevant message from the ppa...

So yes remove it.

---

