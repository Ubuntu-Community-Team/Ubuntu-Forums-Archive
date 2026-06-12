---
title: "Broken packages."
date: 2007-02-03
forum: General Help
---

### Post by moshdj2uk on 2007-02-03
st of all, I'm VERY new to Ubuntu, and Linux for that matter. I have under 1 weeks worth of experience. However, I am a quick learner.

A package I was recently trying to install needed gcc/g++. After a failed install (due to the base package dependency missing), I had 4 broken packages.

Runnning **apt-get check** gave me:

```
Reading package lists... Done Building dependency tree Reading state information... Done You might want to run ‘apt-get -f install’ to correct these. The following packages have unmet dependencies. cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-21 is installed gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-21 is installed libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-21 is installed libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-21 is installed E: Unmet dependencies. Try using -f.
```


So, I went on to try **apt-get -f install** which gave:

```
Reading package lists... Done Building dependency tree Reading state information... Done Correcting dependencies...Done The following packages were automatically installed and are no longer required: xserver-xorg python-crypto xkeyboard-config f-spot libpopt-dev libgnomecupsui1.0-1c2a libopenexr2c2a gstreamer0.10-alsa liborbit2-dev python-alsaaudio mesa-utils xgamma xserver-xorg-video-rendition gcj-4.1-base xclipboard liblaunchpad-integration0 libcamel1.2-8 libopenobex-1.0-0 libwpd8c2a libarts1c2a libxmlsec1 libstdc++5 libstdc++6 tomboy xf86dga libglib-perl evolution-webcal ekiga libglew1 edgy-community-wallpapers gnome-cups-manager bitpim gsfonts-x11 dselect gnome-panel-data ssh-askpass-gnome xserver-xorg-video-cirrus linux-headers-2.6.17-10-generic sound-juicer libpisync0 hplip-data lftp libsdl-image1.2 libgdl-1-common libfaac0 libpanelappletmm-2.6-dev liba52-0.7.4 xditview libxine1 xutils-dev libsmpeg0... Use 'apt-get autoremove' to remove them. The following packages will be REMOVED acidrip acpi-support acroread adonthell amarok amarok-xine amsynth apache apache-common apache2-common apache2-mpm-prefork apollon apport apport-gtk apt apt-utils aptitude ark aspell audacity banshee beast beneath-a-steel-sky billard-gl bitpim bitpim-lib bluez-cups cdrdao cpp cpp-4.1 craft cupsys cupsys-driver-gutenprint deskbar-applet WARNING: The following essential packages will be removed. This should NOT be done unless you know exactly what you are doing! apt libgcc1 (due to apt) libstdc++6 (due to apt) 0 upgraded, 0 newly installed, 308 to remove and 0 not upgraded. Need to get 0B of archives. After unpacking 1154MB disk space will be freed. You are about to do something potentially harmful To continue type in the phrase ‘Yes, do as I say!’
```


**NOTE:** For the sake of the length, I shortened the list of packages above.

Something tells me that shouldn't be happening? Am I really going to lose practically all my installed packages if I attempt to fix the 4 broken ones? Is there a way around this?

Any help is appreciated!

---

### Post by r4ik on 2007-02-03
Synaptic -edit - fix broken packages.

Good luck !

---

### Post by Ramses de Norre on 2007-02-03
```
sudo aptitude install gcc-4.1-base/edgy
```
And remove any unofficial repositories from your sources.list, you've got package versions that aren't in the official repos and they obviously cause trouble.

---

### Post by moshdj2uk on 2007-02-04
Thanks for that. Seems to have fixed the problem.

All the URLs in the source list point to the Ubuntu archive.

---

