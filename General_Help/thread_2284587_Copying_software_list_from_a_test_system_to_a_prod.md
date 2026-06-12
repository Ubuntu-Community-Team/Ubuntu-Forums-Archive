---
title: "Copying software list from a test system to a prod system ?"
date: 2015-06-30
forum: General Help
---

### Post by georgesgiralt on 2015-06-30
Hello !
I've a test machine running 14.04 LTS. It has been carefully installed and tested for my needs. Now my system is quite perfect. 
So I want to make the production system by installing from scratch on a fresh machine and get EXACTLY the same packages I have on the test machine. 
I've searched a lot but all I managed to find is to clone the disk which I will not do because IP addresses, accounts names,... and a lot of configuration need to be redone to move from test to prod. 
Do you have a way to accomplish this ? Easily ? 
Many thanks in advance for your help.

---

### Post by mörgæs on 2015-06-30
If you open the 'upgrade' link in my signature and search for *get-selections* in the text you'll see a method.

---

### Post by slickymaster on 2015-06-30
Besides mörgaes' very good link, you can also have a read at this post, also by one of our staff members: [http://ubuntuforums.org/showthread.php?t=2154266&p=12690888&viewfull=1#post12690888](http://ubuntuforums.org/showthread.php?t=2154266&p=12690888&viewfull=1#post12690888)

---

### Post by georgesgiralt on 2015-06-30
Thank you both for your input which open a brand new field, but some part of my question remains. 
Should I install a vanilla Ubuntu version (and have the UEFI Boot process managed by this install) and then apply the package installation using the list i gathered from my test system 
Or is there a way to apply my selection on the new installation like I would have done using a KS file if I was on an RPM based system ?

---

### Post by Lars Noodén on 2015-06-30
You *could* do a kickstart even on Ubuntu but having done that myself a long while ago, unless you're doing hundreds of machines, I'd say that it's easier to use the [dpkg](http://manpages.ubuntu.com/manpages/trusty/en/man1/dpkg.1.html) method buried in mörgaes' signature link:

```

dpkg --get-selections > installed-software

////

sudo dpkg --set-selections < installed-software
sudo apt-get dselect-upgrade

```

Just be sure to get the configuration files from /etc and the data from where ever it may be.  That can be applied to a vanilla Ubuntu system.

---

### Post by georgesgiralt on 2015-06-30
Thank you !
I'll try your solutions and report back !

---

### Post by georgesgiralt on 2015-07-05
Hello !
So I ran into a list of problems. 
Apart for some configurations (icm screen calibration file, ergonomic mouse configuration... ) problems which I will solve easily, I've a lot of other more important problems. 
1)  When I run the "dpkg --set-selections < my-packages" command on my new system, I get tons of errors :
```

....................................
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-data
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-nox
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-plugin-jack
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-plugin-notify
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-plugin-pulse
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-plugin-sdl
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vlc-plugin-svg
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vorbis-tools
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1707*: vorbisgain
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1708*: wavpack
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1719*: wireshark
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1719*: wireshark-common
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1719*: wmctrl
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1735*: xdotool
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1739*: xfonts-unifont
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1740*: xine-ui
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1742*: xjadeo
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1744*: xmms2-core
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1744*: xmms2-plugin-id3v2
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1744*: xmms2-plugin-mad
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1744*: xmms2-plugin-mpg123
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xephyr
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-core
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-all
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-evdev
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-mouse
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-synaptics
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-vmmouse
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-input-wacom
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-all
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-ati
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-cirrus
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-fbdev
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-glamoregl
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-intel
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-mach64
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-mga
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-modesetting
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-neomagic
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-nouveau
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-openchrome
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-qxl
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-r128
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-radeon
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-s3
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-savage
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-siliconmotion
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-sis
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-sisusb
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-tdfx
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-trident
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-vesa
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1747*: xserver-xorg-video-vmware
dpkg*: avertissement*:*paquet non présent dans la base de données à la ligne 1752*: xvid4conf
dpkg*: avertissement*:*found unknown packages; this might mean the available database
is outdated, and needs to be updated through a frontend method

```
I then ran "apt-get update" and "apt-get upgrade" which put 304 upgraded  packages on my newly installed system. 
And reran the dpkg command. This gave the same error messages as above.
I would have understood the lack of Virtualbox packages as the ppa is not known to my new system, but X-server ?  and Linux kernel ? Something is wrong here ;-) 

Then I wondered how to get the ppa from my test machine to the new one. 
Of course, populating /etc/apt/sources.list.d  and /etc/apt/trusted.gpg.d is not enough, lacking the public keys for the ppa... 
So here is my second question :
2) could I simply copy the GPG files from the old system to the new one ? And have this run ? 

Many thanks in advance for your help ! 
Have a nice and bright day !

---

