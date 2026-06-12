---
title: "Synaptic has Trouble Accessing Repositories..."
date: 2014-07-03
forum: General Help
---

### Post by BlacklightHalo on 2014-07-03
Hi everyone.

I've tried installing a few different programs lately with Synaptic, and although each one seems to work fine when I'm done, when I press the "reload" button to finalize the changes, I get this error message...

[ATTACH=CONFIG]254438[/ATTACH]

Is there something I need to change in my repository settings? What else could I do about this? I'm guessing I should do something about it since it's an error message.

Thanks for your time,

-Valek

---

### Post by deadflowr on 2014-07-03
Post the output for 
```
cat /etc/apt/sources.list
```
But I will say, from the output I see in the picture, it has the version as raring.
Ubuntu 13.04 Raring Ringtail has ended and so the repos for it are longer there.
[Forum staff recommendations on EOL releases, et al]("http://ubuntuforums.org/showthread.php?t=2229730")

---

### Post by BlacklightHalo on 2014-07-03
Thanks for your reply. Here is the output.

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

```

---

### Post by grahammechanical on 2014-07-03
13.04 reached end of life at the begining of 2014. And 13.10 is getting close to end of life. Standard releases only have 9 months support. So, our policy should be if we install a standard release then we upgrade to the next release within 3 months of it being released and if we do not like that idea, then we should running the LTS release (5 years  support) with an opportunity to twice upgrade to the newest LTS before it reaches end of life.

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

Regards.

---

### Post by deadflowr on 2014-07-03
Yes, quite unfortunate that raring has hit EOL.
While we won't be able to fix it, we will be willing to help move you to a supported release.
If you have any questions regarding some of the things you'll need to do, post them.
(Questions such as best back up methods, which version to install, etc,etc)

---

### Post by BlacklightHalo on 2014-07-03
Thanks. I thought I did choose the LTS, but apparently I was wrong.

I'm feeling a bit wary here, though. Raring *finally* got support for the Desktop Cube with OpenGL compositing that would work on my computer, and I'm concerned that if I go to the next release, I'll have to deal with that again, and other things that haven't yet been fixed about it. Any thoughts?

---

### Post by deadflowr on 2014-07-03
Cube, opengl on Kubuntu?
work for me, but I don't know enough about your machine to say how a version like 14.04 will be.
(I base the guess about Kubuntu because that is what you prefixed this thread with, sometimes people do that accidentally, in which case...

---

