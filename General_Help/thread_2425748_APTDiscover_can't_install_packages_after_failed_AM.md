---
title: "APT/Discover can't install packages after failed AMDGPU"
date: 2019-08-29
forum: General Help
---

### Post by Johnius on 2019-08-29
Hello,

I've managed to find myself in a bit of a pickle after trying to install AMDGPU drivers on 19.04.  The install failed at the final package, but the dependent packages are still installed and I can't figure out how to uninstall them.  Every apt command returns these results:

```
The following packages have unmet dependencies:
 amdgpu-dkms : Depends: amdgpu-core but it is not going to be installed
 amdgpu-lib : Depends: amdgpu-core (= 19.20-812932) but it is not going to be installed
 glamor-amdgpu : Depends: amdgpu-core but it is not going to be installed
 gst-omx-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm-amdgpu-common : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu:i386 : Depends: amdgpu-core:i386
 libegl1-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libegl1-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libgbm1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libgbm1-amdgpu:i386 : Depends: amdgpu-core:i386
 libgl1-amdgpu-mesa-dri : Depends: amdgpu-core but it is not going to be installed
                          Recommends: libtxc-dxtn-s2tc0 but it is not installable or
                                      libtxc-dxtn0 but it is not installable
 libgl1-amdgpu-mesa-dri:i386 : Depends: amdgpu-core:i386
                               Recommends: libtxc-dxtn-s2tc0:i386 but it is not installable or
                                           libtxc-dxtn0:i386 but it is not installable
 libglapi-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libglapi-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libllvm7.1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libllvm7.1-amdgpu:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-client0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-client0:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-egl1 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-egl1:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-server0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-server0:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-va-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-va-drivers:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-vdpau-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-vdpau-drivers:i386 : Depends: amdgpu-core:i386
 xserver-xorg-amdgpu-video-amdgpu : Depends: amdgpu-core but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Discover keeps trying to install AMDGPU when I upgrade any packages.

Thanks.

---

### Post by cruzer001 on 2019-08-29
> Every apt command returns these results
Too vague

autoremove?
-f install?

---

### Post by QIII on 2019-08-29
Hello!

AMDGPU is used by the installer if the hardware is supported.  Otherwise, Radeon is used.  There should be no reason to install AMDGPU, unless you are talking about AMDGPU-PRO, which is the proprietary overlay of AMDGPU.

How did you attempt to install AMDGPU?

What are your hardware specs?

With that information, we can start to figure out what to do.

---

### Post by Johnius on 2019-08-29
both of those, trying to remove or purge individual packages listed, --fix-broken.  Help, update, edit-sources all work.  It appears any install/removal of packages causes the error.

---

### Post by TheFu on 2019-08-29
No idea what "Discover" is, but if you manually install .deb files, those will often break dependency validation in a few months. That leads to the issue like above.

My fix when this happens is to *remove all the manually installed .deb files*, get the system fully patched again, then find newer versions (with newer dependencies) from the site.

Over the years, I've learned a few things about Ubuntu package management. In order of preference:
[LIST=1]
[*]Use Canonical repos whenever possible.
[*]Use trusted, reputable, maintained PPAs
[*]Use .deb from trusted, reputable, maintained team, knowing that manually updating is required every month
[*]Use source code, manually recompiling, updating monthly is required
[/LIST]

GPU drivers often have special instructions for installation and maintenance.  With 18.04 and other LTS releases, I thought installation for all tested GPU drivers was built-into the "Additional Drivers" tool.

---

### Post by Johnius on 2019-08-29
> **QIII said:**
> 

How did you attempt to install AMDGPU?

What are your hardware specs?



I used the tutorial from the AMD website ([https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)), not realizing it only works on a specific version.  Radeon HD 7870 with a FX-8150 on Gigabyte 990FX-UD3.  I managed to get the computer working again, I just have package problems now.

---

### Post by Johnius on 2019-08-29
> **TheFu said:**
> 
My fix when this happens is to *remove all the manually installed .deb files*, get the system fully patched again, then find newer versions (with newer dependencies) from the site.


This is what I'm having trouble doing.

---

### Post by cruzer001 on 2019-08-29
```
amdgpu-uninstall
```
Is that the code you originally used?

---

### Post by Johnius on 2019-08-29
> **cruzer001 said:**
> ```
amdgpu-uninstall
```
Is that the code you originally used?

Tried, but since the install failed that script was never written.

---

### Post by deadflowr on 2019-08-29
Look at what amdgpu packages are currently in flux and/or installed
```
dpkg -l | grep amdgpu | awk '{print $1,$2}'
```
post the output.

---

### Post by Johnius on 2019-08-29
```
dpkg -l | grep amdgpu | awk '{print $1,$2}'
iU amdgpu
iU amdgpu-dkms
iU amdgpu-lib
iU amdgpu-lib32
ii amdgpu-pro-pin
iU glamor-amdgpu:amd64
iU gst-omx-amdgpu
iU libdrm-amdgpu-amdgpu1:amd64
iU libdrm-amdgpu-amdgpu1:i386
iU libdrm-amdgpu-common
ii libdrm-amdgpu1:amd64
ii libdrm-amdgpu1:i386
iU libdrm2-amdgpu:amd64
iU libdrm2-amdgpu:i386
iU libegl1-amdgpu-mesa:amd64
iU libegl1-amdgpu-mesa:i386
iU libegl1-amdgpu-mesa-drivers:amd64
iU libegl1-amdgpu-mesa-drivers:i386
iU libgbm1-amdgpu:amd64
iU libgbm1-amdgpu:i386
iU libgl1-amdgpu-mesa-dri:amd64
iU libgl1-amdgpu-mesa-dri:i386
iU libgl1-amdgpu-mesa-glx:amd64
iU libgl1-amdgpu-mesa-glx:i386
iU libglapi-amdgpu-mesa:amd64
iU libglapi-amdgpu-mesa:i386
iU libgles1-amdgpu-mesa:amd64
iU libgles1-amdgpu-mesa:i386
iU libgles2-amdgpu-mesa:amd64
iU libgles2-amdgpu-mesa:i386
iU libllvm7.1-amdgpu:amd64
iU libllvm7.1-amdgpu:i386
iU libosmesa6-amdgpu:amd64
iU libosmesa6-amdgpu:i386
iU libwayland-amdgpu-client0:amd64
iU libwayland-amdgpu-client0:i386
iU libwayland-amdgpu-egl1:amd64
iU libwayland-amdgpu-egl1:i386
iU libwayland-amdgpu-server0:amd64
iU libwayland-amdgpu-server0:i386
iU libxatracker2-amdgpu:amd64
iU libxatracker2-amdgpu:i386
iU mesa-amdgpu-omx-drivers:amd64
iU mesa-amdgpu-va-drivers:amd64
iU mesa-amdgpu-va-drivers:i386
iU mesa-amdgpu-vdpau-drivers:amd64
iU mesa-amdgpu-vdpau-drivers:i386
iU xserver-xorg-amdgpu-video-amdgpu
ii xserver-xorg-video-amdgpu

