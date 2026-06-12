---
title: "apt-get autoremove went wild"
date: 2017-05-03
forum: General Help
---

### Post by poidokan on 2017-05-03
hi,

my sytem has been desintegrated by apt-get autoremove. I know it's my fault, but now I want to restore the lost packages.

The problem is that my internet connection is not working anymore. Here is the list of the removed packages from /var/log/apt/history.log:

```
Commandline: apt-get autoremove
Remove: holap:amd64 (0.0+cvs20100618-1kxstudio1.2), syslinux-legacy:amd64 (3.63+dfsg-2ubuntu5), kde-service-menu-audiokonverter:amd64 (5.9.1-1kxstudio1), libtotem-plparser18:amd64 (3.10.2-0ubuntu1), kde-service-menu-kim4:amd64 (0.9.5-1kxstudio1), wavpack:amd64 (4.70.0-1), libchm1:amd64 (0.40a-3), plasma-widgets-addons:amd64 (4.13.3-0ubuntu0.1), libnl-genl-3-200:amd64 (3.2.21-1ubuntu4), tap-plugins:amd64 (0.7.2-1kxstudio1.1), gir1.2-udisks-2.0:amd64 (2.1.3-1ubuntu0.1), obexd-client:amd64 (0.46-1ubuntu7), zam-plugins:amd64 (3.7-1kxstudio1), smplayer:amd64 (0.8.6-2), libautodie-perl:amd64 (2.23-1), libcrypt-passwdmd5-perl:amd64 (1.3-10), kwalletmanager:amd64 (4.13.3-0ubuntu0.1), petri-foo:amd64 (0.1.87-2), libgmime-2.6-0:amd64 (2.6.20-0ubuntu1), python3-markupsafe:amd64 (0.18-1build2), libnetfilter-conntrack3:amd64 (1.0.4-1), ark:amd64 (4.13.3-0ubuntu0.1), libokularcore4:amd64 (4.13.3-0ubuntu0.1), bristol:amd64 (0.60.11-2), libxml-twig-perl:amd64 (3.44-1), libportsmf0:amd64 (0.1~svn20101010-4), seq24:amd64 (0.9.3-1kxstudio1), marble-data:amd64 (4.13.3-0ubuntu0.1), iw:amd64 (3.4-1), libmbim-glib0:amd64 (1.6.0-2ubuntu0.1), libkdcraw23:amd64 (4.13.0-0ubuntu1), libreadline5:amd64 (5.2+dfsg-2), libnet-domain-tld-perl:amd64 (1.70-1), ffado-mixer-qt4:amd64 (2.3.0+svn2652-1~trusty1), python3-numpy:amd64 (1.8.2-0ubuntu0.1), libjansson4:amd64 (2.5-2), libdmapsharing-3.0-2:amd64 (2.9.24-0ubuntu1), libio-string-perl:amd64 (1.08-3), xorg:amd64 (7.7+1ubuntu8.1), libxml++2.6-2:amd64 (2.36.0-2ubuntu1), xinit:amd64 (1.3.2-1), kxstudio-artwork-plymouth:amd64 (20130827-0kxstudio1), libsidplayfp:amd64 (1.2.2-1), bluedevil:amd64 (2.0~rc1really1.3.2-0ubuntu1), libbinio1ldbl:amd64 (1.4+dfsg1-3ubuntu1), x11-session-utils:amd64 (7.7+1), brasero-common:amd64 (3.10.0-0ubuntu1), gir1.2-gst-plugins-base-1.0:amd64 (1.2.4-1~ubuntu2.1), audacity:amd64 (2.0.5-1ubuntu3.2), audacious-plugins:amd64 (3.4.3-2), libshp1:amd64 (1.2.10-7), sndfile-programs:amd64 (1.0.27-1kxstudio2), python-urllib3:amd64 (1.7.1-1ubuntu4), libnetworkmanagerqt1:amd64 (0.9.8.4-0kxstudio1), kde-service-menu-extract-and-compress:amd64 (1.4.4-1kxstudio1), python-qt4:amd64 (4.10.4+dfsg-1ubuntu1), mobile-broadband-provider-info:amd64 (20140317-1), t1utils:amd64 (1.37-2ubuntu1.1), libiw30:amd64 (30~pre9-8ubuntu1), python3-chardet:amd64 (2.2.1-2~ubuntu1), python-pil:amd64 (2.3.0-1ubuntu3.4), python3-debian:amd64 (0.1.21+nmu2ubuntu2), python-notify:amd64 (0.1.1-3ubuntu2), libnet-ip-perl:amd64 (1.26-1), wireless-regdb:amd64 (2013.02.13-1ubuntu1), ffmpegthumbs:amd64 (4.13.3-0ubuntu0.1+ffmpeg1), bristol-data:amd64 (0.60.11-2), okular:amd64 (4.13.3-0ubuntu0.1), libperlio-gzip-perl:amd64 (0.18-1build3), qsampler:amd64 (0.3.1-1kxstudio3), muse:amd64 (2.2.1-2kxstudio2), python-cups:amd64 (1.9.66-0ubuntu2), blop:amd64 (0.2.8-6kxstudio1), kdesudo:amd64 (3.4.2.4+repack-2ubuntu4), python-pexpect:amd64 (3.1-1ubuntu0.1), libqoauth1:amd64 (1.0.1-2ubuntu1), libcue1:amd64 (1.4.0-1), mtools:amd64 (4.0.18-1ubuntu1), libntdb1:amd64 (1.0-2ubuntu1), gdebi-kde:amd64 (0.9.5.3ubuntu2), libclass-accessor-perl:amd64 (0.34-1), liblist-moreutils-perl:amd64 (0.33-1build3), ubuntu-drivers-common:amd64 (0.2.91.12), kde-service-menu-fuseiso:amd64 (0.2-0ubuntu2), kcalc:amd64 (4.13.0-0ubuntu1), python-renderpm:amd64 (3.0-1build1), diffstat:amd64 (1.58-1), stk-rawwaves:amd64 (4.5.0-1kxstudio2), libaudclient2:amd64 (3.4.3-1), libkface2:amd64 (1.0~digikam3.5.0-0ubuntu10), cadence-tools:amd64 (0.8.1+git20170319), gdebi-core:amd64 (0.9.5.3ubuntu2), ingen:amd64 (0.5.2~svn5817), hardening-includes:amd64 (2.5ubuntu2.1), linux-image-3.13.0-58-lowlatency:amd64 (3.13.0-58.97), caps:amd64 (0.9.23-1kxstudio1), catia:amd64 (0.8.1+git20170319), linux-headers-3.13.0-58-lowlatency:amd64 (3.13.0-58.97), gwenview:amd64 (4.13.3-0ubuntu0.1), rar:amd64 (4.2.0-1), gparted:amd64 (0.18.0-1), libprotobuf8:amd64 (2.5.0-9ubuntu1), python-imaging:amd64 (2.3.0-1ubuntu3.4), xsane-common:amd64 (0.998-5ubuntu1), python3-gridfs:amd64 (2.6.3-1build1), libqextserialport1:amd64 (1.2.0~rc1+git7-g3be3fbf-1), kde-touchpad:amd64 (0.0+git20140305-0ubuntu1), libvorbis0a:i386 (1.3.2-1.3ubuntu1), python3-pykde4:amd64 (4.13.3-0ubuntu0.1), python3-pymongo:amd64 (2.6.3-1build1), rhythmbox-data:amd64 (3.0.2-0ubuntu2), xbitmaps:amd64 (1.1.1-2), catarina:amd64 (0.8.1+git20170319), libxcb-record0:amd64 (1.10-2ubuntu1), alsa-tools-gui:amd64 (1.0.27-2ubuntu3), libconfig++9:amd64 (1.4.9-2), ardour4:amd64 (4.7.0-1kxstudio1), python-reportlab-accel:amd64 (3.0-1build1), python3-lilv:amd64 (0.22.1+git20151211-1kxstudio1), okular-extra-backends:amd64 (4.13.3-0ubuntu0.1), libastro1:amd64 (4.13.3-0ubuntu0.1), libunity-scopes-json-def-desktop:amd64 (7.1.4+14.04.20140210-0ubuntu1), python-kde4:amd64 (4.13.3-0ubuntu0.1), libquazip0:amd64 (0.6.2-0ubuntu1), apturl-common:amd64 (0.5.2ubuntu4), ktorrent-data:amd64 (4.3.1-2ubuntu1), libmarblewidget18:amd64 (4.13.3-0ubuntu0.1), libbaloowidgets4:amd64 (4.13.3-0ubuntu0.1), libkface-data:amd64 (1.0~digikam3.5.0-0ubuntu10), libnet-dns-perl:amd64 (0.68-1.2build1), python-reportlab:amd64 (3.0-1build1), kuser:amd64 (4.13.0-0ubuntu1), python3.4-lilv:amd64 (0.22.1+git20151211-1kxstudio1), dpf-plugins:amd64 (20160309), rubberband-ladspa:amd64 (1.8.2+git20161227-1kxstudio1), kate:amd64 (4.13.3-0ubuntu0.1), digikam:amd64 (3.5.0-0ubuntu10), a2jmidid:amd64 (8~dfsg0-1), wine-mono0.0.8:amd64 (0.0.8-0ubuntu1), pptp-linux:amd64 (1.7.2-7), libsndfile1:i386 (1.0.25-7ubuntu2.1), unace:amd64 (1.2b-10+deb7u1build0.14.04.1), python3-defer:amd64 (1.0.6-2build1), libunity-protocol-private0:amd64 (7.1.4+14.04.20140210-0ubuntu1), libfftw3-long3:amd64 (3.3.3-7ubuntu3), libipc-system-simple-perl:amd64 (1.25-2), libdbus-c++-1-0:amd64 (0.9.0-6ubuntu1), flac:amd64 (1.3.1-1kxstudio2), iputils-arping:amd64 (20121221-4ubuntu1.1), plasma-nm:amd64 (0.9.3.6-0kxstudio1), apturl-kde:amd64 (0.5.2ubuntu4), libqtlocation1:amd64 (1.2.0-3ubuntu5), librtmidi1:amd64 (2.0.1~ds0-3ubuntu1), python3-whoosh:amd64 (2.5.7-2~kxstudio1), usb-creator-common:amd64 (0.2.56.3ubuntu0.1), libpgf6:amd64 (6.12.24+ds1-2), print-manager:amd64 (4.13.3-0ubuntu0.1), libkipi-data:amd64 (4.13.0-0ubuntu1), linux-headers-3.13.0-58:amd64 (3.13.0-58.97), smplayer-themes:amd64 (0.1.20+dfsg-1), libmm-glib0:amd64 (1.0.0-2ubuntu1.1), python3-xkit:amd64 (0.5.0ubuntu2), libkgeomap-data:amd64 (1.0~digikam3.5.0-0ubuntu10), libemail-valid-perl:amd64 (1.192-1), libnm-util2:amd64 (0.9.8.8-0ubuntu7.3), non-sequencer:amd64 (1.9.3+git20120426-1kxstudio1.1), ffado-dbus-server:amd64 (2.3.0+svn2652-1~trusty1), syslinux:amd64 (4.05+dfsg-6+deb8u1), acpid:amd64 (2.0.21-1ubuntu2), wine-gecko2.21:amd64 (2.21-0ubuntu1), wine-gecko2.21:i386 (2.21-0ubuntu1), lmms-common:amd64 (1.1.3-3kxstudio1), kamera:amd64 (4.13.3-0ubuntu0.1), mudita24:amd64 (1.0.3+svn13-4), plasma-desktopthemes-artwork:amd64 (4.13.3-0ubuntu0.1), qmidiarp:amd64 (0.6.3-1kxstudio1), libburn4:amd64 (1.3.4-0ubuntu1), libsigc++-1.2-5c2:amd64 (1.2.7-2ubuntu1), libqt4-webkit:amd64 (4.8.5+git192-g085f851+dfsg-2ubuntu4.1), python-sip:amd64 (4.15.5-1build1), mixxx:amd64 (1.11.0-git3885-ppa0~trusty2), clementine:amd64 (1.2.3~trusty), libnm-glib-vpn1:amd64 (0.9.8.8-0ubuntu7.3), audacity-data:amd64 (2.0.5-1ubuntu3.2), libmnl0:amd64 (1.0.3-3ubuntu1), libsub-name-perl:amd64 (0.05-1build4), lintian:amd64 (2.5.22ubuntu1), libaudcore1:amd64 (3.4.3-1), smplayer-translations:amd64 (0.8.6-2), libspectre1:amd64 (0.2.7-2ubuntu1.2), libfftw3-3:amd64 (3.3.3-7ubuntu3), ksystemlog:amd64 (4.13.0-0ubuntu1), xsane:amd64 (0.998-5ubuntu1), libmodemmanagerqt1:amd64 (1.0.1-0ubuntu2), liboath0:amd64 (2.0.2-2ubuntu2), dnsmasq-base:amd64 (2.68-1ubuntu0.1), libapt-pkg-perl:amd64 (0.1.29build1), kubuntu-driver-manager:amd64 (14.04ubuntu10), libjte1:amd64 (1.19-2), projectm-data:amd64 (2.1.0+dfsg-1build2), libvamp-hostsdk3:amd64 (2.5+repack0-2), usb-modeswitch-data:amd64 (20140327-1), libkateinterfaces4:amd64 (4.13.3-0ubuntu0.1), plasma-dataengines-addons:amd64 (4.13.3-0ubuntu0.1), syslinux-common:amd64 (4.05+dfsg-6+deb8u1), libqmi-glib0:amd64 (1.4.0-1), midisnoop:amd64 (0.1.2~repack0-2), rosegarden:amd64 (16.02-1kxstudio1), python3-pymongo-ext:amd64 (2.6.3-1build1), audacious-plugins-data:amd64 (3.4.3-2), python3-bson:amd64 (2.6.3-1build1), dolphin:amd64 (4.13.3-0ubuntu0.1), libbluedevil1:amd64 (2.0~rc1really1.9.4-0ubuntu1), modemmanager:amd64 (1.0.0-2ubuntu1.1), aptdaemon:amd64 (1.1.1-1ubuntu5.2), libsub-identify-perl:amd64 (0.04-1build3), amsynth:amd64 (1.6.4-1kxstudio1), phasex:amd64 (0.12.0+m1-6kxstudio1), libwlocate0:amd64 (0.0git20130108-0ubuntu1), librubberband2:amd64 (1.8.1-4), faac:amd64 (1.28-6), faad:amd64 (2.7-8), libipc-run-perl:amd64 (0.92-1), usb-creator-kde:amd64 (0.2.56.3ubuntu0.1), gir1.2-gnomekeyring-1.0:amd64 (3.8.0-2), libisofs6:amd64 (1.3.4-0ubuntu1), libxml-xpathengine-perl:amd64 (0.13-1), crda:amd64 (1.1.2-1ubuntu2), giada:amd64 (0.11.2-1kxstudio1), marble-plugins:amd64 (4.13.3-0ubuntu0.1), libarchive-zip-perl:amd64 (1.30-7), python-requests:amd64 (2.2.1-1ubuntu0.3), colibri:amd64 (0.3.0-2ubuntu1), wpasupplicant:amd64 (2.1-0ubuntu1.4), ffado-tools:amd64 (2.3.0+svn2652-1~trusty1), patchutils:amd64 (0.3.2-3), python3-aptdaemon:amd64 (1.1.1-1ubuntu5.2), linux-image-3.13.0-110-lowlatency:amd64 (3.13.0-110.157), libffado2:amd64 (2.3.0+svn2652-1~trusty1), libtie-ixhash-perl:amd64 (1.23-1), digikam-data:amd64 (3.5.0-0ubuntu10), kde-notification-colibri:amd64 (0.3.0-2ubuntu1), libkdcraw-data:amd64 (4.13.0-0ubuntu1), usb-modeswitch:amd64 (2.1.1+repack0-1ubuntu1), libunity9:amd64 (7.1.4+14.04.20140210-0ubuntu1), libopenconnect2:amd64 (5.02-1), software-properties-kde:amd64 (0.92.37.7), linux-headers-3.13.0-110-lowlatency:amd64 (3.13.0-110.157), fuseiso:amd64 (20070708-3+deb7u1ubuntu14.04.1), ktorrent:amd64 (4.3.1-2ubuntu1), libio-pty-perl:amd64 (1.08-1build4), libmowgli2:amd64 (1.0.0-1ubuntu1), kscreen:amd64 (1.0.2.1-0ubuntu1), libsbsms10:amd64 (2.0.1-1), gir1.2-gstreamer-1.0:amd64 (1.2.4-0ubuntu1.1), libraw9:amd64 (0.15.4-1), suil-libs:amd64 (0.8.7+git20170321-1kxstudio1), sooperlooper:amd64 (1.7.0~dfsg0-2), system-config-printer-udev:amd64 (1.4.3+20140219-0ubuntu2.6), konversation-data:amd64 (1.5-1ubuntu1.14.04.1), kcolorchooser:amd64 (4.13.0-0ubuntu1), libprojectm2:amd64 (2.1.0+dfsg-1build2), libkipi11:amd64 (4.13.0-0ubuntu1), python-cupshelpers:amd64 (1.4.3+20140219-0ubuntu2.6), audacious:amd64 (3.4.3-1), libguess1:amd64 (1.1-4), libdebconf-kde0:amd64 (0.3-1), libbrasero-media3-1:amd64 (3.10.0-0ubuntu1), libtext-levenshtein-perl:amd64 (0.06~01-2), lmms:amd64 (1.1.3-3kxstudio1), python3-mako:amd64 (0.9.1-1), qtractor:amd64 (0.8.1-1kxstudio1), libkgeomap1:amd64 (1.0~digikam3.5.0-0ubuntu10), linux-headers-3.13.0-110:amd64 (3.13.0-110.157), network-manager:amd64 (0.9.8.8-0ubuntu7.3), libfltk1.1:amd64 (1.1.10-17), helm:amd64 (0.8.6-1kxstudio2), pinentry-qt4:amd64 (0.8.3-1ubuntu1), kde-config-gtk-style:amd64 (2.2.1-1fakesync1), libwrap0:i386 (7.6.q-25), qsynth:amd64 (0.3.8-1), kmix:amd64 (4.13.3-0ubuntu0.1+kxstudio1), gir1.2-rb-3.0:amd64 (3.0.2-0ubuntu2), ksnapshot:amd64 (4.13.0-0ubuntu1), x11-xfs-utils:amd64 (7.7+1), librhythmbox-core8:amd64 (3.0.2-0ubuntu2), konversation:amd64 (1.5-1ubuntu1.14.04.1), network-manager-pptp:amd64 (0.9.8.2-1ubuntu2), plymouth-label:amd64 (0.8.8-0ubuntu17.1), cadence-data:amd64 (0.8.1+git20170319), libprotobuf-lite8:amd64 (2.5.0-9ubuntu1), python-ntdb:amd64 (1.0-2ubuntu1), python3-bson-ext:amd64 (2.6.3-1build1), yakuake:amd64 (2.9.9-1), libspeechd2:amd64 (0.8-5ubuntu1), libvorbisenc2:i386 (1.3.2-1.3ubuntu1), libkexiv2-data:amd64 (4.13.0-0ubuntu1), libfs6:amd64 (1.0.5-1), libkexiv2-11:amd64 (4.13.0-0ubuntu1), x11-apps:amd64 (7.7+2), libnm-glib4:amd64 (0.9.8.8-0ubuntu7.3), libparse-debianchangelog-perl:amd64 (1.2.0-1ubuntu1), libkscreen1:amd64 (1.0.5-0ubuntu1~ubuntu14.04)
```

