---
title: "Which software to add to ubuntu, to make it a self supporting OS?"
date: 2008-03-24
forum: General Help
---

### Post by nappymonster on 2008-03-24
Hi all,
I'm going to install ubuntu for someone i know in may, and have several questions, as i myself have not been using ubuntu for very long.
Please bear in mind:
-It's going to be dual-booted with XP on a laptop, but only so that if he gets incredibly stuck he still has XP.
-He is not very computer literate.
-He wants it to function on it's own, so needs to get his outlook across, etc.

My questions are:
-Should i use gusty gibbon or hardy heron?
-What software needs to be downloaded to:
 -Use office documents (i.e which version of openoffice, or should i use something else)
 -Transfer Bookmarks etc from internet explorer.
 -Transfer all outlook files. (Evolution or Thunderbird?)
 -Have all the features the basic-average computer user needs to run properly.

Thanks,
Nappymonster

---

### Post by anaconda on 2008-03-24
Hi!

You should install all codecs, so that you can watch all types of video-formats, then install flash and java support..  and the ability to watch DVD-movies.(or if you want those pre-installed you might want to install Linux-mint, which is basically ubuntu with propietary codecs pre-installed..)

Gutsy or Hardy.. difficult choise. Hardy isn't released yet, BUT in my machine  it already works better than gutsy. Another point in hardys favour is that it is a long support version of ubuntu..

openoffice will be already installed..

Bookmarks can be transported.. I think you will need to manually export them from internet explorer..

I prefer thunderbird..

Pretty much all needed programs are already installed in a frech ubuntu installation..

---

### Post by very_japi on 2008-03-24
This is the script i run on every computer i install ubuntu into to get it up and running

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
echo "deb http://ppa.launchpad.net/do-core/ubuntu gutsy main" >> /etc/apt/sources.list
echo "deb http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://ppa.launchpad.net/tualatrix/ubuntu gutsy main" >> /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy main" >> /etc/apt/sources.list
echo "deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe" >> /etc/apt/sources.list
apt-get update
apt-get install amule libdvdcss2 gnome-bluetooth startupmanager inkscape rar unrar sensors-applet tilda grub-splashimages cheese pingus kopete gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse flashplugin-nonfree compizconfig-settings-manager fusion-icon vlc ubuntu-restricted-extras conky fusion-icon emerald sysinfo transmission thunderbird sunbird gmountiso oggconvert gimp-gap pidgin-plugin-pack gnome-art ubuntu-tweak lanmap scribus screenlets ubuntu-tweak timidity virtualbox sysinfo oggconvert k3b glade-gnome gnome-do gnome-vfs-obexftp --force-yes
aptitude safe-upgrade
```

should take care of everything. (applications, codecs, flash... everything) The catch is that this script is for gutsy gibbon so it probably needs some tweaking to work in hardy.


Also use Hardy Heron couse it imports IE and Mail setting during the installation.

---

### Post by IanW on 2008-03-24
I think the only tweak needed to run that script in hardy would be to replace each "gutsy" with "hardy".

BTW it lists fusion-icon, oggconvert & ubuntu-tweak twice, and Hardy comes with Transmission already installed.

---

### Post by sumguy231 on 2008-03-24
If I were you, I would just wait a month for Hardy Heron to be released before making the switch, because Hardy is an LTS release and supported for longer. As far as OpenOffice goes, a recent version is already included.

---

### Post by nappymonster on 2008-03-25
Thanks everybody but sumguy231, as i said in post 1, i'm doing this in may (over a months time) when hardy will be a stable release.

---