```

---

### Post by deadflowr on 2019-08-29
Ubuntu only with two of those packages
libdrm-amdgpu1
xserver-xorg-video-amdgpu

Perhaps try isolating th iU outputs and pipe that through xargs like
```
dpkg -l | awk '/^iU/{print $2}' | xargs sudo dpkg --remove --force-remove-reinstreq   --dry-run
```
If it looks good try running wthout the --dry-run
```
dpkg -l | awk '/^iU/{print $2}' | xargs sudo dpkg --remove --force-remove-reinstreq 
```

---

### Post by Johnius on 2019-08-29
Not sure what argument to add to get only the packages I want gone.  cut/paste of the first command looks like it's preparing to delete the entire OS and errors out.

```
dpkg: error processing package libkf5bookmarks5:amd64 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libkf5calendarevents5:amd64:
 plasma-workspace depends on libkf5calendarevents5; however:
  Package libkf5calendarevents5:amd64 is to be removed.
 plasma-calendar-addons depends on libkf5calendarevents5; however:
  Package libkf5calendarevents5:amd64 is to be removed.
 kdepim-addons depends on libkf5calendarevents5; however:
  Package libkf5calendarevents5:amd64 is to be removed.dpkg: error processing package libkf5calendarevents5:amd64 (--remove):
 dependency problems - not removing
