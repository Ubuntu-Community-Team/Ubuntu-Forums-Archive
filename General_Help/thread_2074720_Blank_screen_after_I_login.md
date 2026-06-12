---
title: "Blank screen after I login"
date: 2012-10-22
forum: General Help
---

### Post by Green_Star on 2012-10-22
I upgraded from 1204 to 1210. After the upgrade, I rebooted and loged in at login screen. After login I dont see any panel, its just blank screen. I think it loged-in but couldnt load unity, in my 1204 I configure to auto start temp sensor and Cuttlefish, those windows are poped up, so I guess it is loggin in but couldn't load unity. If I insert audio CD, it pops up asking what I want to do with that audio cd. I tried creating brand new user from command prompt, still no luck with that new user.

---

### Post by Green_Star on 2012-10-22
I can see the Ubuntu One sync notifications too, so the startup applications are loading but I cant see the unity interface. 

When I tried to install ATI binary drivers from command prompt, 

when attempting to install the Catalyst Legacy drivers from the ATI binary package (12.6):


> DKMS part of installation failed.

...and the log...

> 
Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.97.100.3/build; sh make.sh --nohints --uname_r=3.5.0-2.fc17.x86_64 --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.97.100.3 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.3 from DKMS



Does some one know how to fix it?

---

### Post by Green_Star on 2012-10-22
I tried the new drivers from following link
[https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860478](https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860478)

still no luck. So I ran following command

> #sudo aticonfig -initial
No supported adaptors detected.

damn.

Couple of years back Linux just used to boot in to atleast minimal graphics mode, these new versions really sucks. 

How come a dumb user able to use Linux if it atleast cant boot into a gui?

---

