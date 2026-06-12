---
title: "[ubuntu] Can't boot up ubuntu anymore after installing mesa-utils package"
date: 2014-03-31
forum: General Help
---

### Post by FDRmz4Y on 2014-03-31
So my laptop fan was being loud and I tried to fix it by installing mesa-utils:

> sudo apt-get install mesa-utils mesa-utils-extra  

In the installation it told me that some packages will be uninstalled during the installation of this package, and I said yes.

Now, I can't seem to boot up Ubuntu anymore. It boots up to a black screen. In addition after the installation, it seemed like nothing would happen when I pressed the "Shutdown" button under the settings icon in the top right corner.
 
I don't remember exactly what I removed and I also don't know how I can reinstall the packages I removed, since I don't think I have access to a terminal anymore. However, I do have access to a LiveCD, so I think I could use that.

Also, I've been trying to avoid an upgrade to Ubuntu 13.04 (because I think the upgrade will take a while as I KNOW I'm going to run into problems during/after the upgrade), and I need to use a Linux OS for school, but I don't want to cause unnecessary trouble for myself. But now I'm considering that it might be worth it to upgrade because it might help to eliminate some other troubles I might have. Is there any way quick and SAFE way to do this upgrade (12.10 to 13.04), without totally ruining my system?

---

### Post by FDRmz4Y on 2014-03-31
After thinking about this, a possibility of what might have happened is that I actually now have a mesa package which doesn't work with my integrated graphics card. Is there any way I can revert these changes that I have made?

EDIT:
Here is what happened when I tried to install mesa-utils

> Start-Date: 2014-03-30  23:40:43
Commandline: apt-get install mesa-utils mesa-utils-extra
Install: mesa-utils:amd64 (8.0.1+git20110129+d8f7d6b-0ubuntu2), libegl1-mesa-drivers:amd64 (8.0.4-0ubuntu0.7, automatic), libgl1-mesa-dri:amd64 (8.0.4-0ubuntu0.7, automatic), libgl1-mesa-glx:amd64 (8.0.4-0ubuntu0.7, automatic), libglapi-mesa:amd64 (8.0.4-0ubuntu0.7, automatic), libopenvg1-mesa:amd64 (8.0.4-0ubuntu0.7, automatic), libgbm1:amd64 (8.0.4-0ubuntu0.7, automatic), mesa-utils-extra:amd64 (8.0.1+git20110129+d8f7d6b-0ubuntu2), libegl1-mesa:amd64 (8.0.4-0ubuntu0.7, automatic), libwayland0:amd64 (0.85.0-1ubuntu2, automatic), libxcb-xfixes0:amd64 (1.8.1-1ubuntu0.2, automatic), libgles2-mesa:amd64 (8.0.4-0ubuntu0.7, automatic), libllvm3.0:amd64 (3.0-4ubuntu1, automatic)
Remove: libglapi-mesa-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1)
End-Date: 2014-03-30  23:40:58

And maybe some related items:

> Start-Date: 2014-03-30  23:04:09
Commandline: aptdaemon role='role-commit-packages' sender=':1.72'
Install: linux-image-3.5.0-47-generic:amd64 (3.5.0-47.71~precise1), linux-headers-3.5.0-47:amd64 (3.5.0-47.71~precise1), linux-headers-3.5.0-47-generic:amd64 (3.5.0-47.71~precise1)
Upgrade: libsmbclient:amd64 (3.6.3-2ubuntu2.9, 3.6.3-2ubuntu2.10), openssh-server:amd64 (5.9p1-5ubuntu1.1, 5.9p1-5ubuntu1.2), gwibber-service-identica:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), smbclient:amd64 (3.6.3-2ubuntu2.9, 3.6.3-2ubuntu2.10), thunderbird-locale-en-us:amd64 (24.3.0+build2-0ubuntu0.12.04.1, 24.4.0+build1-0ubuntu0.12.04.1), udisks:amd64 (1.0.4-5ubuntu2.1, 1.0.4-5ubuntu2.2), gnome-settings-daemon:amd64 (3.4.2-0ubuntu0.6.4, 3.4.2-0ubuntu0.6.5), libcupsfilters1:amd64 (1.0.18-0ubuntu0.1, 1.0.18-0ubuntu0.2), thunderbird:amd64 (24.3.0+build2-0ubuntu0.12.04.1, 24.4.0+build1-0ubuntu0.12.04.1), libpython2.7:amd64 (2.7.3-0ubuntu3.4, 2.7.3-0ubuntu3.5), firefox-globalmenu:amd64 (27.0.1+build1-0ubuntu0.12.04.1, 28.0+build2-0ubuntu0.12.04.1), gwibber-service-twitter:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), gwibber-service-facebook:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), libwbclient0:amd64 (3.6.3-2ubuntu2.9, 3.6.3-2ubuntu2.10), libfwtsacpica1:amd64 (14.02.00-0ubuntu0~p, 14.03.01-0ubuntu2~p), linux-image-generic-lts-quantal:amd64 (3.5.0.46.52, 3.5.0.47.53), libgnutls26:amd64 (2.12.14-5ubuntu3.6, 2.12.14-5ubuntu3.7), python2.7:amd64 (2.7.3-0ubuntu3.4, 2.7.3-0ubuntu3.5), gir1.2-gtk-3.0:amd64 (3.4.2-0ubuntu0.6, 3.4.2-0ubuntu0.7), update-manager:amd64 (0.156.14.11, 0.156.14.12), librsvg2-common:amd64 (2.36.1-0ubuntu1, 2.36.1-0ubuntu1.1), update-manager-core:amd64 (0.156.14.11, 0.156.14.12), xkb-data:amd64 (2.5-1ubuntu1.3, 2.5-1ubuntu1.5), samba-common:amd64 (3.6.3-2ubuntu2.9, 3.6.3-2ubuntu2.10), linux-headers-generic-lts-quantal:amd64 (3.5.0.46.52, 3.5.0.47.53), libgtk-3-bin:amd64 (3.4.2-0ubuntu0.6, 3.4.2-0ubuntu0.7), firefox:amd64 (27.0.1+build1-0ubuntu0.12.04.1, 28.0+build2-0ubuntu0.12.04.1), openssh-client:amd64 (5.9p1-5ubuntu1.1, 5.9p1-5ubuntu1.2), libgtk-3-0:amd64 (3.4.2-0ubuntu0.6, 3.4.2-0ubuntu0.7), sudo:amd64 (1.8.3p1-1ubuntu3.4, 1.8.3p1-1ubuntu3.6), libgwibber2:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), libfwts1:amd64 (14.02.00-0ubuntu0~p, 14.03.01-0ubuntu2~p), tzdata-java:amd64 (2013g-0ubuntu0.12.04, 2014a-0ubuntu0.12.04), libgail-3-0:amd64 (3.4.2-0ubuntu0.6, 3.4.2-0ubuntu0.7), google-chrome-stable:amd64 (33.0.1750.117-1, 33.0.1750.152-1), firefox-locale-en:amd64 (27.0.1+build1-0ubuntu0.12.04.1, 28.0+build2-0ubuntu0.12.04.1), flashplugin-installer:amd64 (11.2.202.341ubuntu0.12.04.1, 11.2.202.346ubuntu0.12.04.1), initramfs-tools:amd64 (0.99ubuntu13.4, 0.99ubuntu13.5), libdvdnav4:amd64 (4.2.0-1, 4.2.0-1ubuntu0.1), gwibber-service:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), linux-generic-lts-quantal:amd64 (3.5.0.46.52, 3.5.0.47.53), libfwtsiasl1:amd64 (14.02.00-0ubuntu0~p, 14.03.01-0ubuntu2~p), tzdata:amd64 (2013g-0ubuntu0.12.04, 2014a-0ubuntu0.12.04), librsvg2-2:amd64 (2.36.1-0ubuntu1, 2.36.1-0ubuntu1.1), python2.7-minimal:amd64 (2.7.3-0ubuntu3.4, 2.7.3-0ubuntu3.5), thunderbird-globalmenu:amd64 (24.3.0+build2-0ubuntu0.12.04.1, 24.4.0+build1-0ubuntu0.12.04.1), thunderbird-gnome-support:amd64 (24.3.0+build2-0ubuntu0.12.04.1, 24.4.0+build1-0ubuntu0.12.04.1), fwts:amd64 (14.02.00-0ubuntu0~p, 14.03.01-0ubuntu2~p), linux-libc-dev:amd64 (3.2.0-59.90, 3.2.0-60.91), samba-common-bin:amd64 (3.6.3-2ubuntu2.9, 3.6.3-2ubuntu2.10), ssh-askpass-gnome:amd64 (5.9p1-5ubuntu1.1, 5.9p1-5ubuntu1.2), gwibber:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), libssh-4:amd64 (0.5.2-1ubuntu0.12.04.2, 0.5.2-1ubuntu0.12.04.3), libgwibber-gtk2:amd64 (3.4.2-0ubuntu2.3, 3.4.2-0ubuntu2.4), fwts-efi-runtime-dkms:amd64 (14.02.00-0ubuntu0~p, 14.03.01-0ubuntu2~p), initramfs-tools-bin:amd64 (0.99ubuntu13.4, 0.99ubuntu13.5), cups-filters:amd64 (1.0.18-0ubuntu0.1, 1.0.18-0ubuntu0.2), libgtk-3-common:amd64 (3.4.2-0ubuntu0.6, 3.4.2-0ubuntu0.7), ca-certificates:amd64 (20111211, 20130906ubuntu0.12.04.1), thunderbird-locale-en:amd64 (24.3.0+build2-0ubuntu0.12.04.1, 24.4.0+build1-0ubuntu0.12.04.1)