Which packages do I need to reinstall to repair the network? How do I install them without network?

Thaks a lot for any help.

---

### Post by ajgreeny on 2017-05-03
Why do you know it's your fault?
What did you do apart from running the autoremove command?

---

### Post by poidokan on 2017-05-03
Actually I'm just used being guilty when it comes to computers. I guess I mixed things up by installing some packages with Syanptic and some from the terminal. Anyway, if I had not confirmed the removal (although I was suspicious about the long list of "packages not needed") my system would be still ok.

---

### Post by deadflowr on 2017-05-03
> **ajgreeny said:**
> Why do you know it's your fault?
What did you do apart from running the autoremove command?

It' could be the simple caveat to running autoremove.
Being that if at one time you installed a package which also brought in another package and then removed the original package you installed.
Apt still considers those other packages only to be required by that original package.
And so it deems them unneeded anymore, even if those other packages are still wanted.
From man apt:
>  autoremove (apt-get(8))
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed as dependencies changed or the package(s) needing
           them were removed in the meantime.

           You should check that the list does not include applications you
           have grown to like even though they were once installed just as a
           dependency of another package. You can mark such a package as
           manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for
           automatic removal.
if that make sense.

---

### Post by ajgreeny on 2017-05-03
It shouldn't matter whether you used terminal or synaptic to install packages, but so that we can understand a bit more, what have you installed and then subsequently removed?

