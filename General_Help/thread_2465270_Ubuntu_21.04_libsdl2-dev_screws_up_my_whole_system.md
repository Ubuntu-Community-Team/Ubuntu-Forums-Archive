---
title: "Ubuntu 21.04: libsdl2-dev screws up my whole system"
date: 2021-07-28
forum: General Help
---

### Post by fpi1337 on 2021-07-28
Dear community,

this is my first post on this board and I'm not exactly sure if I'm doing it in the right section of this boards so please forgive me, if I did wrong!

My problem is pretty self-explaining if you're reading the title. I first encountered this problem with my fresh XUbuntu 21.04 installation a few days ago. At one point I noticed an error message while booting, telling me that the AppArmor profiles couldn't load properly, so XUbuntu just started in tty. I could start my display manager by typing in "startx" which was no problem at all. HOWEVER: My internet / apt-get install/apt update commands wouldn't work since I had no internet access anymore. Well, after I reinstalled XUbuntu, I began searching for the cause of all that. And there it was: I could reproduce it three times in a row with three newly installed XUbuntu partitions. The first thing and only thing to do to screw up the whole system is just installing libsdl2-dev by typing 

```
sudo apt-get install libsdl2-dev
```. 

After it was installed, I could reboot my system. However this would lead to the error I described above. 

My fourth try was actually installing a fresh new Ubuntu 21.04 (without XFCE). After installing libsdl2-dev my whole display manager (GNOME this time) went black and rebooting was screwed again. So I'm pretty sure that this package seems to be broken. Is there something to do about this package?

I'll install XUbuntu 20.04 hoping for a package version of libsdl2-dev not screwed.

UPDATE: I can confirm that this does not happen with (X)Ubuntu 20.04 - so it really is an issue with the 21.04 package of libsdl2-dev.

---

### Post by monkeybrain20122 on 2021-07-28
That's odd. I have that installed in ubuntu 21.04 no problem whatsoever. Do you have a nvidia card?

---

### Post by fpi1337 on 2021-07-28
Yep, I have a NVIDIA card (GTX 970)... It somehow uninstalls some packages which is pretty odd. Is something wrong with NVIDIA cards? However it also affects my internet access - that's pretty odd too.

---

### Post by monkeybrain20122 on 2021-07-28
I think Nvidia may be responsible for some graphic glitches and black screen, but it doesn't explain the apparmor profile couldn't load. Since you are installing and uninstalling anyway can you make a fresh install in one of your test partition without any Nvidia proprietary driver and see if you still experience problems? Just want to narrow down what causes it.

---

### Post by fpi1337 on 2021-07-29
Hi monkeybrain,

thank you for your tip. I'll do a fresh install on my laptop, since 20.04 seems to run stable now. And yes indeed: I always check the box "install third party software" when I install Ubuntu. This probably contains the NVIDIA drivers as well. I will keep you updated! :)

---

### Post by fpi1337 on 2021-07-29
I've got an update for you:

Now I can confirm that the libsdl2-dev installation really screws up everything. Check my terminal log:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

