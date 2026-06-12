---
title: "autoremove"
date: 2014-10-23
forum: General Help
---

### Post by unitedworld2k12 on 2014-10-23
Dear friends i was uninstalling wine from my  xubuntu14.04 after that i used the command autoremove and now after logging in i find completely dramatic changes have been taken place on my computer and am in xfce mode and my google chrome browser is gone even.


Here is the log history i am copying and pasting it for your reference ...please help me out..


```
apt-get purge wine*
Purge: gconf-service:i386 (3.2.6-0ubuntu2), inkscape:i386 (0.48.4-3ubuntu2), xubuntu-default-settings:i386 (14.04.5), pidgin-libnotify:i386 (0.14-9ubuntu2), python-ldb:i386 (1.1.16-1), python-pycurl:i386 (7.19.3-0ubuntu3), abiword-plugin-mathview:i386 (3.0.0-4ubuntu1.1), python3-pycurl:i386 (7.19.3-0ubuntu3), libldb1:i386 (1.1.16-1), gstreamer0.10-plugins-bad:i386 (0.10.23-7.2ubuntu1), pidgin:i386 (2.10.9-0ubuntu3.1), gtk-theme-config:i386 (1.0-1), libgnomevfs2-common:i386 (2.24.4-1ubuntu6), software-properties-gtk:i386 (0.92.37.1), libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), chromium-browser-l10n:i386 (37.0.2062.120-0ubuntu0.14.04.1~pkg1049), chromium-browser:i386 (37.0.2062.120-0ubuntu0.14.04.1~pkg1049), libabiword-3.0:i386 (3.0.0-4ubuntu1.1), libcurl3:i386 (7.35.0-1ubuntu2.1), python3-software-properties:i386 (0.92.37.1), kerneloops-daemon:i386 (0.12+git20090217-3ubuntu8), libraptor2-0:i386 (2.0.13-1), samba:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), samba-common-bin:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), winbind:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), wine-gecko2.21:i386 (2.21-0ubuntu1), xchat-common:i386 (2.8.8-7.1ubuntu5), wine-mono0.0.8:i386 (0.0.8-0ubuntu1), libgnomevfs2-0:i386 (2.24.4-1ubuntu6), libgnomevfs2-extra:i386 (2.24.4-1ubuntu6), xchat-indicator:i386 (0.3.11-0ubuntu4), python-samba:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), system-config-printer-udev:i386 (1.4.3+20140219-0ubuntu2.2), libkdc2-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), samba-vfs-modules:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), librdf0:i386 (1.0.17-1), samba-dsdb-modules:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), libsmbclient:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), libhdb9-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), wine1.6-i386:i386 (1.6.2-0ubuntu4), libslv2-9:i386 (0.6.6+dfsg1-2), libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8), network-manager-gnome:i386 (0.9.8.8-0ubuntu4.3), gconf-service-backend:i386 (3.2.6-0ubuntu2), winetricks:i386 (0.0+20140302-0ubuntu2), libcurl3-gnutls:i386 (7.35.0-1ubuntu2.1), system-config-printer-common:i386 (1.4.3+20140219-0ubuntu2.2), vlc-plugin-notify:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1), abiword:i386 (3.0.0-4ubuntu1.1), samba-libs:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), python-cupshelpers:i386 (1.4.3+20140219-0ubuntu2.2), libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), xubuntu-desktop:i386 (2.180), whoopsie:i386 (0.2.24.6), smbclient:i386 (4.1.6+dfsg-1ubuntu2.14.04.3), vlc:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1), wine1.6:i386 (1.6.2-0ubuntu4), libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), system-config-printer-gnome:i386 (1.4.3+20140219-0ubuntu2.2), gconf2:i386 (3.2.6-0ubuntu2), python-smbc:i386 (1.0.14.1-0ubuntu2), software-properties-common:i386 (0.92.37.1), software-center:i386 (13.10-0ubuntu4.1), pepperflashplugin-nonfree:i386 (1.3ubuntu1), flashplugin-installer:i386 (11.2.202.411ubuntu0.14.04.1), vlc-plugin-pulse:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1), librasqal3:i386 (0.9.32-1), xchat:i386 (2.8.8-7.1ubuntu5), gvfs-backends:i386 (1.20.1-1ubuntu1), libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), abiword-plugin-grammar:i386 (3.0.0-4ubuntu1.1), gstreamer1.0-plugins-bad:i386 (1.2.4-1~ubuntu1), libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1), apt-transport-https:i386 (1.0.1ubuntu2.5), python-gconf:i386 (2.28.1+dfsg-1ubuntu2), vlc-nox:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1)
End-Date: 2014-10-23  17:36:34

Start-Date: 2014-10-23  17:37:35
Commandline: apt-get autoremove
Remove: libopenal1:i386 (1.14-4ubuntu1), libgstreamer-plugins-bad1.0-0:i386 (1.2.4-1~ubuntu1), liblua5.2-0:i386 (5.2.3-1), tsconf:i386 (1.0-12), libtar0:i386 (1.2.20-3ubuntu0.1), libspandsp2:i386 (0.0.6~pre21-2), liblivemedia23:i386 (2014.01.13-1), libopencv-contrib2.4:i386 (2.4.8+dfsg1-2ubuntu1), libva-x11-1:i386 (1.3.0-2), libzvbi0:i386 (0.2.35-2), libbluray1:i386 (0.5.0-1), libzvbi-common:i386 (0.2.35-2), libenca0:i386 (1.15-2), libxcb-randr0:i386 (1.10-2ubuntu1), libwildmidi1:i386 (0.2.3.4-2.1ubuntu3), libgtkglext1:i386 (1.2.0-3.1fakesync3), unixodbc:i386 (2.2.14p2-5ubuntu5), libdca0:i386 (0.0.5-6ubuntu1), libproxy-tools:i386 (0.4.11-0ubuntu4), libmpg123-0:i386 (1.16.0-1ubuntu1), libopencv-objdetect2.4:i386 (2.4.8+dfsg1-2ubuntu1), libopencv-core2.4:i386 (2.4.8+dfsg1-2ubuntu1), libodbc1:i386 (2.2.14p2-5ubuntu5), libflite1:i386 (1.4-release-8), libdvbpsi8:i386 (1.0.0-3), libbasicusageenvironment0:i386 (2014.01.13-1), libfaad2:i386 (2.7-8), libopencv-calib3d2.4:i386 (2.4.8+dfsg1-2ubuntu1), p7zip:i386 (9.20.1~dfsg.1-4), libofa0:i386 (0.9.3-5ubuntu1), libssh2-1:i386 (1.4.3-2), libosmesa6:i386 (10.1.3-0ubuntu0.1), fonts-wqy-microhei:i386 (0.2.0-beta-2), libvlc5:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1), libdirectfb-1.2-9:i386 (1.2.10.0-5), libmagick++5:i386 (6.7.7.10-6ubuntu3), ocl-icd-libopencl1:i386 (2.1.3-4), libaacs0:i386 (0.7.0-1), libgroupsock1:i386 (2014.01.13-1), libdc1394-22:i386 (2.2.1-2ubuntu2), libopencv-legacy2.4:i386 (2.4.8+dfsg1-2ubuntu1), libkate1:i386 (0.4.1-1ubuntu1), tdb-tools:i386 (1.2.12-1), libcdaudio1:i386 (0.99.12p2-13), libfreerdp1:i386 (1.0.2-2ubuntu1), libpostproc52:i386 (0.git20120821-4), libhogweed2:i386 (2.7.1-1), libvo-aacenc0:i386 (0.1.3-1), odbcinst1debian2:i386 (2.2.14p2-5ubuntu5), libsidplay2:i386 (2.1.1-14), libmms0:i386 (0.6.2-3ubuntu2), icoutils:i386 (0.31.0-2), libts-0.0-0:i386 (1.0-12), libtbb2:i386 (4.2~20130725-1.1ubuntu1), libopenal-data:i386 (1.14-4ubuntu1), libopencv-ml2.4:i386 (2.4.8+dfsg1-2ubuntu1), libopencv-features2d2.4:i386 (2.4.8+dfsg1-2ubuntu1), libwildmidi-config:i386 (0.2.3.4-2.1ubuntu3), libgnutls28:i386 (3.2.11-2ubuntu1), libopencv-video2.4:i386 (2.4.8+dfsg1-2ubuntu1), perlmagick:i386 (6.7.7.10-6ubuntu3), libxcb-keysyms1:i386 (0.3.9-1ubuntu1), libaio1:i386 (0.3.109-4), gstreamer1.0-plugins-bad-videoparsers:i386 (1.2.4-1~ubuntu1), libresid-builder0c2a:i386 (2.1.1-14), liblircclient0:i386 (0.9.0-0ubuntu5), libsbc1:i386 (1.1-2ubuntu2), libopencv-imgproc2.4:i386 (2.4.8+dfsg1-2ubuntu1), libvcdinfo0:i386 (0.7.24+dfsg-0.1ubuntu2), libmatroska6:i386 (1.4.1-2), ttf-wqy-microhei:i386 (0.2.0-beta-2), libgc1c2:i386 (7.2d-5ubuntu2), libupnp6:i386 (1.6.17-1.2), libass4:i386 (0.10.1-3ubuntu1), libgstreamer-plugins-bad0.10-0:i386 (0.10.23-7.2ubuntu1), libgsl0ldbl:i386 (1.16+dfsg-1ubuntu1), libusageenvironment1:i386 (2014.01.13-1), libopencv-highgui2.4:i386 (2.4.8+dfsg1-2ubuntu1), libgif4:i386 (4.1.6-11), libmimic0:i386 (1.0.4-2.1ubuntu1), libcapi20-3:i386 (3.25+dfsg1-3.3ubuntu2), libxcb-xv0:i386 (1.10-2ubuntu1), libebml4:i386 (1.3.0-2), gstreamer1.0-plugins-bad-faad:i386 (1.2.4-1~ubuntu1), python-dnspython:i386 (1.11.1-1build1), libcddb2:i386 (1.3.2-4fakesync2), gnome-exe-thumbnailer:i386 (0.9.3-0ubuntu1), libswscale2:i386 (9.16-0ubuntu0.14.04.1), libzbar0:i386 (0.10+doc-9build1), libopencv-flann2.4:i386 (2.4.8+dfsg1-2ubuntu1), libdirac-encoder0:i386 (1.0.2-6ubuntu1), libiso9660-8:i386 (0.83-4.1ubuntu1), libvlccore7:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1), libvo-amrwbenc0:i386 (0.1.3-1), libmpcdec6:i386 (0.1~r459-1ubuntu3), libmodplug1:i386 (0.8.8.4-4.1), odbcinst:i386 (2.2.14p2-5ubuntu5), attr:i386 (2.4.47-1ubuntu1), libxcb-composite0:i386 (1.10-2ubuntu1), libcrystalhd3:i386 (0.0~git20110715.fdd2f19-9ubuntu1), fonts-horai-umefont:i386 (460-1), libgme0:i386 (0.5.5-2), libsrtp0:i386 (1.4.5~20130609~dfsg-1), vlc-data:i386 (2.1.4+git20141006+r54582+19+11~ubuntu14.04.1)
End-Date: 2014-10-23  17:38:49
```