dpkg: too many errors, stopping
Errors were encountered while processing:
 baloo-kf5
 breeze-icon-theme
 cups
 cups-client
 cups-common
 cups-core-drivers
 cups-daemon
 cups-ipp-utils
 cups-ppdc
 cups-server-common
 dpkg-dev
 firefox
 frameworkintegration
 ghostscript
 ghostscript-x
 google-chrome-stable
 kded5
 kdoctools5
 kinit
 kio
 kpackagetool5
 kross
 ktexteditor-katepart
 libblockdev-fs2:amd64
 libblockdev-loop2:amd64
 libblockdev-part-err2:amd64
 libblockdev-part2:amd64
 libblockdev-swap2:amd64
 libblockdev-utils2:amd64
 libblockdev2:amd64
 libcups2:amd64
 libcupsimage2:amd64
 libdpkg-perl
 libegl-mesa0:amd64
 libgbm1:amd64
 libgl1-mesa-dri:amd64
 libglapi-mesa:amd64
 libglx-mesa0:amd64
 libgs9:amd64
 libgs9-common
 libkf5activities5:amd64
 libkf5activitiesstats1:amd64
 libkf5archive5:amd64
 libkf5attica5:amd64
 libkf5auth5:amd64
 libkf5authcore5:amd64
 libkf5baloo5
 libkf5balooengine5
 libkf5bluezqt6:amd64
 libkf5bookmarks5:amd64
 libkf5calendarevents5:amd64
Processing was halted because there were too many errors.

```

---

### Post by deadflowr on 2019-08-29
What does
```
dpkg -l | awk '/^iU/{print $1,$2}'
```
show?

I'm going on the premise that the listed packages from post #11 were the only problem packages.
If there are more you might need to try to remove the packages listed in post #11 individually,
keeping only the two packages I mentioned in post #12
(keep
libdrm-amdgpu1
xserver-xorg-video-amdgpu
)

---

### Post by Johnius on 2019-08-29
Looks like basically every package I have installed.

```

