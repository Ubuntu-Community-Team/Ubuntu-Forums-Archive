---
title: "Ubuntu 14.04 Hardware Enablement Stack"
date: 2015-02-06
forum: General Help
---

### Post by craig10x on 2015-02-06
I have asked this before but please help refresh my memory...Right now i am running 14.10 but considering re-installing 14.04 and staying on LTS to the next LTS becomes available...Now, i need to do the install over the weekend, and was hoping 14.04.2 would be out (which it isn't due to problems they are having) so i would have to go with 14.04.1

Now, when 14.04.2 releases and you can get the stack, i'd want to install it then to get the 3.16 kernel from utopic...

1) Could you give me the terminal command i'd need at that time?
2) How would you know when you could install it?  Does it become available as soon as the point release arrives?
3) I have seen command for this, some including something called "mesa" and some not...what's that? and is it a good thing to have?

Thanks ;)

Oh, and i promise to save the info you give me, so i will have it handy when i need it and don't need to ask again :mrgreen:

---

### Post by mc4man on 2015-02-06
you can find commands, info in here maybe
[http://ubuntuforums.org/showthread.php?t=2263097](http://ubuntuforums.org/showthread.php?t=2263097)

The kernel is usually easy, currently it's in trusty -proposed so had already tested installing - 
```
sudo apt-get  install --install-recommends linux-generic-lts-utopic
```

mesa can sometimes be an issue, didn't bother  as I already have some  advanced packages & don't think it would provide anything needed here anyway.

---

### Post by craig10x on 2015-02-06
I just installed 14.04 again...have it up and running...is it ok to apply that command now to get the 3.16 kernel...or is it best to wait for the 14.04.2 release?
Also, is that the only thing i need, would i have the latest hardware updates automatically on my 14.04.1 when 14.04.2 is out?
And, after installing, would i be getting updates on the kernel through the software updater?
Oh, and what about the xorg stack? seems like that command would only update the kernel...wouldn't you want to also add the xorg stuff as well?

---

### Post by craig10x on 2015-02-07
I'm still confused about all this business...i wanted to know how to get the stuff you won't get automatically when each point release comes out (like the forthcoming 14.04.2)...you know: kernel, latest xorg stuff, and whatever else one would get automatically if he installed the actual latest point release...
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

When i read the wiki, they show how to get the kernel and the xorg stack for precise, and yet for TRUSTY they only show you how to get the new kernel...
Some have mentioned the mesa packages are not needed, but even if so, how would you get both kernel and xorg stack for TRUSTY?  Wouldn't you want both?  Or is there some reason they suggest only the kernel update?
This is what has me very confused...

---

### Post by craig10x on 2015-02-08
Anyone else have any thoughts on this?  I know a  lot use LTS so i am surprised there isn't more general knowledge of how this is handled...:(

---

### Post by mc4man on 2015-02-08
I would assume that when .2 is ready they may post a 'safe' command to install the mesa stack. Whether they do or not won't change the fact that it is not going to work for all users & may do some decent damage.
Any posted command would likely assume & have been tested on a generic install of 14.04.1 & can't anticipate any user changes to their 14.04.1 install.

So any attempt should be done with a simulation first, looking for newly installed & removed closely. Just because the new mesa packages are installed doesn't mean it's being done correctly.

Ex. here on my main install. I had to remove some -dev packages first to even get a possible install.
old command a no go  - 
> sudo apt-get install -s --install-recommends  libgl1-mesa-glx-lts-utopic
......
The following packages have unmet dependencies:
 libgl1-mesa-glx-lts-utopic : Depends: libglapi-mesa-lts-utopic (= 10.3.2-0ubuntu1~trusty1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

adding to it presents & would do  a 'bad' install (there are numerous varitions of this bad install based on command
```
sudo apt-get install -s --install-recommends xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic
....
The following extra packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libandroid-properties1
  libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0
  libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3
  libegl1-mesa-lts-utopic libepoxy0 libevdev2 libgbm1-lts-utopic libgflags2
  libgl1-mesa-dri-lts-utopic libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic
  libgles2-mesa-lts-utopic libgoogle-glog0 libhud-client2 libhybris-common1
  libjsoncpp0 libllvm3.5 liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0
  libmirclient7 libmirclientplatform-mesa libmirplatform
  libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18 libprocess-cpp1
  libqdjango-db0 libqmenumodel0 libqt5xmlpatterns5
  libubuntu-application-api-mirserver1 libubuntu-location-service0
  libubuntu-platform-hardware-api1 libunity-api0 libunity-mir1
  libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1
  libusermetricsoutput1 libxatracker2-lts-utopic libzmqpp3
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic mediascanner2.0 python3-apparmor
  python3-apparmor-click python3-click python3-libapparmor qmenumodel-qml
  qtdeclarative5-dee-plugin qtdeclarative5-gsettings1.0
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-video-all-lts-utopic xserver-xorg-video-ati-lts-utopic
  xserver-xorg-video-cirrus-lts-utopic xserver-xorg-video-fbdev-lts-utopic
  xserver-xorg-video-intel-lts-utopic xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mga-lts-utopic xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
Suggested packages:
  content-hub fdutils linux-lts-utopic-tools sqlite3-doc xfonts-100dpi
  xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux
Recommended packages:
  libegl1-mesa-drivers-lts-utopic unity-scope-click
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo cheese empathy gir1.2-totem-1.0 gnome-contacts
  gnome-control-center gstreamer1.0-clutter indicator-bluetooth
  libcheese-gtk23 libcheese7 libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libegl1-mesa
  libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgles1-mesa libgles2-mesa libopenvg1-mesa libtotem0 libwayland-egl1-mesa
  libxatracker2 mcp-account-manager-uoa mesa-vdpau-drivers
  nautilus-sendto-empathy totem totem-mozilla totem-plugins
  unity-control-center unity-control-center-signon
  webaccounts-extension-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xul-ext-webaccounts
The following NEW packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libandroid-properties1
  libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0
  libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3
  libegl1-mesa-lts-utopic libepoxy0 libevdev2 libgbm1-lts-utopic libgflags2
  libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0 libllvm3.5
  liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7
  libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa
  libmirprotobuf0 libmirserver18 libprocess-cpp1 libqdjango-db0 libqmenumodel0
  libqt5xmlpatterns5 libubuntu-application-api-mirserver1
  libubuntu-location-service0 libubuntu-platform-hardware-api1 libunity-api0
  libunity-mir1 libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1
  libusermetricsoutput1 libxatracker2-lts-utopic libzmqpp3
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic mediascanner2.0 python3-apparmor
  python3-apparmor-click python3-click python3-libapparmor qmenumodel-qml
  qtdeclarative5-dee-plugin qtdeclarative5-gsettings1.0
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic
  xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
0 upgraded, 114 newly installed, 71 to remove and 10 not upgraded.
```

Note ^ 114 new, 71 removed, some of the installed have no place in 14.04 like unity8 ect., & some removed aren't replaced

So this is pretty clean here on this install - 
```
sudo apt-get install -s --install-recommends xserver-xorg-lts-utopic \
libgl1-mesa-glx-lts-utopic libgl1-mesa-dri-lts-utopic libgles2-mesa-lts-utopic \
libgles1-mesa-lts-utopic libopenvg1-mesa-lts-utopic  xserver-xorg-core-lts-utopic

```

```
sudo apt-get install -s --install-recommends xserver-xorg-lts-utopic \
> libgl1-mesa-glx-lts-utopic libgl1-mesa-dri-lts-utopic libgles2-mesa-lts-utopic \
> libgles1-mesa-lts-utopic libopenvg1-mesa-lts-utopic  xserver-xorg-core-lts-utopic
......
The following extra packages will be installed:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libglapi-mesa-lts-utopic libllvm3.5
  libwayland-egl1-mesa-lts-utopic libxatracker2-lts-utopic
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-video-all-lts-utopic xserver-xorg-video-ati-lts-utopic
  xserver-xorg-video-cirrus-lts-utopic xserver-xorg-video-fbdev-lts-utopic
  xserver-xorg-video-intel-lts-utopic xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mga-lts-utopic xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
Suggested packages:
  fdutils linux-lts-utopic-tools xfonts-100dpi xfonts-75dpi
  gpointing-device-settings touchfreeze firmware-linux
The following packages will be REMOVED:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libgles1-mesa libgles2-mesa libopenvg1-mesa
  libwayland-egl1-mesa libxatracker2 mesa-vdpau-drivers xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libllvm3.5 libopenvg1-mesa-lts-utopic libwayland-egl1-mesa-lts-utopic
  libxatracker2-lts-utopic linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic
  xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
0 upgraded, 49 newly installed, 43 to remove and 10 not upgraded.
....
```
Note only 43 removed & 49 installed, inc. in the 49 installed are the kernel packages so pretty much tit for tat & likely a good install of the lts stack *on this machine*

Now if I run this same command on another older 14.04.1 install I have it fails, why?, who knows. likely from some package(s) previously installed

Best surefire way to get 14.04.2 - do a fresh install

---

### Post by craig10x on 2015-02-08
@mc4man: Thanks for coming back with that :D
Ah, i see now that it can be rather tricky...hmmm

Hoping it would be simple and foolproof...lol  I didn't really want to have to install to FULLY get each new incremental release (by fully, i mean new kernels, drivers and all of course)....
Make me re-think a bit about whether i might be better off just upgrading this to 14.10 again and continue my upgrades to each new 6 month version of ubuntu....The upgrades (using the software updater) for me have been 100% perfect each time and effortless...the upgrade even cleaned up the no longer needed stuff for me (including old kernels) so might be the better way to go....

I thought upgrading the stacks would be as simple and smooth, so for that reason, i was willing to go the LTS to LTS route....but for a techno phobe like me, perhaps better to go back to the 6 month upgrade method instead...

Unless those problems relate to the fact that the xorg and mesa stuff from utopic is not yet showing in the package manager (I don't have proposed enabled) and perhaps there are still bugs (which is part of the reason that 14.04.2 had been delayed to feb 19th among other problems)

Perhaps i should "sit tight" until the final release? (less risky then?)

---

### Post by mc4man on 2015-02-08
I would certainly wait till the 19th or so & see what shakes out.
The kernel install will generally be a piece of cake plus it's non critical. By that I mean there's no real risk of needed packages being removed & users can always just boot to the previous kernel if there is some issue.

On the other hand mesa packages don't 'co-exist'. So the lts upgrade removes the current ones & if there is some issue with the install, well,  there is no 'easy'  alternative at that point.
That's why no matter who or where gives some command for mesa you or anyone should always simulate first & read carefully before committing to an actual install/replacement of the X stack packages.
Generally speaking the number of packages removed should match or be very close to the number being installed for mesa.

Also part of the point release are a number of SRU updates but all 14.04 users will get those anyway.

The question of whether to stick on an lts to next lts is more a personal choice than one of better or worse. Here I'm staying on 14.04 until I can better see what 16.04 & later will be like on a desktop install. The main determining factor for me about 16.04 is whether unity7 & compiz remain which is looking quite likely.
The decision here about 16.04+ will be,  do I like unity8/next, so far   nothing has been made  available to make that judgment. My initial feeling solely based on partial descriptions is I won't. 

( the other elephant in my room is - if Canonical isn't successful in terms of Oem for phones & tablets then does it really have a long term future after 18.04 or so??

---

### Post by craig10x on 2015-02-08
Thanks....i decided to go back to 14.10...another 100% perfect upgrade...i figured...heck...i upgrade to each new version, it goes smooth as silk and at the end it even cleans up and removes obsolete files...what more can you ask for?  While i would have liked to stay LTS, the risk of having problems doing the stack upgrades is against it for me (since i am a bit of a techno phobe...lol) so, weighing one against the other, i made the move ;)
I very much appreciated your input, however :D

---

