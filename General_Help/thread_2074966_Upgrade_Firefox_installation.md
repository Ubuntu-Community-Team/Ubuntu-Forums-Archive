---
title: "Upgrade Firefox installation"
date: 2012-10-22
forum: General Help
---

### Post by ztirffritz on 2012-10-22
I upgraded my PC to 12.04 and all went well, but it disabled a bunch or repos and now nothing seems to be upgrading.  Is there a way to get a default list of repos for apt-get?  What made me curious was that my Firefox seems to be stuck on version 13, even though version 16 has been released.  Alternatively, is there an easy way to update Firefox?

---

### Post by Karlchen on 2012-10-22
Hello, ztirffritz.

Please post the content of the following file: **/etc/apt/source.list**. Run ```
cat /etc/apt/sources.list
```Kind regards,
Karl

---

### Post by ztirffritz on 2012-10-22
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise universe
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise multiverse
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security main restricted
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security universe
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) precise-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by ztirffritz on 2012-10-24
Does anyone have any ideas?

---

### Post by zeroseven0183 on 2012-10-25
You might want to try changing your source/download server. Here's how: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Edit the Software Sources from the Ubuntu Software Centre (Edit menu). Either you select the one nearest to you or have Ubuntu select for you the best one.

---

### Post by ztirffritz on 2012-10-25
I thought that all the repos were supposed to be replicas of each other?  Is that not the case?  How the heck can one tell if the repo in use is valid and/or up-to-date?  I'm currently downloading a metric ****-ton of updates, but I would have thought that any repo that is online should be the same as all the rest, albeit maybe slower or faster.

---

