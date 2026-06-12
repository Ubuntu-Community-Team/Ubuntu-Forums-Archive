---
title: "Need a certain package, but cannot install due to unmet/broken dependencies."
date: 2013-04-18
forum: General Help
---

### Post by kaldor on 2013-04-18
I'm using Ubuntu 12.04.2 LTS with kernel 3.2 and the NVIDIA proprietary driver (nvidia-experimental-310 package).

A project I'm following requires the libgl1-mesa-dev:i386 package to be installed. However, upon attempting to install it I get this:

```
$ sudo apt-get install libgl1-mesa-dev:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dev:i386 : Depends: mesa-common-dev:i386 (= 9.0-0ubuntu1)
                        Depends: libgl1-mesa-glx:i386 (= 9.0-0ubuntu1)
                        Depends: libdrm-dev:i386 (>= 2.4.24)
                        Depends: libx11-xcb-dev:i386 but it is not going to be installed
                        Depends: libxdamage-dev:i386 but it is not going to be installed
                        Depends: libxext-dev:i386 but it is not going to be installed
                        Depends: libxfixes-dev:i386 but it is not going to be installed
                        Depends: libxxf86vm-dev:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

And then, just to try installing one of those dependencies:

```

$ sudo apt-get install libdrm-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdrm-nouveau1a:i386 libkms1:i386 libsvga1 mplayer
Suggested packages:
  mplayer-doc netselect fping
The following packages will be REMOVED:
  alsamixergui blender braid celestia-gnome compiz compiz-plugins
  compiz-plugins-main compiz-plugins-main-default fahviewer filezilla
  freeglut3 freeglut3-dev glew-utils gnome-mplayer google-earth-stable
  google-talkplugin ia32-crossover ia32-libs ia32-libs-multiarch:i386
  ia32-limbo ioquake3 libdrm-dev libfltk1.1 libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglew1.5
  libglew1.5-dev libglu1-mesa:i386 libglu1-mesa-dev libgtkglext1
  libgtkglext1-dev libgtkglextmm-x11-1.2-0 libosmesa6 libosmesa6:i386
  libqt4-opengl:i386 libsdl-gfx1.2-dev libsdl-net1.2-dev libsdl-ttf2.0-dev
  libsdl1.2-dev libswt-glx-gtk-3-jni libva-glx1 libvisual-0.4-plugins
  libvisual-0.4-plugins:i386 libwxgtk2.8-0 lonesurvivor mesa-common-dev
  mesa-utils mplayer2 netflix-desktop nux-tools nvidia-cg-toolkit openarena
  python-wxgtk2.8 teamviewer7 ubuntu-desktop unity vlc wine-compholio:i386
  wine1.5 wine1.5-amd64 wine1.5-i386:i386 xbmc xbmc-bin xorg
The following NEW packages will be installed:
  libdrm-dev:i386 libdrm-nouveau1a:i386 libkms1:i386 libsvga1 mplayer
0 upgraded, 5 newly installed, 67 to remove and 0 not upgraded.
Need to get 3,246 kB of archives.
After this operation, 1,525 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


```

Obviously I'm not going to do that. So, what's the most painless way to go about this?

---

### Post by schragge on 2013-04-18
[s]See [post=12587000]this post[/post][/s] [highlight]Edit[/highlight]. Sorry, it's not your situation.

---

### Post by Bashing-om on 2013-04-18
kaldor; Hi !

Is your installed system 64 bit, and the package to be installed 32 bit ?

sometimes dpkg gets confused with 32bit packages on 64bit system. 
Apply the command below
```
dpkg --print-foreign-architectures
```
if above command does not show any output then try
```
sudo dpkg --add-architecture i386
```
and 
```

