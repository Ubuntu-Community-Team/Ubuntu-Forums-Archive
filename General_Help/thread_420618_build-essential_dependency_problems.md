---
title: "build-essential dependency problems"
date: 2007-04-23
forum: General Help
---

### Post by sojyujai on 2007-04-23
I'm having problems getting my mic to work and it looks like the solution will be to recompile my alsa drivers with the latest version a la [this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto").  I start out with trying to install build-essential and get the following errors:

```
dave@dave-ubuntu:~$ sudo apt-get install build-essential ncurses-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev instead of ncurses-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  libncurses5-dev: Depends: libc-dev
E: Broken packages
```

So, playing around with Synaptic I see that the version of build-essential in the repositories is 11.3 and this depends on libc6-dev (version in repos = 2.5-0ubuntu11) and this in turn depends on libc6 (2.5-0ubuntu11).

Somehow my installed version of libc6 is 2.5-0ubuntu14 which according to the dependencies is incompatible with libc6-dev 2.5-0ubuntu11.  If I try to force a downgrade the version of libc6 to 2.5-0ubuntu11  I am told I have to also remove the following packages:
libc-i686
ubuntu-minimal

and this seems like it would be a bad idea.

An other option I guess would be to install libc6-dev version 2.5-0ubuntu14 if it exists, but I can't seem to find it in the repositories.

So does anyone know if installing libc6-dev (2.5-0ubuntu14) would solve the problem, and if so how I can install it?  Or is there another solution to this I'm unaware of?

---

### Post by rjfioravanti on 2007-04-23
Did you recently upgrade from edgy to feisty or something similar? 

One thing that could cause this maybe is drawing from different sources... maybe output your /etc/apt/sources.list file?

what happens if you do sudo apt-get update followed by sudo apt-get upgrade

---

### Post by sojyujai on 2007-04-23
> **rjfioravanti said:**
> Did you recently upgrade from edgy to feisty or something similar? 

One thing that could cause this maybe is drawing from different sources... maybe output your /etc/apt/sources.list file?

what happens if you do sudo apt-get update followed by sudo apt-get upgrade

Thanks for the reply, this was a fresh feisty install but I've been fiddling with it non-stop since I installed it a few days ago so who knows what I might have done...  

Strange I tried the apt-get update/upgrade last night with no joy but decided to try it again after your reply and now it seems the problem has been fixed!  Not sure why, I've been using the local singapore ubuntu repositories, I wonder if there was something screwy happening with them last night?  More likely something I did wrong.  But it's fixed now so thanks for the help!

---

### Post by aysiu on 2007-04-23
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