Start-Date: 2014-03-30  23:35:10
Commandline: aptdaemon role='role-commit-packages' sender=':1.72'
Install: xserver-xorg-video-ati:amd64 (6.14.99~git20111219.aacbd629-0ubuntu2, automatic), xserver-xorg-video-openchrome:amd64 (0.2.904+svn1050-1ubuntu0.1, automatic), xserver-xorg-video-mga:amd64 (1.4.13.dfsg-4build2, automatic), xserver-xorg-core:amd64 (1.11.4-0ubuntu10.14, automatic), xserver-xorg-video-mach64:amd64 (6.9.0-1build2, automatic), xserver-xorg-video-trident:amd64 (1.3.4-2build2, automatic), libgl1-mesa-glx:amd64 (8.0.4-0ubuntu0.7, automatic), xserver-xorg-video-sis:amd64 (0.10.3-3build2, automatic), xserver-xorg-video-qxl:amd64 (0.0.16-2ubuntu0.1, automatic), xserver-xorg-video-siliconmotion:amd64 (1.7.5-1build2, automatic), libglapi-mesa:amd64 (8.0.4-0ubuntu0.7, automatic), xserver-xorg-video-savage:amd64 (2.3.3-1ubuntu1, automatic), xserver-xorg-video-tdfx:amd64 (1.4.3-4build2, automatic), xserver-xorg-video-intel:amd64 (2.17.0-1ubuntu4.4, automatic), xserver-xorg-video-r128:amd64 (6.8.1-5build2, automatic), xserver-xorg-input-evdev:amd64 (2.7.0-0ubuntu1.2, automatic), xserver-xorg-video-vesa:amd64 (2.3.0-7build2, automatic), xserver-xorg-video-s3:amd64 (0.6.3-4build2, automatic), xserver-xorg-video-fbdev:amd64 (0.4.2-4ubuntu2, automatic), xserver-xorg-video-nouveau:amd64 (0.0.16+git20111201+b5534a1-1build3, automatic), xserver-xorg-video-neomagic:amd64 (1.2.5-2build2, automatic), libgles2-mesa:amd64 (8.0.4-0ubuntu0.7), xserver-xorg-video-sisusb:amd64 (0.9.4-2build2, automatic), xserver-xorg-video-radeon:amd64 (6.14.99~git20111219.aacbd629-0ubuntu2, automatic), xserver-xorg-video-cirrus:amd64 (1.3.2-4build1, automatic)
Remove: x11-apps:amd64 (7.6+5ubuntu1), ubuntu-desktop:amd64 (1.267.1), xserver-xorg-video-mach64-lts-quantal:amd64 (6.9.3-0ubuntu1~precise2), xserver-xorg-video-trident-lts-quantal:amd64 (1.3.6-0ubuntu2~precise1), xserver-xorg-video-sis-lts-quantal:amd64 (0.10.7-0ubuntu1~precise2), x11-xserver-utils-lts-quantal:amd64 (7.7~3ubuntu1~precise1), xserver-common-lts-quantal:amd64 (1.13.0-0ubuntu6.5~precise1), xserver-xorg-video-modesetting-lts-quantal:amd64 (0.5.0-0ubuntu1~precise2), xserver-xorg-input-synaptics-lts-quantal:amd64 (1.6.2-1ubuntu5~precise1), xserver-xorg-input-evdev-lts-quantal:amd64 (2.7.3-0ubuntu2~precise1), xserver-xorg-video-ati-lts-quantal:amd64 (6.99.99~git20120913.8637f772-0ubuntu1~precise2), libxatracker1-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), libgl1-mesa-glx-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-input-vmmouse-lts-quantal:amd64 (12.9.0-0ubuntu3~precise1), xserver-xorg-video-s3-lts-quantal:amd64 (0.6.5-0ubuntu1~precise1), x11-session-utils:amd64 (7.6+2), xserver-xorg-video-vesa-lts-quantal:amd64 (2.3.2-0ubuntu1~precise1), xserver-xorg-video-tdfx-lts-quantal:amd64 (1.4.5-0ubuntu1~precise2), xserver-xorg-video-fbdev-lts-quantal:amd64 (0.4.3-0ubuntu1~precise1), xserver-xorg-video-nouveau-lts-quantal:amd64 (1.0.2-0ubuntu3~precise2), x11-xfs-utils:amd64 (7.6+1), libglapi-mesa-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-video-mga-lts-quantal:amd64 (1.6.2-0ubuntu1~precise2), xinit:amd64 (1.3.1-1), xserver-xorg-video-sisusb-lts-quantal:amd64 (0.9.6-0ubuntu1~precise1), xserver-xorg-video-vmware-lts-quantal:amd64 (12.0.2+git.e5ac80d8-0ubuntu1~precise2), xserver-xorg-video-neomagic-lts-quantal:amd64 (1.2.7-0ubuntu1~precise1), xserver-xorg-video-radeon-lts-quantal:amd64 (6.99.99~git20120913.8637f772-0ubuntu1~precise2), xserver-xorg-video-openchrome-lts-quantal:amd64 (0.3.1-0ubuntu1~precise3), xserver-xorg-video-cirrus-lts-quantal:amd64 (1.5.1-0ubuntu2~precise1), xserver-xorg-input-wacom-lts-quantal:amd64 (0.17.0-0ubuntu2~precise1), xorg:amd64 (7.6+12ubuntu2), xserver-xorg-input-mouse-lts-quantal:amd64 (1.7.2-2build1~precise1), xserver-xorg-input-all-lts-quantal:amd64 (7.7+1ubuntu4~precise1), xserver-xorg-video-intel-lts-quantal:amd64 (2.20.9-0ubuntu2.3~precise1), xserver-xorg-video-savage-lts-quantal:amd64 (2.3.6-0ubuntu1~precise1), xserver-xorg-video-all-lts-quantal:amd64 (7.7+1ubuntu4~precise1), libgl1-mesa-dri-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-video-siliconmotion-lts-quantal:amd64 (1.7.7-0ubuntu1~precise1), xserver-xorg-lts-quantal:amd64 (7.7+1ubuntu4~precise1), xserver-xorg-core-lts-quantal:amd64 (1.13.0-0ubuntu6.5~precise1), xserver-xorg-video-r128-lts-quantal:amd64 (6.9.1-0ubuntu1~precise2)
End-Date: 2014-03-30  23:36:09

