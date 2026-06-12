---
title: "Oops. T_T I Broked Synaptic"
date: 2007-07-18
forum: General Help
---

### Post by DM was on fire! on 2007-07-18
I was trying to install my ATI drivers and I entered /etc/apt/sources.list in the custom field, and now Synaptic gives me this:

"E: Type '/etc/apt/sources.list' is not known on line 37 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

This is what I get for fooling with something I shouldn't.
Can someone help me? ^^;;

---

### Post by Happy_Man on 2007-07-18
Somehow, you messed up your sources.list. It's fixable, though; could you please post the output of ```
cat /etc/apt/sources.list
``` please?

---

### Post by DM was on fire! on 2007-07-18
> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

/etc/apt/sources.list
deb http://


[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
apt


I was trying to fix it on my own (not a good idea), and I entered the last three lines above on my own (only I didn't finish the "apt").

---

### Post by Nythain on 2007-07-18
remove these lines
```

/etc/apt/sources.list
deb http://
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
apt

```down at the bottom

Edit: on a side note... what version of ubuntu are you running, because you are mixing dapper and feisty ubuntu repos (thats not to good) and that debian sarge repo might not be a good idea (it theoretically could be if the version of ubuntu you are running is based on sarge and not a different release)

---

### Post by DM was on fire! on 2007-07-18
I'm running Dapper.
I think it was from back when I thought I was running Feisty (then I thought I was running Edgy, and FINALLY I learned because it was LTS and installed off of the disk, that I was running Dapper.

EDIT - YIPPEE! SYNAPTIC HAS BEEN UNBROKED. I think I can just deal with the fact my ATI drivers don't work. I'm not trying that for a long time.
I went ahead and removed all the Feisty stuff too. :D Thanks so much for your help. <3

*goes repo trawling*

---