---

### Post by /ADM on 2014-10-23
You told the computer to remove wine and 'everything' to do with that package.  Then you ran autoremove which removes packages that are not needed anymore.  Which obviously, removed a lot important packages.

run sudo apt-get install xubuntu-desktop.  It will calculate dependencies again and re-install all the ones it is missing.

---

### Post by ian-weisser on 2014-10-23
Autoremove is not psychic. It doesn't know your intent.
It only does what you told it to do.

It only knows what you (using apt) have marked as eligible/ineligible for autoremoval.
It *does* list the packages for you and give you the option to abort.

Honestly, 'purge wine*' is a rather unwise command.
The * leads to unexpected -for the user- behavior. As you experienced, and has already been discussed.
Purge is not a force-remove command (good thing for you that it's not). It simply means to remove settings files in /etc in addition to the package.

Instead, I would have suggested  [FONT=courier new]sudo apt-get autoremove wine[/FONT]

---

### Post by oldos2er on 2014-10-23
Support request moved to General Help.

---

### Post by unitedworld2k12 on 2014-10-23
Thanks it helps for now and gradually i will get to install all those accidentally un installed things..

---

### Post by unitedworld2k12 on 2014-10-23
Thanks.

---

### Post by unitedworld2k12 on 2014-10-23
> **ian-weisser said:**
> Autoremove is not psychic. It doesn't know your intent.
It only does what you told it to do.

It only knows what you (using apt) have marked as eligible/ineligible for autoremoval.
It *does* list the packages for you and give you the option to abort.

Honestly, 'purge wine*' is a rather unwise command.
The * leads to unexpected -for the user- behavior. As you experienced, and has already been discussed.
Purge is not a force-remove command (good thing for you that it's not). It simply means to remove settings files in /etc in addition to the package.

Instead, I would have suggested  [FONT=courier new]sudo apt-get autoremove wine[/FONT]

yeah i just learned a great deal today.

---

