---
title: "How to install XBMC on Ubuntu?"
date: 2013-10-20
forum: General Help
---

### Post by carmen2012 on 2013-10-20
I know that XBMC is available in the Ubuntu Software Center but for the last week or so, I've been trying to install it and getting errors.  The errors are listed below.  I'm just wondering if there are some official instructions on how to install it manually on Ubuntu as the Software Center doesn't seem to work.

Thank you


*****************************************
Failed to download package files
Check your Internet connection.




Failed to fetch [http://security.ubuntu.com/ubuntu/po...3.04.1_all.deb](http://security.ubuntu.com/ubuntu/po...3.04.1_all.deb) 404 Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/po....04.1_i386.deb](http://security.ubuntu.com/ubuntu/po....04.1_i386.deb) 404 Not Found [IP: 91.189.91.15 80]

---

### Post by QIII on 2013-10-20
Hello!

Which version of Ubuntu are you running?

---

### Post by carmen2012 on 2013-10-20
I am using Ubuntu 13.04 right now, will be upgrading to 13.10 soon.

---

### Post by QIII on 2013-10-20
Could you please post the contents of /etc/apt/sources.list?

Please place it in code tags by clicking the "#" symbol above the input box, placing your cursor between the code tags generated and pasting.

---

### Post by carmen2012 on 2013-10-20
Here is the contents of the requested file.

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring universe
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```

---

### Post by QIII on 2013-10-20
OK.  Could you try updating again in the terminal?  Make the terminal as wide as you can, so the urls are not shortened.

Highlight the 404s and paste those lines between code tags.

---

### Post by carmen2012 on 2013-10-20
Sorry, I'm kind of new to this, I know how to open a terminal session, but how do you update in terminal?

To install XBMC, I have just been opening the Software Center, searching for it and then trying to install it.  After a few minutes, it times out with the error in the original post.

---

### Post by QIII on 2013-10-20
In the terminal, do

```
sudo apt-get update
```

---

### Post by carmen2012 on 2013-10-20
no error messages when I run that command

---

### Post by QIII on 2013-10-20
OK, good.  What we did was made sure your "catalogue" is up to date.

Now let's make sure all of your currently installed software is up to date.  The following command *will not attempt *to upgrade you to a new version of Ubuntu.  It will attempt to upgrade your installed software.

```
sudo apt-get dist-upgrade
```

---

### Post by carmen2012 on 2013-10-20
ok, that took a bit, but it just finished

---

### Post by QIII on 2013-10-20
Alright.  We'll move on to installing xbmc... maybe.

Just by way of explanation.  I'm not having you do this in the terminal out of ubergeekness.  The fact is that there are dozens of desktop environments and none of us knows the ins and outs of all of them, particularly when people customize them as they do.  So the terminal is the common denominator.  That's why you see all the commands in the terminal on the forums.

Anyway...

```
sudo apt-get install xbmc
```

This is where we may actually run into some fun stuff, but we may get l lucky.

---

### Post by carmen2012 on 2013-10-20
Thank you for the explanation of why things are done through a terminal session, I learnt something.

In terms of the XBMC install, drum roll please, it worked!  The last line in the terminal session did say "E: Sub-process /usr/bin/dpkg returned an error code (1)" , but the XBMC icon is there and when I click it, it works.  There were a few other error messages in the output, but again, I'm not sure if that is normal or not.

In any case though, it works.  Thank you so much for your time this evening, now on to get some opinions on hardware.

---

