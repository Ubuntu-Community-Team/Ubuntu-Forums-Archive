---
title: "apt-get dist-upgrade wants to delete x-windows and stuff"
date: 2006-11-29
forum: General Help
---

### Post by Kallewoof on 2006-11-29
> 
$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-glx x-window-system-core xorg xserver-xorg xserver-xorg-core
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-newport xserver-xorg-driver-nsc
  xserver-xorg-driver-nv xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-sis xserver-xorg-driver-sisusb xserver-xorg-driver-tdfx
  xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-wacom
The following packages will be upgraded:
  linux-restricted-modules-2.6.15-27-386
  linux-restricted-modules-2.6.15-27-686 tar
3 upgraded, 0 newly installed, 44 to remove and 0 not upgraded.
Need to get 16.6MB of archives.
After unpacking 29.9MB disk space will be freed.
Do you want to continue [Y/n]? nope. not really...
Abort.


I figured this was a temporary issue, but it's been several days and the packages haven't been corrected. Any idas what's causing that?

-Kalle.

---

### Post by ciscosurfer on 2006-11-29
> **Kallewoof said:**
> I figured this was a temporary issue, but it's been several days and the packages haven't been corrected. Any idas what's causing that?

-Kalle.Do you get the same messages if you try using aptitude instead of apt-get?```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by az on 2006-11-29
Do you have mixed repositories?  Did you at one time have a foreign repository in your list?  Are you trying to downgrade some stuff?

---

### Post by taurus on 2006-11-29
Paste your /etc/apt/sources.list here!

```
cat /etc/apt/sources.list
```

---

### Post by brottman on 2006-11-29
Also, it would help a lot if you explained what you were trying to do. Are you trying to upgrade from Dapper to Edgy? Or are you on Edgy and just testing a dist-upgrade for giggles?

---

### Post by Kallewoof on 2006-11-29
How weird. I thought I subscribed to this list but I got no notifies. Sorry for late replies, folks!

I am using Edgy. I am not trying to do anything abnormal. I simply saw the "updates available" icon, clicked it, got an error which said "This is a bug!", so I tried apt-get dist-upgrade from a prompt instead, and got what you saw before.

Here's the /etc/apt/sources.list:
> 
$ cat /etc/apt/sources.list
deb [http://www.albertomilone.com/drivers/dapper/nonlegacy/32bit](http://www.albertomilone.com/drivers/dapper/nonlegacy/32bit) binary/

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy multiverse

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


As for using any foreign apt repos, I did use one at one point for NVidia drivers, but went back to using "Envy" since, when Ubuntu had a x-server upgrade, that repo didn't seem to handle it well.

-Kalle.

---

### Post by Kallewoof on 2006-11-29
> **ciscosurfer said:**
> Do you get the same messages if you try using aptitude instead of apt-get?```
sudo aptitude update && sudo aptitude dist-upgrade
```

This is what I got:

The following packages are BROKEN:
  xserver-xorg xserver-xorg-core 
The following packages will be upgraded:
  linux-restricted-modules-2.6.15-27-386 
  linux-restricted-modules-2.6.15-27-686 nvidia-glx tar 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.1MB of archives. After unpacking 1536kB will be used.
The following packages have unmet dependencies:
  xserver-xorg: Depends: xserver-xorg-video-all but it is not installable or
                         xserver-xorg-video which is a virtual package.
  xserver-xorg-core: Depends: xserver-xorg-video-all but it is not installable or
                              xserver-xorg-video which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
nvidia-glx [1.0.8776+2.6.17.6-1 (edgy-security, now)]

Score is 0

Accept this solution? [Y/n/q/?]

---

### Post by Kallewoof on 2006-11-30
> **Kallewoof said:**
> As for using any foreign apt repos, I did use one at one point for NVidia drivers, but went back to using "Envy" since, when Ubuntu had a x-server upgrade, that repo didn't seem to handle it well.

I looked again and realized I never actually removed the repo, I just ran envy on top of it. And removing that repo fixed the whole thing. Sorry for taking your time, folks.

-Kalle.

---

