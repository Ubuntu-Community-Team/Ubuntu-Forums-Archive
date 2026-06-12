---
title: "Unable to update from 11.04"
date: 2013-08-21
forum: General Help
---

### Post by Santosh_Kumar_BR on 2013-08-21
I am unable to update from Ver:11.04. It is showing error as 'Encountered  a section with no package, header, E: Problem with merge list/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386-Packages, E:The package lists or status file could not or pasted or reopened.

---

### Post by Cheesemill on 2013-08-21
You can't update because support for 11.04 ran out 10 months ago so the repositories have been moved. There is a method for upgrading but that would only take you to 11.10 which has also reached end of life.

Because of the massive differences between 11.04 and current versions I would highly recommend backing up all of your data and doing a fresh installation instead, this will be much quicker and far more likely to proceed without any problems than trying to update through 2 unsupported releases.

---

### Post by Santosh_Kumar_BR on 2013-08-21
Thank you for your reply. Can you please guide me how can I update.

Thanks

---

### Post by Cheesemill on 2013-08-21
If you are sure that you really want to try and upgrade instead of doing a clean installation then backup everything important first as there is every chance that this will fail.

Then post back with the output of the following command and I'll tell you what to do next...
```
cat /etc/apt/sources.list
```

---

### Post by Santosh_Kumar_BR on 2013-08-21
Done. Actually I was using Ubuntu. Now when I am trying to download, it shows as paid.

---

### Post by Santosh_Kumar_BR on 2013-08-21
Ubuntu is recently installed. So please guide how to install.

---

### Post by Cheesemill on 2013-08-21
If you want to do a clean installation then just download the iso file from [here]("http://www.ubuntu.com/download/desktop") and follow the instructions on the page to either burn the image to a DVD or create a bootable USB stick.

If you want to try and upgrade instead even though I don't recommend it then please post the information I asked for in post #4.

---

### Post by Santosh_Kumar_BR on 2013-08-21
Okay, I will update. Please let me know the next step.

---

### Post by Cheesemill on 2013-08-21
Again, let me know the information I asked for in post #4 and I will.

---

### Post by Santosh_Kumar_BR on 2013-08-21
Okay.It says,

#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by Cheesemill on 2013-08-21
I need the entire output of the command. Open a terminal and run the command...
```
cat /etc/apt/sources.list
```

And then copy ***all*** of the output and paste it into your reply.

---