dpkg -l | awk '/^iU/{print $1,$2}'
iU amdgpu
iU amdgpu-dkms
iU amdgpu-lib
iU amdgpu-lib32
iU baloo-kf5
iU breeze-icon-theme
iU chromium-codecs-ffmpeg-extra
iU cups
iU cups-bsd
iU cups-client
iU cups-common
iU cups-core-drivers
iU cups-daemon
iU cups-ipp-utils
iU cups-ppdc
iU cups-server-common
iU deborphan
iU dialog
iU dpkg-dev
iU faad
iU ffmpeg
iU firefox
iU firefox-locale-en
iU flac
iU fluid-soundfont-gm
iU fonts-opensymbol
iU frameworkintegration
iU ghostscript
iU ghostscript-x
iU glamor-amdgpu:amd64
iU google-chrome-stable
iU gst-omx-amdgpu
iU gtkorphan
iU kactivities-bin
iU kded5
iU kdoctools5
iU kimageformat-plugins
iU kinit
iU kio
iU kpackagelauncherqml
iU kpackagetool5
iU kross
iU ktexteditor-data
iU ktexteditor-katepart
iU kwayland-data
iU libavdevice58:amd64
iU libavresample4:amd64
iU libblockdev-crypto2:amd64
iU libblockdev-fs2:amd64
iU libblockdev-loop2:amd64
iU libblockdev-part-err2:amd64
iU libblockdev-part2:amd64
iU libblockdev-swap2:amd64
iU libblockdev-utils2:amd64
iU libblockdev2:amd64
iU libcairo-perl
iU libcephfs2
iU libcups2:amd64
iU libcupsimage2:amd64
iU libdirectfb-1.7-7:amd64
iU libdpkg-perl
iU libdrm-amdgpu-amdgpu1:amd64
iU libdrm-amdgpu-amdgpu1:i386
iU libdrm-amdgpu-common
iU libdrm2-amdgpu:amd64
iU libdrm2-amdgpu:i386
iU libegl-mesa0:amd64
iU libegl1-amdgpu-mesa:amd64
iU libegl1-amdgpu-mesa:i386
iU libegl1-amdgpu-mesa-drivers:amd64
iU libegl1-amdgpu-mesa-drivers:i386
iU libegl1-mesa:amd64
iU libenca0:amd64
iU libgbm1:amd64
iU libgbm1-amdgpu:amd64
iU libgbm1-amdgpu:i386
iU libgif7:amd64
iU libgl1-amdgpu-mesa-dri:amd64
iU libgl1-amdgpu-mesa-dri:i386
iU libgl1-amdgpu-mesa-glx:amd64
iU libgl1-amdgpu-mesa-glx:i386
iU libgl1-mesa-dri:amd64
iU libglade2-0:amd64
iU libglapi-amdgpu-mesa:amd64
iU libglapi-amdgpu-mesa:i386
iU libglapi-mesa:amd64
iU libgles1-amdgpu-mesa:amd64
iU libgles1-amdgpu-mesa:i386
iU libgles2-amdgpu-mesa:amd64
iU libgles2-amdgpu-mesa:i386
iU libglib-perl
iU libglx-mesa0:amd64
iU libgs9:amd64
iU libgs9-common
iU libgtk2-gladexml-perl
iU libgtk2-perl
iU libkf5activities5:amd64
iU libkf5activitiesstats1:amd64
iU libkf5archive5:amd64
iU libkf5attica5:amd64
iU libkf5auth-data
iU libkf5auth5:amd64
iU libkf5authcore5:amd64
iU libkf5baloo5
iU libkf5balooengine5
iU libkf5bluezqt-data
iU libkf5bluezqt6:amd64
iU libkf5bookmarks-data
iU libkf5bookmarks5:amd64
iU libkf5calendarevents5:amd64
iU libkf5codecs-data
iU libkf5codecs5:amd64
iU libkf5completion-data
iU libkf5completion5:amd64
iU libkf5config-bin
iU libkf5config-data
iU libkf5configcore5:amd64
iU libkf5configgui5:amd64
iU libkf5configwidgets-data
iU libkf5configwidgets5:amd64
iU libkf5coreaddons-data
iU libkf5coreaddons5:amd64
iU libkf5crash5:amd64
iU libkf5dbusaddons-bin
iU libkf5dbusaddons-data
iU libkf5dbusaddons5:amd64
iU libkf5declarative-data
iU libkf5declarative5:amd64
iU libkf5dnssd-data
iU libkf5dnssd5:amd64
iU libkf5doctools5:amd64
iU libkf5emoticons-bin
iU libkf5emoticons-data
iU libkf5emoticons5:amd64
iU libkf5filemetadata-bin:amd64
iU libkf5filemetadata-data
iU libkf5filemetadata3:amd64
iU libkf5globalaccel-bin
iU libkf5globalaccel-data
iU libkf5globalaccel5:amd64
iU libkf5globalaccelprivate5:amd64
iU libkf5guiaddons5:amd64
iU libkf5holidays-data
iU libkf5holidays5:amd64
iU libkf5i18n-data
iU libkf5i18n5:amd64
iU libkf5iconthemes-bin
iU libkf5iconthemes-data
iU libkf5iconthemes5:amd64
iU libkf5idletime5:amd64
iU libkf5itemmodels5:amd64
iU libkf5itemviews-data
iU libkf5itemviews5:amd64
iU libkf5jobwidgets-data
iU libkf5jobwidgets5:amd64
iU libkf5js5:amd64
iU libkf5jsapi5:amd64
iU libkf5jsembed-data
iU libkf5jsembed5:amd64
iU libkf5kcmutils-data
iU libkf5kcmutils5:amd64
iU libkf5kdelibs4support-data
iU libkf5kdelibs4support5:amd64
iU libkf5kdelibs4support5-bin
iU libkf5khtml-bin
iU libkf5khtml-data
iU libkf5khtml5:amd64
iU libkf5kiocore5:amd64
iU libkf5kiofilewidgets5:amd64
iU libkf5kiogui5:amd64
iU libkf5kiontlm5:amd64
iU libkf5kiowidgets5:amd64
iU libkf5kirigami2-5
iU libkf5krosscore5:amd64
iU libkf5krossui5:amd64
iU libkf5modemmanagerqt6:amd64
iU libkf5networkmanagerqt6
iU libkf5newstuff-data
iU libkf5newstuff5:amd64
iU libkf5newstuffcore5:amd64
iU libkf5notifications-data
iU libkf5notifications5:amd64
iU libkf5notifyconfig-data
iU libkf5notifyconfig5:amd64
iU libkf5package-data
iU libkf5package5:amd64
iU libkf5parts-data
iU libkf5parts-plugins
iU libkf5parts5:amd64
iU libkf5people-data
iU libkf5people5:amd64
iU libkf5peoplebackend5:amd64
iU libkf5peoplewidgets5:amd64
iU libkf5plasma5:amd64
iU libkf5plasmaquick5:amd64
iU libkf5plotting5:amd64
iU libkf5prison5:amd64
iU libkf5pty-data
iU libkf5pty5:amd64
iU libkf5purpose-bin:amd64
iU libkf5purpose5:amd64
iU libkf5quickaddons5:amd64
iU libkf5runner5:amd64
iU libkf5service-bin
iU libkf5service-data
iU libkf5service5:amd64
iU libkf5solid5:amd64
iU libkf5solid5-data
iU libkf5sonnet5-data
iU libkf5sonnetcore5:amd64
iU libkf5sonnetui5:amd64
iU libkf5style5:amd64
iU libkf5su-bin
iU libkf5su-data
iU libkf5su5:amd64
iU libkf5syndication5abi1:amd64
iU libkf5syntaxhighlighting-data
iU libkf5syntaxhighlighting5
iU libkf5texteditor-bin
iU libkf5texteditor5:amd64
iU libkf5texteditor5-libjs-underscore
iU libkf5textwidgets-data
iU libkf5textwidgets5:amd64
iU libkf5threadweaver5:amd64
iU libkf5unitconversion-data
iU libkf5unitconversion5:amd64
iU libkf5wallet-bin
iU libkf5wallet-data
iU libkf5wallet5:amd64
iU libkf5waylandclient5:amd64
iU libkf5waylandserver5:amd64
iU libkf5webkit5:amd64
iU libkf5widgetsaddons-data
iU libkf5widgetsaddons5:amd64
iU libkf5windowsystem-data
iU libkf5windowsystem5:amd64
iU libkf5xmlgui-bin
iU libkf5xmlgui-data
iU libkf5xmlgui5:amd64
iU libkf5xmlrpcclient-data
iU libkf5xmlrpcclient5:amd64
iU libkwalletbackend5-5:amd64
iU libldap-2.4-2:amd64
iU libldap-common
iU libllvm7.1-amdgpu:amd64
iU libllvm7.1-amdgpu:i386
iU libnss-systemd:amd64
iU libosmesa6-amdgpu:amd64
iU libosmesa6-amdgpu:i386
iU libpam-systemd:amd64
iU libpango-perl
iU libpoppler-glib8:amd64
iU libpoppler-qt5-1:amd64
iU libpoppler85:amd64
iU libprocps7:amd64
iU librados2
iU libreoffice-avmedia-backend-gstreamer
iU libreoffice-base-core
iU libreoffice-calc
iU libreoffice-common
iU libreoffice-core
iU libreoffice-draw
iU libreoffice-help-en-us
iU libreoffice-impress
iU libreoffice-kde5
iU libreoffice-math
iU libreoffice-qt5
iU libreoffice-style-breeze
iU libreoffice-style-colibre
iU libreoffice-style-tango
iU libreoffice-writer
iU libudev1:i386
iU libvorbisidec1
iU libwayland-amdgpu-client0:amd64
iU libwayland-amdgpu-client0:i386
iU libwayland-amdgpu-egl1:amd64
iU libwayland-amdgpu-egl1:i386
iU libwayland-amdgpu-server0:amd64
iU libwayland-amdgpu-server0:i386
iU libxatracker2:amd64
iU libxatracker2-amdgpu:amd64
iU libxatracker2-amdgpu:i386
iU libxcb-res0:amd64
iU linux-generic
iU linux-headers-5.0.0-25
iU linux-headers-5.0.0-25-generic
iU linux-headers-generic
iU linux-image-5.0.0-25-generic
iU linux-image-generic
iU linux-libc-dev:amd64
iU linux-modules-5.0.0-25-generic
iU linux-modules-extra-5.0.0-25-generic
iU menu
iU mesa-amdgpu-omx-drivers:amd64
iU mesa-amdgpu-va-drivers:amd64
iU mesa-amdgpu-va-drivers:i386
iU mesa-amdgpu-vdpau-drivers:amd64
iU mesa-amdgpu-vdpau-drivers:i386
iU mesa-va-drivers:amd64
iU mesa-vdpau-drivers:amd64
iU mesa-vdpau-drivers:i386
iU mesa-vulkan-drivers:amd64
iU mplayer
iU mppenc
iU plasma-framework
iU poppler-utils
iU procps
iU python3-uno
iU qml-module-org-kde-activities:amd64
iU qml-module-org-kde-bluezqt:amd64
iU qml-module-org-kde-draganddrop:amd64
iU qml-module-org-kde-kcm:amd64
iU qml-module-org-kde-kconfig:amd64
iU qml-module-org-kde-kcoreaddons:amd64
iU qml-module-org-kde-kholidays:amd64
iU qml-module-org-kde-kio:amd64
iU qml-module-org-kde-kirigami2
iU qml-module-org-kde-kquickcontrols:amd64
iU qml-module-org-kde-kquickcontrolsaddons:amd64
iU qml-module-org-kde-kwindowsystem:amd64
iU qml-module-org-kde-newstuff
iU qml-module-org-kde-purpose:amd64
iU qml-module-org-kde-qqc2desktopstyle
iU qml-module-org-kde-runnermodel
iU qml-module-org-kde-solid:amd64
iU sonnet-plugins
iU soundkonverter
iU speex
iU systemd-sysv
iU timidity
iU udev
iU uno-libs3
iU ure
iU vorbis-tools
iU vorbisgain
iU wavpack
iU wpasupplicant
iU xserver-xorg-amdgpu-video-amdgpu