fpi@fpi-VPCEH3J1E:~$ sudo apt-get install libsdl2-dev
[sudo] password for fpi: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  appstream apt-config-icons aptdaemon-data apturl-common
  chromium-codecs-ffmpeg-extra colord-data dns-root-data dnsmasq-base
  gir1.2-goa-1.0 gir1.2-javascriptcoregtk-4.0 gir1.2-nm-1.0 gir1.2-snapd-1
  gir1.2-soup-2.4 gir1.2-vte-2.91 gir1.2-webkit2-4.0 gnome-software-common
  gstreamer1.0-vaapi libappstream-glib8 libappstream4 libbluetooth3
  libbrlapi0.8 libcolorhug2 libept1.6.0 libgspell-1-2 libgspell-1-common
  liblzo2-2 libmalcontent-0-0 libmbim-glib4 libmbim-proxy libmm-glib0 libndp0
  libnetplan0 libnm0 libnma-common libnma0 libnvidia-cfg1-390
  libnvidia-common-390 libnvidia-decode-390 libnvidia-encode-390
  libnvidia-fbc1-390 libnvidia-gl-390 libnvidia-ifr1-390 liboobs-1-5
  libplymouth5 libqmi-glib5 libqmi-proxy libreoffice-help-common libstemmer0d
  libteamdctl0 libva-wayland2 libxapian30 libxnvctrl0
  mobile-broadband-provider-info modemmanager nvidia-compute-utils-390
  nvidia-kernel-source-390 nvidia-prime nvidia-utils-390 ppp pptp-linux
  pulseaudio-module-bluetooth python3-dateutil python3-debconf python3-debian
  python3-defer python3-netifaces python3-software-properties shimmer-themes
  squashfs-tools system-tools-backends tcl unattended-upgrades
  update-notifier-common usb-modeswitch usb-modeswitch-data xbrlapi
  xserver-xorg-video-nvidia-390 xubuntu-wallpapers
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gir1.2-ibus-1.0 gir1.2-polkit-1.0 libasound2-dev libblkid-dev libc-dev-bin
  libc-devtools libc6-dev libcrypt-dev libdbus-1-dev libegl-dev
  libegl1-mesa-dev libffi-dev libgl-dev libgl1-mesa-dev libgles-dev libgles1
  libgles2 libglib2.0-0 libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin
  libglu1-mesa-dev libglvnd-dev libglx-dev libibus-1.0-5 libibus-1.0-dev
  libice-dev libmount-dev libnetplan0 libnsl-dev libnss-systemd libopengl-dev
  libopengl0 libpam-systemd libpcre16-3 libpcre2-16-0 libpcre2-dev
  libpcre2-posix2 libpcre3-dev libpcre32-3 libpcrecpp0v5 libpolkit-agent-1-0
  libpolkit-gobject-1-0 libpthread-stubs0-dev libpulse-dev
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libselinux1-dev libsepol1-dev
  libsm-dev libsndio-dev libsystemd0 libtirpc-dev libudev-dev libudev1
  libwayland-bin libwayland-dev libx11-dev libxau-dev libxcb1-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxi-dev
  libxinerama-dev libxkbcommon-dev libxrandr-dev libxrender-dev libxss-dev
  libxt-dev libxv-dev libxxf86vm-dev linux-libc-dev manpages-dev mate-polkit
  mate-polkit-common policykit-1 pulseaudio pulseaudio-module-bluetooth
  pulseaudio-utils python3-distupgrade python3-distutils python3-lib2to3
  python3-update-manager rpcsvc-proto systemd systemd-sysv systemd-timesyncd
  ubuntu-release-upgrader-core udev update-manager-core update-notifier-common
  uuid-dev x11proto-dev x11proto-input-dev x11proto-randr-dev
  x11proto-scrnsaver-dev x11proto-xext-dev x11proto-xf86vidmode-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
Suggested packages:
  libasound2-doc glibc-doc libgirepository1.0-dev libglib2.0-doc libxml2-utils
  libice-doc libsm-doc libwayland-doc libx11-doc libxcb-doc libxext-doc
  libxt-doc pavumeter paprefs ubuntu-sounds systemd-container
Recommended packages:
  rtkit dbus-user-session
The following packages will be REMOVED:
  aptdaemon apturl blueman brltty brltty-x11 colord dbus-user-session
  friendly-recovery gnome-software gnome-software-plugin-snap
  gnome-system-tools language-selector-gnome lightdm netplan.io
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nvidia-settings packagekit packagekit-tools
  plymouth plymouth-label plymouth-theme-ubuntu-text
  plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text policykit-1-gnome
  python3-aptdaemon python3-aptdaemon.gtk3widgets rtkit
  screen-resolution-extra snapd software-properties-common
  software-properties-gtk synaptic ubuntu-minimal ubuntu-release-upgrader-gtk
  ubuntu-standard update-manager update-notifier xiccd xubuntu-artwork
  xubuntu-core xubuntu-default-settings xubuntu-desktop

 ...
 
```

You can see that many necessary files got removed. For  example xubuntu-desktop AND the network-manager. No wonder that I have  no internet access nor a desktop on startup anymore. However I installed  it on my laptop now (with third party software). I'll try to install it  without any third party software now and check if this weird issue  still persists.

UPDATE: Even without the third party software the issue still persists.

---

### Post by monkeybrain20122 on 2021-07-29
Indeed that is super odd. This is a clean install right? (no upgrade, no /home partition)  Actually looking at the debian file inside the .deb the only thing that is in conflict with libsdl2 is libsdl1. Like I said I have libsdl2 and libsdl2-dev installed in Ubuntu 21.04 and there is no problem whatsoever.

---

### Post by Impavidus on 2021-07-29
You've got a long list of autoremovable packages. This may happen after you removed some other software with a lot of dependencies, but shouldn't happen after a fresh install. Many are packages I would expect on every Xubuntu system.

Installing libsdl2-dev triggers the installation of many other packages, mostly dev packages for various libraries. I didn't check all of them, but there doesn't seem to be anything suspicious about that list. But any of those packages could trigger removal of the packages in the final list, not just libsdl2-dev itself.

That final list is suspicious. When I mark libsdl2-dev for installation in synaptic on Xubuntu 21.04, I do get a list of additional packages to install, fairly similar to your list, but it doesn't want to remove anything. Removing xubuntu-desktop itself isn't something to worry about (it doesn't contain any software, but only triggers installation of other packages with software), but it indicates that something else, considered a core component of the Xubuntu flavour, is removed. Definitely weird.

Could you show the output of```
cat /etc/apt/sources.list
sudo apt update
```
If there's something wrong with your software sources, you may get strange effects. For example, installing libsdl2-dev (latest version) may trigger upgrading of some dependency to the latest version, which is incompatible with something important that must be upgraded too, but can't as faulty software sources don't point to the latest version of that important package, causing removal of that important package.

A few weeks back I had someone on the forums with a very weird problem, that was ultimately traced back to a faulty repository mirror, so changing to the main server is another thing you can try.

---

### Post by fpi1337 on 2021-07-30
@monkeybrain

yep, that's a fresh install. I basically installed it and installed libsdl2-dev right after the first startup. There were no steps inbetween.

@Impavidus

I just reinstalled 21.04 and I got these entries in my sources.list (+ terminal output of sudo apt update):

```
fpi@fpi-VPCEH3J1E:~$ cat /etc/apt/sources.list
#deb cdrom:[Xubuntu 21.04 _Hirsute Hippo_ - Release amd64 (20210420)]/ hirsute main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hirsute main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hirsute-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ hirsute universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute universe
deb http://de.archive.ubuntu.com/ubuntu/ hirsute-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ hirsute multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hirsute-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ hirsute-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hirsute-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu hirsute partner
# deb-src http://archive.canonical.com/ubuntu hirsute partner

