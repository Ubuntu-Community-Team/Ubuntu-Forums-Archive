---
title: "error during update"
date: 2012-12-29
forum: General Help
---

### Post by closbar on 2012-12-29
trying to update 12.04 lts and i can't it show me this

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I dont have any problem  with the network, Help me please thanks

---

### Post by gnush on 2012-12-29
That website is down. Are you trying to update to a newer version of Ubuntu, or are you just doing a normal system update? If you're trying to update Ubuntu, I'd suggest re-installing everything instead, assuming you can back-up your files if needed.

---

### Post by ibjsb4 on 2012-12-29
> **closbar said:**
> trying to update 12.04 lts and i can't it show me this

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I dont have any problem  with the network, Help me please thanks

Those are maverick-backports and need to be removed if you running 12o4.

If you need help with this please [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
cat -n /etc/apt/sources.list
```

And post that

---

### Post by closbar on 2012-12-29
trying normal update.
thanks

---

### Post by closbar on 2012-12-29
ok done terminal 
```
  1    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise restricted main multiverse universe #Added by software-properties
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    11    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted main multiverse universe #Added by software-properties
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    17    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    18    
    19    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20    ## team, and may not be under a free licence. Please satisfy yourself as to 
    21    ## your rights to use the software. Also, please note that software in 
    22    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23    ## security team.
    24    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    25    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    26    
    27    ## Uncomment the following two lines to add software from the 'backports'
    28    ## repository.
    29    ## N.B. software from this repository may not have been tested as
    30    ## extensively as that contained in the main release, although it includes
    31    ## newer versions of some applications which may provide useful features.
    32    ## Also, please note that software in backports WILL NOT receive any review
    33    ## or updates from the Ubuntu security team.
    34    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    35    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    36    
    37    ## Uncomment the following two lines to add software from Canonical's
    38    ## 'partner' repository.
    39    ## This software is not part of Ubuntu, but is offered by Canonical and the
    40    ## respective vendors as a service to Ubuntu users.
    41    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    42    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    43    
    44    ## This software is not part of Ubuntu, but is offered by third-party
    45    ## developers who want to ship their latest software.
    46    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    47    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    48    
    49    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    50    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
    51    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    52    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    53    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe
    54    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe #Added by software-properties
    55    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
    56    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe #Added by software-properties
    57    deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    58    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
```
Thanks for your help

---

### Post by cariboo on 2012-12-30
I moved your last post to the jail, as it looked like a double post.

To solve your problem just comment out line 34 and 35:

```
34    #deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
35    #deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
```

like in the above code box. Just put a # sign before the deb in lines 34 & 35.

---

### Post by closbar on 2012-12-30
Thank for your help but how I can do that?
Thanks again

---

### Post by plucky on 2012-12-30
> **closbar said:**
> Thank for your help but how I can do that?
Thanks again

Edit the file **sources.list** 

```
gksudo gedit /etc/apt/sources.list
```

and as cariboo907 says > Just put a # sign before the deb in lines 34 & 35

Good Luck

---

### Post by closbar on 2012-12-30
thank you guys it is good now

---

### Post by BlinkinCat on 2012-12-30
Hi,

Remember to mark as solved via the Thread Tools Menu at top of page - :p

Cheers

---