Start-Date: 2014-03-30  23:38:28
Commandline: aptdaemon role='role-commit-packages' sender=':1.72'
Install: libglapi-mesa-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1)
Remove: mesa-utils:amd64 (8.0.1+git20110129+d8f7d6b-0ubuntu2), gnome-power-manager:amd64 (3.4.0-0ubuntu1.1), unity:amd64 (5.20.0-0ubuntu3), unity-2d:amd64 (5.14.0-0ubuntu2), libwxbase2.8-0:amd64 (2.8.12.1-6ubuntu2), gnome-media:amd64 (3.4.0-0ubuntu3.1), nautilus:amd64 (3.4.2-0ubuntu9), compiz-plugins-default:amd64 (0.9.7.12-0ubuntu3), gvfs-fuse:amd64 (1.12.1-0ubuntu1.2), libgnome-desktop-3-2:amd64 (3.4.2-0ubuntu0.2), gnome-session-bin:amd64 (3.2.1-0ubuntu8), x11-utils:amd64 (7.6+4ubuntu0.1), libunity-2d-private0:amd64 (5.14.0-0ubuntu2), nautilus-share:amd64 (0.7.3-1ubuntu2), gvfs-backends:amd64 (1.12.1-0ubuntu1.2), gnome-settings-daemon:amd64 (3.4.2-0ubuntu0.6.5), libnux-2.0-0:amd64 (2.14.1-0ubuntu1), libtinyxml2.6.2:amd64 (2.6.2-1build1), libglew1.6:amd64 (1.6.0-4), gnome-session:amd64 (3.2.1-0ubuntu8), libgl1-mesa-glx:amd64 (8.0.4-0ubuntu0.7), libglapi-mesa:amd64 (8.0.4-0ubuntu0.7), apturl-common:amd64 (0.5.1ubuntu3), libqt4-opengl:amd64 (4.8.1-0ubuntu4.6), unity-2d-spread:amd64 (5.14.0-0ubuntu2), unity-2d-panel:amd64 (5.14.0-0ubuntu2), eog:amd64 (3.4.2-0ubuntu1.1), libwxgtk2.8-0:amd64 (2.8.12.1-6ubuntu2), indicator-power:amd64 (2.0-0ubuntu1), libunity-core-5.0-5:amd64 (5.20.0-0ubuntu3), compiz-gnome:amd64 (0.9.7.12-0ubuntu3), opencpn:amd64 (3.2.2-0~precise1), apturl:amd64 (0.5.1ubuntu3), libgnome-media-profiles-3.0-0:amd64 (3.0.0-1), unity-2d-shell:amd64 (5.14.0-0ubuntu2), nautilus-sendto:amd64 (3.0.1-2ubuntu2), unity-greeter:amd64 (0.2.9-0ubuntu1.2), libvisual-0.4-plugins:amd64 (0.4.0.dfsg.1-7), indicator-session:amd64 (0.3.96-0ubuntu1), gnome-screensaver:amd64 (3.4.1-0ubuntu1), indicator-datetime:amd64 (0.3.94-0ubuntu2), libgles2-mesa:amd64 (8.0.4-0ubuntu0.7), gnome-control-center:amd64 (3.4.2-0ubuntu0.13.1), brasero:amd64 (3.4.1-0ubuntu1.1), nux-tools:amd64 (2.14.1-0ubuntu1), compiz:amd64 (0.9.7.12-0ubuntu3), gvfs:amd64 (1.12.1-0ubuntu1.2), ubuntuone-client-gnome:amd64 (3.0.1-0ubuntu1), compiz-plugins-main-default:amd64 (0.9.7.0~bzr19-0ubuntu10.1), libglu1-mesa:amd64 (8.0.4-0ubuntu0.7), libglewmx1.6:amd64 (1.6.0-4), gvfs-daemons:amd64 (1.12.1-0ubuntu1.2)
End-Date: 2014-03-30  23:39:09

