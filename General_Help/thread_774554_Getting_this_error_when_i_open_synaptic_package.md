---
title: "Getting this error when i open synaptic package"
date: 2008-04-29
forum: General Help
---

### Post by Tnhl1989 on 2008-04-29
I get this massage when i try to open synaptic package manager. 
Well at first i was following another forum about how to add hotmail to evolution but i got the first massage 

E: Malformed line 57 in source list /etc/apt/sources.list(dist parse)

Then when i tried to open synaptic the following came up. 

E: Malformed line 57 in source list /etc/apt/sources.list(dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report. 

What do i do?

---

### Post by aheckler on 2008-04-29
Type "cat /etc/apt/sources.list" in the terminal and post the output here.

---

### Post by Tnhl1989 on 2008-04-29
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy multiverse
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security main restricted
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security multiverse
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security multiverse
deb [http://debian.webseterwood.com/](http://debian.webseterwood.com/) edgy
deb [http://blueeyedcreature.net/ubuntu](http://blueeyedcreature.net/ubuntu) ./
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy

---

### Post by aheckler on 2008-04-29
Alright, run "sudo gedit /etc/apt/sources.list" in terminal. Then take out the last line of the file, the one that says "deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy". Save and close.

Now type this in terminal:

```
sudo apt-get update
```

---

### Post by Tnhl1989 on 2008-04-29
I still get that message.
I forgot where I went to change the whole thing for updates.

---

### Post by aheckler on 2008-04-29
Ok, try doing "sudo gedit /etc/apt/sources.list" again and removing the last two lines, which should be:

```
deb http://debian.webseterwood.com/ edgy
deb http://blueeyedcreature.net/ubuntu ./
```

Then do "sudo apt-get update" in terminal. That should let you get into Synaptic OK.

---

### Post by Tnhl1989 on 2008-04-29
THanks a lot that worked. :)

---