deb http://security.ubuntu.com/ubuntu hirsute-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hirsute-security main restricted
deb http://security.ubuntu.com/ubuntu hirsute-security universe
# deb-src http://security.ubuntu.com/ubuntu hirsute-security universe
deb http://security.ubuntu.com/ubuntu hirsute-security multiverse
# deb-src http://security.ubuntu.com/ubuntu hirsute-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
fpi@fpi-VPCEH3J1E:~$ sudo apt update
[sudo] password for fpi: 
Hit:1 http://de.archive.ubuntu.com/ubuntu hirsute InRelease
Hit:2 http://de.archive.ubuntu.com/ubuntu hirsute-updates InRelease
Hit:3 http://security.ubuntu.com/ubuntu hirsute-security InRelease
Hit:4 http://de.archive.ubuntu.com/ubuntu hirsute-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
159 packages can be upgraded. Run 'apt list --upgradable' to see them.
fpi@fpi-VPCEH3J1E:~$ 

```

If I check the packages to be installed/removed in Synaptic, I experience the same issue. Maybe you're right and there's indeed something wrong with my sources. Is there any fix for that?

---

### Post by Impavidus on 2021-07-30
I use nl.archive.ubuntu.com (I'm on the other side or de border), but de.archive.ubuntu.com is usually reliable and all normal sources are listed.

I forgot to ask before, but did you install all available upgrades after installing Ubuntu, before attempting to install any additional software?

---

### Post by fpi1337 on 2021-07-30
> **Impavidus said:**
> I use nl.archive.ubuntu.com (I'm on the other side or de border), but de.archive.ubuntu.com is usually reliable and all normal sources are listed.

I forgot to ask before, but did you install all available upgrades after installing Ubuntu, before attempting to install any additional software?

Thank you for your answer! No I did not upgrade my packages but I did so just now. And what can I say? libsdl2-dev will install properly now! No packages to be removed or something else! 

But still, the question remains: why is that so? I mean, upgrading isn't really a must, isn't it (it is for installing that package obviously)? I never experienced such a weird issue with any other distribution but I guess I was just lucky. I almost never upgrade my packages since normally every package I want to install would upgrade its dependencies automatically if needed by apt. I expected that libsdl2-dev would act that way too but unfortunately it didn't. 

However: problem solved! :)

---

### Post by Impavidus on 2021-07-31
When you install a new package, its dependencies may have to be upgraded. The dependencies of those dependencies may have to be upgraded too, and then the other packages depending on those upgraded dependencies may have to be upgraded too. I never tried to find out how apt handles this. Does it upgrade a whole bunch of packages or does it remove some? I don't know.

Anyway, those upgrades are created for a reason. I always install all of them. It never gave me serious issues. I've been using Ubuntu for 15 years. You can postpone upgrades to a convenient time, but better not ignore them.

---

### Post by fpi1337 on 2021-07-31
Yeah, I know that. I was introduced to Linux (first with OpenSUSE in 2007/8 and later with Ubuntu (late 2008)) back in the days. apt never changed its scheme. To that day every distro I used downloaded it that way you described it. EVERY dependency got resolved, even if that meant downloading a newer version of a already installed package. That's why I am so curious about this specific case. Normally apt (Synaptic as well) would have updated the outdated packages before installing libsdl2-dev. 

As you are here already, there's another question, since you also use 21.04: Will you switch/reinstall your Ubuntu version when the support runs out? As far as I know, 21.04 won't be supported anymore in the next year.

---

### Post by Impavidus on 2021-07-31
I think I'll upgrade to 21.10 in December. I normally upgrade in December and June, but about once every 4 releases (not exact) I do a fresh install instead. My current system was installed as 20.04 and has been upgraded twice.

---

