---
title: "No module for running kernel found."
date: 2008-07-07
forum: General Help
---

### Post by dchurch24 on 2008-07-07
Hi all,

Having a complete nightmare here.

I installed virtualbox and it completely buggered my video and sound drivers.

After some nightmarish hours sorting it (and recieving a lot of help from here) |I got it working again.

However, usually once the box is up and running it stays like it.

Sadly, we had a powercut today, and upon turning the machine on again, it just simply will not boot.

I get the error:

No module for kernel found
and also:

221.338826: ata4.00: status {DRDY ERR}

and then the whole thing cycles round it.

I can access the machine via ssh (using my laptop - hence being able to post here) and I can see the primary drive.

After about 20 mins it boots into some sort of blue screen and is filled with rubbish characters

I've taken out the sata drives one by one in 'hope' that one has become corrupted through the powercut (despite having anti-surge plugs), yet I get the same thing no matter what.

I am now at the end of my tether - I am at a complete loss, and am worried that if I ever do get this thing running again, I will be scared to install any software, or reboot the thing for fear of yet more problems.

I'm not a complete noob, but not far from it.

Does anyone know how I can turn this into a working machine once again?

When I ssh into the machine, none of the drives (aside from the IDE dvd drive) are seen in the /media folder, yet I can ls in the default folder and can see my home folder etc...

By the way, the two ata drives in it are almost brand new - less than 3 weeks old - the other one I had in it just died with no warning.  Does Ubuntu just eat drives? I once read an article that linux is harder on HDDs than any other OS by using them more.

I am almost at the point of just giving up and watching things like 'Eastenders' on TV like everyone else and leaving computers alone for as long as I live. I couldn't get on with Windows, can't stand the mac OS, and the OS I found that I can actually use does this sort of thing every now and then when I simply install a program.

Am I doomed?

---

### Post by dchurch24 on 2008-07-07
I just did:

sudo apt-get upgrade
and 
sudo apt-get update

and for some reason it seems to think that it's running Gutsy rather than Heron - this was a fresh Heron install when I installed it.

Something is very, very odd.

---

### Post by dentaku65 on 2008-07-07
> **dchurch24 said:**
> I just did:

sudo apt-get upgrade
and 
sudo apt-get update

and for some reason it seems to think that it's running Gutsy rather than Heron - this was a fresh Heron install when I installed it.

Something is very, very odd.

mmm, should be:
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
You cannot do upgrade prior to update

Can you post this?
```
cat /etc/apt/sources.list
```

---

### Post by dchurch24 on 2008-07-07
Sorry, it was the other way around, I'm getting tired and if I'm honest, a little annoyed with it now!!

The cat brings me this:

```

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
dave@dave-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse


```

Somehow, I have it booting into the login now, but it is so very, very, very slow. Unusably slow to be honest.

I'm attempting to log it in now, but each keypress takes about 5-10 minutes to register!
 
PS. Thanks for the quick reply, very much appreciated.

---

### Post by dchurch24 on 2008-07-07
Now I just have a message appear saying "There was an error starting the GNOME Sttings Daemon"

Just a quick note anyone thinking of installing Virtualbox on 8.04 - don't! ;-)

---

### Post by dchurch24 on 2008-07-07
Just did: top

remotely, and there is nothing using the processor - all 4 are about .001% in usage and the RAM (8gb) is barely used, yet every every keypress or mouse click takes a good 10 minutes to register.

All the video setting are gone, and it now just clones across the two screens. That I can handle - but the huge delay in doing anything makes the machine unuseable.

Not sure where I should turn next to be honest. Tried the live CD, but I don't want to reinstall if I can help it - I just don't want to lose all my data (Again!!)

I've just clicked the 'System' menu to see if I can get Synaptic up to uninstall vbox - it could take some time! lol

---

### Post by dchurch24 on 2008-07-08
Hmmmm - still no joy.

Anyone?

---

### Post by dchurch24 on 2008-07-08
Ok, this is one seriously fubared system.

I think it may be time to start again from scratch.

---

