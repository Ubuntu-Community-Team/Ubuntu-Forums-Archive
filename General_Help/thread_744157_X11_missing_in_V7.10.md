---
title: "X11 missing in V7.10 ?"
date: 2008-04-03
forum: General Help
---

### Post by kingkong22 on 2008-04-03
I just installed ubuntu v7.10 from desktop CD version. but only found /usr/include/X11/bitmaps existing. no x.h under X11. I think v7.10 
should include X11.  is my installation wrong or something wrong ?
please help. thanks a lot !!

---

### Post by Slushdoot on 2008-04-03
I'm not 100% sure, but might you need to install xorg-dev to get that?

---

### Post by kingkong22 on 2008-04-03
but it said
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-dev

---

### Post by Slushdoot on 2008-04-03
Hmm```
slushy@tacostand:~$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libc6-dev libdmx-dev libexpat1-dev libfontconfig1-dev libfontenc-dev
  libfreetype6-dev libfs-dev libice-dev libsm-dev libx11-dev libxau-dev
  libxaw-headers libxaw7-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxevie-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev
  libxi-dev libxinerama-dev libxkbfile-dev libxkbui-dev libxkbui1 libxmu-dev
  libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxrender-dev
  libxres-dev libxss-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev
  libxvmc-dev libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev linux-libc-dev
  x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dmx-dev x11proto-evie-dev x11proto-fixes-dev
  x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev
  x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xserver-xorg-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev libdmx-dev libexpat1-dev libfontconfig1-dev libfontenc-dev
  libfreetype6-dev libfs-dev libice-dev libsm-dev libx11-dev libxau-dev
  libxaw-headers libxaw7-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxevie-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev
  libxi-dev libxinerama-dev libxkbfile-dev libxkbui-dev libxkbui1 libxmu-dev
  libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxrender-dev
  libxres-dev libxss-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev
  libxvmc-dev libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev linux-libc-dev
  x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dmx-dev x11proto-evie-dev x11proto-fixes-dev
  x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev
  x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xorg-dev xserver-xorg-dev xtrans-dev zlib1g-dev
0 upgraded, 75 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.5MB of archives.
After unpacking 56.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
I have all the repos enabled, so that might be it.

---

### Post by Seisen on 2008-04-03
Post your source list

```
cat /etc/apt/sources.list
```

---

### Post by kingkong22 on 2008-04-03
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

---

### Post by mali2297 on 2008-04-03
> **kingkong22 said:**
> deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

Is that all!? :shock:

Do you have a GUI to work from?

---

### Post by kingkong22 on 2008-04-03
yes. in fact, after I checked out X11 missing, I googled for help first. I tried many different ways. they don't work in my hp dv6000.  that's the last try in source.list.

---

### Post by mali2297 on 2008-04-03
So you manually deleted all other lines in the file? Do you have a backup?

---

### Post by kingkong22 on 2008-04-03
sorry. no I don't have a backup.

---

### Post by mali2297 on 2008-04-03
I don't know if this is possible, but go to **System -> Administration -> Software Properties** and see if you can reenable the repositories.

Otherwise, copy/paste this content into your /etc/apt/sources.list:
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://packages.medibuntu.org/ gutsy free non-free 

```

Then run
```

sudo apt-get update

```

---

### Post by kingkong22 on 2008-04-03
I pasted souces.list and run sudo ... finally I got following errors
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 5696B in 1s (4492B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


So, What should I do next ? Thank you so much !!!

---

### Post by mali2297 on 2008-04-03
> **kingkong22 said:**
> I pasted souces.list and run sudo ... finally I got following errors
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 5696B in 1s (4492B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


So, What should I do next ? Thank you so much !!!

OK. For the time being, you can just comment out that last line. That is, put a # in front of the line, like this:
```

# deb http://packages.medibuntu.org/ gutsy free non-free

```
Then run *apt-get update* again.

EDIT:
...**or**, if you want to fix it, copy/paste into the terminal:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
sudo apt-get update

```

---

### Post by mali2297 on 2008-04-03
By the way, why do you need x.h?

---

### Post by kingkong22 on 2008-04-03
After I commented out the last line from sources.list, and re-run sudo apt-get update, then
I ran sudo apt-get install xorg-dev, X11 was installed fine. In fact, I want to install gtk and Qt, too. what commands do I need ? Thank you for great help.

---

### Post by WakkiTabakki on 2008-04-03
> **kingkong22 said:**
>  In fact, I want to install gtk and Qt, too. what commands do I need ? Thank you for great help.

Start synaptic from 'System / Administration / Synaptic package manager' and use the search function.

/N

---

### Post by mali2297 on 2008-04-03
> **kingkong22 said:**
> After I commented out the last line from sources.list, and re-run sudo apt-get update, then
I ran sudo apt-get install xorg-dev, X11 was installed fine. In fact, I want to install gtk and Qt, too. what commands do I need ? Thank you for great help.

```

sudo apt-get install build-essential libgtk2.0-dev libqt4-dev

```
Good luck on whatever project that you're planning.

---

### Post by kingkong22 on 2008-04-03
Thank you all !!!

---