sudo apt-get install -f
sudo apt-get update ; sudo apt-get dist-upgrade
```[INDENT=3]
see if this helps

[/INDENT]

---

### Post by mc4man on 2013-04-18
Your versions posted don't seem correct for 12.04. You can have 'normal' or the lts stack packages, but neither are "9.0-0ubuntu1"
(current avail are  8.0.4-0ubuntu0.4 or 9.0.3-0ubuntu0.1~precise1 or if proposed is enabled 9.0.3-0ubuntu0.1~precise2 

9.0-0ubuntu1 is a quantal package version??

Maybe run these 3 commands, may shed some light on

```
apt-cache policy libgl1-mesa-dev:i386 libgl1-mesa-dev-lts-quantal:i386
```
```
apt-cache policy libgl1-mesa-glx:i386 libgl1-mesa-glx-lts-quantal:i386
```
```
apt-cache policy libdrm-dev:i386 libdrm-dev-lts-quantal:i386
```

---

### Post by kaldor on 2013-04-18
> **mc4man said:**
> Your versions posted don't seem correct for 12.04. You can have 'normal' or the lts stack packages, but neither are "9.0-0ubuntu1"
(current avail are  8.0.4-0ubuntu0.4 or 9.0.3-0ubuntu0.1~precise1 or if proposed is enabled 9.0.3-0ubuntu0.1~precise2 

9.0-0ubuntu1 is a quantal package version??

Maybe run these 3 commands, may shed some light on

```
apt-cache policy libgl1-mesa-dev:i386 libgl1-mesa-dev-lts-quantal:i386
```
```
apt-cache policy libgl1-mesa-glx:i386 libgl1-mesa-glx-lts-quantal:i386
```
```
apt-cache policy libdrm-dev:i386 libdrm-dev-lts-quantal:i386
```

From the commands, it looks like something from a previous PPA causing a problem (x-swat). I haven't used this PPA since around August.

Output:

```
$ apt-cache policy libgl1-mesa-dev:i386 libgl1-mesa-dev-lts-quantal:i386
libgl1-mesa-dev:i386:
  Installed: (none)
  Candidate: 9.0-0ubuntu1
  Version table:
     9.0-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main i386 Packages
     8.0.4-0ubuntu0.4 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
     8.0.4-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     8.0.2-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libgl1-mesa-dev-lts-quantal:i386:
  Installed: (none)
  Candidate: 9.0.3-0ubuntu0.1~precise2
  Version table:
     9.0.3-0ubuntu0.1~precise2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages


```

```

$ apt-cache policy libgl1-mesa-glx:i386 libgl1-mesa-glx-lts-quantal:i386
libgl1-mesa-glx:i386:
  Installed: 9.0-0ubuntu1
  Candidate: 9.0-0ubuntu1
  Version table:
 *** 9.0-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     8.0.4-0ubuntu0.4 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
     8.0.4-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     8.0.2-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libgl1-mesa-glx-lts-quantal:i386:
  Installed: (none)
  Candidate: 9.0.3-0ubuntu0.1~precise2
  Version table:
     9.0.3-0ubuntu0.1~precise2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages



```

```

$ apt-cache policy libdrm-dev:i386 libdrm-dev-lts-quantal:i386
libdrm-dev:i386:
  Installed: (none)
  Candidate: 2.4.39-0ubuntu1
  Version table:
     2.4.39-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main i386 Packages
     2.4.39-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     2.4.32-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libdrm-dev-lts-quantal:i386:
  Installed: (none)
  Candidate: 2.4.39-0ubuntu1~precise1
  Version table:
     2.4.39-0ubuntu1~precise1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages



```

Thanks for the assistance thus far.

---

### Post by mc4man on 2013-04-19
I guess you could take care of in several different ways.

1. make sure the ppa is enabled, then use ppa-purge on. If successful then you'd likely get the current installed ppa packages set back to precise versions (the 0.8.x ones.

2. make sure ppa is enabled, open synaptic > Origin & note all the packages installed from the ppa. If there are lts-quantal versions then try to install them to replace the ones from ppa, then see where you stand.

3. manually remove & replace thru synaptic - could be a bit risky depending on what else gets removed. If you find no other way post complete list & I'll see what's involved...

4. acquire all the needed packages & use dpkg on, again some risk involved

(in 2.,  3. & 4.  you may be able to make things easier if any of the ppa packages can be removed without removing any  other packages you don't want removed, sometimes some -dev packages fit this.


Is this a 12.04 install upgraded to 12.04.2 (assuming yes) or a 12.04.2 install from the get go? If the former then ppa-purge may be best option.

---

### Post by pramiracetam on 2013-06-12
You are experiencing this bug [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606)

Some packages in the dependency have not been fully migrated to multiarch yet.  There are two workarounds listed in that bug report; a third option is using a 32bit chroot environment.

---

