---
title: "Sources list issues with Artful"
date: 2017-10-30
forum: General Help
---

### Post by sports fan Matt on 2017-10-30
Thought I had everything just backed up and right but got this error changing repos back to artful from 12.04. 

E:Malformed entry 46 in list file /etc/apt/sources.list (Component), E:The list of sources could not be read.

Can we take a look at my sources list and see if more then this is a problem?

---

### Post by oldos2er on 2017-10-30
"We" can't look at it until you post it.   :)

```
cat -n /etc/apt/sources.list
```

---

### Post by sports fan Matt on 2017-10-31
Sorry about that :) 

```
 5	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main restricted
     6	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful restricted main universe multiverse #Added by software-properties
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates main restricted
    11	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates restricted main universe multiverse #Added by software-properties
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful universe
    17	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates universe
    18	
    19	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20	## team, and may not be under a free licence. Please satisfy yourself as to 
    21	## your rights to use the software. Also, please note that software in 
    22	## multiverse WILL NOT receive any review or updates from the Ubuntu
    23	## security team.
    24	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse
    25	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates multiverse
    26	
    27	## N.B. software from this repository may not have been tested as
    28	## extensively as that contained in the main release, although it includes
    29	## newer versions of some applications which may provide useful features.
    30	## Also, please note that software in backports WILL NOT receive any review
    31	## or updates from the Ubuntu security team.
    32	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports restricted main universe multiverse
    33	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports main restricted universe multiverse #Added by software-properties
    34	
    35	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security main restricted
    36	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security restricted main universe multiverse #Added by software-properties
    37	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security universe
    38	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security multiverse
    39	
    40	## Uncomment the following two lines to add software from Canonical's
    41	## 'partner' repository.
    42	## This software is not part of Ubuntu, but is offered by Canonical and the
    43	## respective vendors as a service to Ubuntu users.
    44	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
    45	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
    46	deb [http://us.archive.ubuntu.com/ubuntu/artful](http://us.archive.ubuntu.com/ubuntu/artful) universe
    47	deb-src [http://us.archive.ubuntu.com/ubuntu/artful](http://us.archive.ubuntu.com/ubuntu/artful) universe
    48	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates universe
    49	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates universe
    50	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
    51	deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) artful main
    52	deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) artful main
    53	
    54	deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
    55	deb-src [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
    56	deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
    57	deb-src [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
```

I just saw holes in my list, I think that's part of the issue as well.  Could it be time for a brand new sources list from scratch?

---

### Post by jbicha on 2017-10-31
lines 46-47 should have a space after ubuntu/ before artful

---

### Post by sports fan Matt on 2017-10-31
Sounds good, now just trying to change it.  (been a long while since I've worked with Linux in general.)

---

### Post by sports fan Matt on 2017-10-31
Solved my generating a new sources list. Thanks for the help!

---

