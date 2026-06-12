---
title: "some programs do not work.."
date: 2006-11-13
forum: General Help
---

### Post by cptjaben on 2006-11-13
My parents are divorced and because I spend a good deal of time on my computer, I bring the tower back and forth with me to each house. For some reason When i'm using the setup (my normal tower, speakers, monitor, etc) at my father's many of my programs (open office, amarok, kaffeine, etc.) do not run. However they work fine at my mothers house even though i'm using the same computer. the only real difference is that my mom's house has cable and my dad's satellite. Does anyone know why certain programs might not run if they are connect to different peripherals?

---

### Post by taurus on 2006-11-13
What programs are you talking about here?  Are you talking about the network apps?

---

### Post by cptjaben on 2006-11-13
Amarok, kaffeine, open office, k3b, kcalc, scribus. and totem moive player. when I run them in the terminal i get:

john@john:~$ amarok
Floating point exception (core dumped)

john@john:~$ k3b
ERROR: Communication problem with k3b, it probably crashed.

john@john:~$ kaffeine
ERROR: Communication problem with kaffeine, it probably crashed.

all of the rest give me the same as k3b and kaffeine did. any ideas?

---

### Post by taurus on 2006-11-13
Did you happen to upgrade from Dapper to Edgy recently???

---

### Post by cptjaben on 2006-11-13
Yes, I updated to edgy a few days after it was released.

---

### Post by taurus on 2006-11-13
And how did you upgrade it, not replacing dapper with edgy in /etc/apt/sources.list???

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by cptjaben on 2006-11-13
I upgraded it using Update Manager as seen [here]("https://help.ubuntu.com/community/EdgyUpgrades"). as far as dapper with edgy in /etc/apt/sources.list, I'm not exactly sure what you mean, how can I check?

---

### Post by taurus on 2006-11-13
Applications -> Accessories -> Terminal

```
cat /etc/apt/sources.list
```

---

### Post by cptjaben on 2006-11-13
When I type cat /etc/apt/sources.list into terminal I get this:

```
john@john:~$ cat /etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
# deb http://archive.canonical.com/ubuntu dapper-commercial main

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype (official)
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free
# deb http://www.getautomatix.com/apt dapper main
# deb http://www.beerorkid.com/compiz/ dapper main
# deb http://xgl.compiz.info/ dapper main
# deb-src http://xgl.compiz.info/ dapper main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

#compiz Quinn's
# deb http://www.beerorkid.com/compiz dapper main
# deb http://xgl.compiz.info/ dapper main
# deb-src http://xgl.compiz.info/ dapper main

# deb http://morgoth.free.fr/ubuntu dapper-backports main
# deb-src http://wine.budgetdedicated.com/apt dapper mainci

 # debian.scribus.net - Primary repository
# deb http://debian.scribus.net/debian dapper main restricted
# deb-src http://debian.scribus.net/debian dapper main restricted

# debian.tagancha.org - Backup repository    
# deb http://debian.tagancha.org/debian dapper main restricted
# deb-src http://debian.tagancha.org/debian dapper main restricted

```

IT looks like the more official looking sources got updated but not the all, not entirely sure.

---

### Post by taurus on 2006-11-13
And have you ran

```
sudo aptitude update
sudo aptitude upgrade
```
And if k3b and other apps still don't run, try to remove them and install them again...

---

### Post by cptjaben on 2006-11-13
I reinstalled various programs and their codecs and engines and I'm still having the same problem. The thing that i don't understand is that the programs seem to work fine when i'm connected to my mothers monitor, mouse speakers, internet, etc. is there any reason why one's computer might not run certain programs because of this?

---

### Post by cptjaben on 2006-11-14
When i edit my xorg.conf and change it from "fglrx" to "ati" and restart my computer, my programs seem to work again, but I can't change the resolution to higher than 800 by 600, does anyone got any ideas?

---

### Post by taurus on 2006-11-14
> **cptjaben said:**
> I reinstalled various programs and their codecs and engines and I'm still having the same problem. The thing that i don't understand is that the programs seem to work fine when i'm connected to my mothers monitor, mouse speakers, internet, etc. is there any reason why one's computer might not run certain programs because of this?
Wait a second.  In your original message, you said the only difference is the network connection, satellite and cable!!!  If you switch monitor, then you need to reconfigure your X since you would have a difference refreshing rates and what not...

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cptjaben on 2006-11-14
> My parents are divorced and because I spend a good deal of time on my computer, I bring the tower back and forth with me to each house. For some reason When i'm using the setup (my normal tower, speakers, monitor, etc)...the only real difference is that my mom's house has cable and my dad's satellite

sorry, i guess i had conflicting messages there, I meant the only main difference is that the internet is different, however the monitors are different as well but i didn't think that made a differnece.

---

### Post by cptjaben on 2006-11-14
After running sudo dpkg-reconfigure -phigh xserver-xorg and restarting, my programs appear to be working however, I cannot change my resolution any higher than 800 by 600. got any ideas on how to fix this? I have a radeon 9700 pro.

---

### Post by taurus on 2006-11-14
Well, you now need to install a driver for your ATI.

---

### Post by cptjaben on 2006-11-14
okay, I believe the problem has been solved. Thanks very much for the help and putting up with my lack of knowledge.

---

