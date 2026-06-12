---
title: "Installing one package, many other packages must be removed"
date: 2016-10-02
forum: General Help
---

### Post by Daslee on 2016-10-02
So I want to install libglu1-mesa-dev and it wants to remove many other packages that are needed. Same thing happened like years ago when I tried to install Skype. I marked all those packages for removal and system screwed up, so I had to reinstall Ubuntu. Now I don't want to screw up my system, so I'm asking you guys, why the hell is this thing happening? Here is screenshot how it looks in synaptic package manager: [https://s21.postimg.org/tgfscsm5z/Screenshot_from_2016_10_02_23_23_20.png](https://s21.postimg.org/tgfscsm5z/Screenshot_from_2016_10_02_23_23_20.png)

If I try to install libglu1-mesa-dev package using apt-get, I get this error:
> The following packages have unmet dependencies: gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


---

### Post by mc4man on 2016-10-02
Post results of this, maybe something will stand out
```
apt-cache policy libgl1-mesa-glx libglu1-mesa libgbm1 libgl1-mesa-dri libosmesa6
```

---

### Post by Daslee on 2016-10-03
```
libgl1-mesa-glx:  Installed: (none)
  Candidate: 11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty
  Version table:
     11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
     10.1.3-0ubuntu0.6 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty-updates/main amd64 Packages
     10.1.0-4ubuntu5 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty/main amd64 Packages
libglu1-mesa:
  Installed: 9.0.0-2
  Candidate: 9.0.0-2
  Version table:
 *** 9.0.0-2 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
libgbm1:
  Installed: 10.1.3-0ubuntu0.5
  Candidate: 11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty
  Version table:
     11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
     10.1.3-0ubuntu0.6 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty-updates/main amd64 Packages
 *** 10.1.3-0ubuntu0.5 0
        100 /var/lib/dpkg/status
     10.1.0-4ubuntu5 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty/main amd64 Packages
libgl1-mesa-dri:
  Installed: (none)
  Candidate: 11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty
  Version table:
     11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
     10.1.3-0ubuntu0.6 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty-updates/main amd64 Packages
     10.1.0-4ubuntu5 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty/main amd64 Packages
libosmesa6:
  Installed: (none)
  Candidate: 11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty
  Version table:
     11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
     10.1.3-0ubuntu0.6 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty-updates/main amd64 Packages
     10.1.0-4ubuntu5 0
        500 http://ubuntu-archive.mirror.serveriai.lt/ trusty/main amd64 Packages
```

---

### Post by T2uiYKb7 on 2016-10-03
I've just skimmed over this but it sounds like you've removed an important dependency a couple of times. You removed a package that the core of Ubuntu has labelled as necessary, that it's **"dependent" **on. It doesn't always seem to make sense, Xubuntu has some odd one's that couldn't possibly effect the stability of the OS as a whole. 

But when those packages are removed important system packages say [B]"If that's gone we won't work so you have to get rid of us too, these no point in us sticking around."

[/B]If you remove a package and it says that a bunch of obviously important system packages also **"have"** to go, say no.

---

### Post by ian-weisser on 2016-10-03
> **Daslee said:**
> I'm asking you guys, why the hell is this thing happening?
It's happening because you are installing non-Ubuntu software intended for a different release or version of Ubuntu.
This happens most commonly when you try to install bleeding-edge software onto older systems.

Ubuntu is not a black-box operating system, with ever-consistent libs and system calls that you can install any software on top of.
The Ubuntu OS and applications are *integrated*; they only work if everything uses the same versions of the same dependencies. 
Your attempt to install bleeding-edge software forces dependency upgrades that break your system horribly.

Apt assumes that you know more than it does, and that you occasionally want to override it's mere machine logic for your own purposes.
When you tell it 'install this bleeding-edge package, and ignore the consequences. I want it.'
Well, you are sudo...it's going to warn you of the consequences and give you a chance to back out, and then it's going to execute your instruction.

---

### Post by mc4man on 2016-10-03
Your problems are from using the xorgers ppa, though not sure if you've installed anything from it yet.
(- though not having libgl1-mesa-dri installed  is curious & not good

If you have or can install synaptic do so, then open it  & under the Origin tab  highlight that ppa & see if any packages from that ppa are installed.
Meanwhile you could run this simulation & see what it says
```
sudo apt-get update
```
```
sudo apt-get -s dist-upgrade
```

Ultimately it may be best to use ppa-purge on the xorgers ppa & return to just Ubuntu xserver/mesa packages

---

### Post by Daslee on 2016-10-03
> **mc4man said:**
> Your problems are from using the xorgers ppa, though not sure if you've installed anything from it yet.
(- though not having libgl1-mesa-dri installed  is curious & not good

If you have or can install synaptic do so, then open it  & under the Origin tab  highlight that ppa & see if any packages from that ppa are installed.
Meanwhile you could run this simulation & see what it says
```
sudo apt-get update
```
```
sudo apt-get -s dist-upgrade
```

Ultimately it may be best to use ppa-purge on the xorgers ppa & return to just Ubuntu xserver/mesa packages

When I type xorg in synaptic, Origin tab, I can see some packages installed, such as xorg, noaveu display drivers (the one that I'm not using). In Software & Updates, Additional drivers tab I can see that I have X.Org X server.

As I can remember, I used that ppa to install nvidia drivers. So if I purge xorgers ppa, what happens to my gpu drivers? They will be deleted aswell? Or it will only delete X.Org X server gpu driver?

I actually installed mesa-common-dev package and now I have what I needed (for OpenGL development), but still I would like to resolve this problem.

---

### Post by mc4man on 2016-10-03
you can get nvidia drivers from this 'semi-official' ppa instead
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
I'd purge xorg-edgers and just use above instead, the value of xorg-edgers is diminishing 
```
sudo ppa-purge xorg-edgers
```

---

