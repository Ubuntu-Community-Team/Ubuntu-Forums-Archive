---
title: "apt-get update Really Slow"
date: 2016-03-17
forum: General Help
---

### Post by Jason_Hunter on 2016-03-17
I've been having this problem for a long time, but never figured it out. I believe it's hard to figure this one out;)

The problem has many issues affecting my system, but one thing that is common is that apt-get is really slow to update. 

I've been getting through this problem by running an older kernel, but recently this has not worked aswell.

apt-get update is really slow, like taking 20 minutes to complete

I need help to troubleshoot this.

I've tried strace apt-get update, but I'm not really seeing anything strange. 

Anyone got any pointers as to how I can troubleshoot this and where to start?;)

I'm on Ubuntu 15.10, 32 bit.

---

### Post by oldos2er on 2016-03-17
Which repository server are you using?

---

### Post by Jason_Hunter on 2016-03-17
Nothing special. Here's my sources list: 

```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner






##hmm, for cyberduck
# deb [https://s3.amazonaws.com/repo.deb.cyberduck.io](https://s3.amazonaws.com/repo.deb.cyberduck.io) nightly main # deaktivert under oppgradering til utopic
# deb [https://s3.amazonaws.com/repo.deb.cyberduck.io](https://s3.amazonaws.com/repo.deb.cyberduck.io) stable main # deaktivert under oppgradering til utopic


##insync
# deb [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) vivid non-free contrib # deaktivert under oppgradering til vivid
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) wily-proposed multiverse main universe restricted
```

---

### Post by vasa1 on 2016-03-17
Why do you have deb-src? Do you really need that? And backports? These have the *potential* to muck things up. Just mentioning it even though the risk may be minimmal.

As was implied by oldos2er's question, try another server.

---

### Post by sammiev on 2016-03-17
Sever found here.

---

### Post by Jason_Hunter on 2016-03-17
Ok, I've set it to "main server", instead of "server for norway" and it's just the same. 

I don't believe the problem lies here, at all.

---

### Post by vasa1 on 2016-03-17
Have you talked with your ISP?

---

### Post by Jason_Hunter on 2016-03-17
I don't see how the ISP can be to blame here, cause if I ping archive.ubuntu.com, I get a ping of 40ms and if I ping no.archive.ubuntu.com, I get a ping of 30ms.

---

### Post by Bucky Ball on 2016-03-17
> **Jason_Hunter said:**
> I don't see how the ISP can be to blame here, cause if I ping archive.ubuntu.com, I get a ping of 40ms and if I ping no.archive.ubuntu.com, I get a ping of 30ms.

That is extremely slow. If you are expecting faster then I would indeed contact your ISP. Are there other machines connected in your dwelling and are they getting the same speeds or are blazingly faster or just significantly faster?

If they're all slow, contact ISP. If it's only this one, perhaps an issue with hardware itself or a driver.

---

### Post by Jason_Hunter on 2016-03-17
Seriously, that's not that slow;) And, I've got another computer with ubuntu with just the same ping time and its apt-get update is normal.

I need some logs somehow from apt-get, to be able to move forward with this problem.

---

### Post by Bucky Ball on 2016-03-17
Are you using the standard kernel for your version of Ubuntu (you haven't installed a newer one for whatever reason)?

---

### Post by Jason_Hunter on 2016-03-17
I should also add that this problem is not occuring immediately when I reboot, it sort of just happens after a while of using it. I believe it's a kernel issue with my hardware. As I said in the beginning, I've been running an old kernel for a while, becuase the newer kernels who exhibit this behavior more frequently. Now, however, it also happens when I use the oldest kernel available in grub.

I've installed the newest I could find as well, kernel 4.4.1 and it's just the same there.

It's the standard kernel from Ubuntu, so nothing special

Hmm, ok, I see now that I've actually been running 4.4.1 right now and that means that kernel 3.13 probably works if I boot that. Sorry, I thought I had booted 3.13;) 

Anyways, I'd like to still solve this with 4.4.1 to see what's going on. 

In dmesg, I see lots of kernel panics: 

[http://pastebin.ca/3403996](http://pastebin.ca/3403996)

wow, I don't know how I thought I was running 4.4.1, cause I am running 3.13 

Hehe, I guess it's too late. 

Ok, so I'm definitely running 3.13 and I see these bugs.

---

### Post by Bucky Ball on 2016-03-17
Why don't you, using the stock kernel:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... regardless of however long it takes, reboot and try again. See if you still have the same issue. If you're stopping the update because its slow you'll never know if it's been fixed in the kernel, if that is the problem, as you're never getting through the update/upgrade.

I'd forget about 4.4 kernel for now. Wasn't intended for your release, may cause others issues, and it has shown that the sluggishness is not related to kernel (from what you're saying). Try and fix on the latest 14.04 kernel for now. 

Just a note: Rather than post five posts that say not much, please edit your thoughts in to the first post of the bunch and that way you can avoid the redundant other four. Thanks.

---