---

### Post by mansonfan78 on 2014-03-31
You could try the "nomodeset" option.  At the grub menu hit "e" to edit configuration and find the line that ends with "quiet splash" and change it to read: quiet splash nomodeset.  This will boot in a default graphics mode.  This isn't permanent, so until you've fixed the problem you'll have to do this every time.
You could also try using the recovery mode from the grub menu and at the next menu select "repair broken packages".  You may have to select the option to enable networking first.

---

### Post by mc4man on 2014-03-31
Assuming that under "And maybe some related items:" are 3 separate, in order  actions on your part (in full?)  & the one at top the last one you seemed to have created quite a mess. There were a number of packages removed that seemingly were never re-installed in any version. You could carefully go thru it all & maybe figure it all  out.
Were you using the unity-greeter?

Was this a 12.04.x install updated to 12.10 at some point? There seemed to be a number of lts-quantal packages removed period   or removed & replaced with quantal versions.

---

### Post by FDRmz4Y on 2014-03-31
@mansonfan78 - I have just tried what you suggested, but it doesn't seem to help.
@mc4man - Yes, I could go through through it, except I don't know how to reinstall those packages when my boot isn't working. I'm not sure what unity greeter is, and no, this was not an install updated to 12.10.

---

### Post by mörgæs on 2014-04-01
13.04 is unspported, so you shouldn't focus on this one. Better to go for a fresh install of 13.10.

---

### Post by mc4man on 2014-04-01
Well unity-greeter is your means to login, it was removed in 23:38:28 along with a bunch of other things like unity, libnux, nautilus, gvfs*, gnome-session, gnome-settings-daemon, ect., ect. 
So putting aside any missing mesa or mismatched mesa libraries you have no chance  of logging in. Also any lts-quantal packages installed/removed, whatever, are for precise (12.04.1), so if this wasn't an upgraded install a bit of a mystery as to why you were installing/removing them.

You could try to get to a tty (ctrl+alt+FX like F1 or F3) or try recovery > fsck > root shell  & install ubuntu-desktop, gnome-session, unity-greeter, gnome-settings-daemon ect.
If that doesn't work or help then  wouldn't waste any more  time, I'd copy out any needed data & do a fresh install of either 12.04, 12.10, 13.10 (12.10 is EOL in a month or so, 13.10 is EOL in 3 months or so.

---