Autoremove is a command that many of us use regularly to keep junk out of the system, for example unneeded kernels that have been installed in normal updating.

---

### Post by monkeybrain20122 on 2017-05-03
If you use synaptic (muon for kde?? I haven't used kubuntu for a long time but I remembered kde came with its own package managing gui which was as good as synaptic) after you removed a package check the side panel (status) If there are autoremovable packages they will show up in a section called autoremovable(or autoremove) When you installed a package x other packages y and z may be installed as dependencies. When you remove x, y and z are "no longer needed" so they would become autoremovable. But sometimes y and z are actually important packages on their own, so in that case you would either reinstall x, or remove y and z and then reinstall them (so that they are no longer "auto-removable" since the second time around they were not installed as something else's dependencies) 

Since kde has very tight dependency structure, it could be that you have removed some apparently unimportant package but it has a ton of things listed as its dependencies. So always check the autoremovable section (if it shows up) whenever you uninstall stuffs. Running "autoremove" or using something like bleachbit can be dangerous if you don't know exactly what are being removed (so if you use bleachbit, check the preview first)

---

### Post by poidokan on 2017-05-03
The last thing I installed was wine. Shortly after that I had no sound working anymore. I tried to reinstall pulseaudio with syanptic, but it failed and I got a message of broken packages. I'm not aware of what I could have removed. On the other side I never used autoremove up to now.

My hope was on
```
sudo dkpg -i kubuntu-driver-manager_14.04ubuntu7_amd64.deb
sudo dkpg -i ubuntu-drivers-common_0.2.91.12_amd64.deb
```
but I still don't know how to get the network work again.

---

### Post by oldos2er on 2017-05-03
What is the output of ```
lsb_release -a
``` ? Do you recall if you ever removed kubuntu-desktop?

---

### Post by poidokan on 2017-05-04
it says "no lsb modules are available"

As  far as I kno I did not remove Kubuntu-Desktop. On purpose at least...

---