```

---

### Post by cruzer001 on 2019-08-29
"dependency problems"

When it comes to dependencies I have ran into times where apt/dpkg just can't get the job done.  Do you by any chance have aptitude installed?  Aptitude handles depends better that apt.

---

### Post by Johnius on 2019-08-29
I don't have aptitude installed.  I tried to install it, but got the original error.

---

### Post by TheFu on 2019-08-29
I've had the aptitude not installed, but needed problem before.  It is smarter about solving dependency issues, but I've only needed it for times with 1 issue, not 50 half-installed packages.  Add it to your list of software to be installed on every new system. 

Whenever an issue like this happens that takes more than 4 hrs to solve, that's when I wipe, and reinstall from backups made prior to the issue.  Takes about 30-45 min to have my machine back just like it was ... from last night or last week or 7 weeks ago or 87 days ago, thanks to good, versioned, automatic, backups.
I didn't always have backup religion, but after a few issues and 1 got-hacked problem, I got it.

---

### Post by Johnius on 2019-08-30
Yeah, I was probably going to revert to LTS later this weekend.  I keep all my data on a separate hard drive just for this reason.  I was hoping I could learn something through this other than "when things go wrong, nuke it."

---

### Post by TheFu on 2019-08-30
All I can say is to review post #5 above for installation prioritization and patch weekly.
At the first problem with APT, fix it. Don't wait.

---

### Post by Johnius on 2019-09-04
Removed the amdgpu-pro-local source repository from Discovery -> Sources.

---

