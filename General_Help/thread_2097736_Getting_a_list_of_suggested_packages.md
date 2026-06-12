---
title: "Getting a list of suggested packages"
date: 2012-12-24
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-24
I tried to install Virtual Box 
```

sudo apt-get install virtualbox

```and this was the output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwvstreams4.6-base libuniconf4.6 libwvstreams4.6-extras
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgsoap1 virtualbox-dkms virtualbox-qt
[COLOR=Red][B]Suggested packages:
  virtualbox-guest-additions-iso vde2[/B][/COLOR]
The following NEW packages will be installed:
  libgsoap1 virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 4 newly installed, 0 to remove and 242 not upgraded.
Need to get 23.5 MB of archives.
After this operation, 70.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```Once I am done with installing, is there any command which will let me see what the suggested packages were in case I want to installed those later at some point of time? Also is there any apt-get switch which automatically installs the suggested packages side-by-side?

---

### Post by wojox on 2012-12-24
> **Holmes.Sherlock said:**
> I tried to install Virtual Box 
Once I am done with installing, is there any command which will let me see what the suggested packages were in case I want to installed those later at some point of time? Also is there any apt-get switch which automatically installs the suggested packages side-by-side?

Sure try: ```
apt-cache depends virtualbox
```

---

### Post by Holmes.Sherlock on 2012-12-24
> **wojox said:**
> Sure try: ```
apt-cache depends virtualbox
```
The output is
```

virtualbox
  Depends: libc6
  Depends: libcurl3
  Depends: libgcc1
  Depends: libgsoap1
  Depends: libpng12-0
  Depends: libpython2.7
  Depends: libsdl1.2debian
  Depends: libssl1.0.0
  Depends: libstdc++6
  Depends: libvncserver0
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxml2
  Depends: libxmu6
  Depends: libxt6
  Depends: zlib1g
  Depends: python
  Depends: python-central
  Depends: adduser
  Suggests: virtualbox-guest-additions-iso
  Suggests: vde2
 |Recommends: virtualbox-dkms
  Recommends: virtualbox-source
  Recommends: virtualbox-qt
 |Recommends: libgl1-mesa-glx
  Recommends: <libgl1>
    libgl1-mesa-glx
    libgl1-mesa-swx11
  Recommends: libqt4-opengl
  Recommends: libqtcore4
  Recommends: libqtgui4
  Conflicts: <virtualbox-2.0>
  Conflicts: <virtualbox-2.1>
  Conflicts: <virtualbox-2.2>
  Conflicts: <virtualbox-3.0>
  Breaks: virtualbox-ose
  Replaces: virtualbox-ose

```
What does "Breaks", "Replaces" mean? I have already installed virtualbox-ose package. Should I remove it?

---

### Post by Bucky Ball on 2012-12-24
And:
```

sudo apt-get autoremove

```... to remove packages that are no longer used.

Then try these two, one after the other:

```
sudo apt-get update
sudo apt-get upgrade
``` Agree to anything it wants to install or remove. Incidentally,

[COLOR=Red]**```
Suggested packages:   virtualbox-guest-additions-iso vde2
```**[/COLOR]... is the suggested package. You were doing fine before if you just hit 'y' and went ahead with what you posted before ...

---

