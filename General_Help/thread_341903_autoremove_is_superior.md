---
title: "autoremove is superior"
date: 2007-01-19
forum: General Help
---

### Post by Anonii on 2007-01-19
Hay there!

I just got a nice "error" (?) in APT. It basicaly asks me to remove many essential things because they are not needed anymore.

```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bluez-passkey-gnome f-spot libgnomecupsui1.0-1c2a libopenobex-1.0-0 tomboy
  evolution-webcal ekiga edgy-community-wallpapers gimp-print
  ttf-devanagari-fonts gcalctool pnm2ppa gthumb gnome-nettool cdparanoia
  xfonts-scalable openoffice.org-impress ubuntu-docs ttf-punjabi-fonts
  linux-headers-generic wvdial xsane ttf-indic-fonts libdjvulibre15
  tangerine-icon-theme openoffice.org-draw python-apport-utils ttf-thai-tlwg
  libgnome-mag2 ttf-kochi-mincho doc-base brltty-x11 gucharmap
  edgy-session-splashes zenity libbtctl4 avahi-daemon gnome-games
  hwdb-client-gnome xscreensaver-gl gdebi vnc-common evolution-exchange
  ttf-mgopen openoffice.org-gtk fortunes-min libwvstreams4.2-base esound
  resilience-theme ttf-kannada-fonts ttf-gentium human-cursors-theme gnome-mag
  gnome-screensaver rhythmbox gedit bluez-cups dbus-1-utils readahead hpijs
  brltty ubuntu-artwork screen hplip dc gnome-themes python-virtkey
  ubuntu-sounds whois libpt-plugins-v4l2 scim-modules-socket powernowd scim
  update-notifier fortune-mod apport edgy-gdm-themes libgpod0 libscim8c2a
  ttf-lao usplash-theme-ubuntu libmdbtools ttf-kochi-gothic festlex-cmu
  libnss-mdns libpoppler1-glib foomatic-db-hpijs xfonts-75dpi
  scim-gtk2-immodule guile-1.6-libs gedit-common industrialtango-theme
  libgutenprintui2-1 librecode0 human-theme gnome-btdownload bluez-utils
  libxevie1 diveintopython ttf-gujarati-fonts xvncviewer hwdb-client-common
  gnome-volume-manager openoffice.org-evolution gtk2-engines libpt-plugins-v4l
  openoffice.org-math gdb edgy-wallpapers eog gdm screensaver-default-images
  xfonts-base gtk2-engines-ubuntulooks libdbus-1-cil ttf-telugu-fonts
  gnome-spell bug-buddy ttf-tamil-fonts libbrlapi1 libgutenprint2 bittorrent
  language-selector openoffice.org festlex-poslex at-spi tsclient rdesktop
  vino gnome-keyring-manager cupsys-driver-gutenprint firefox-gnome-support
  human-icon-theme python-problem-report evince ttf-arphic-uming
  libqthreads-12 libbluetooth2 gnome-games-data festvox-kallpc16k fping
  ttf-malayalam-fonts landscape-client contact-lookup-applet xfonts-100dpi
  xcursor-themes libgnomevfs2-bin gray-theme human-gtk-theme gimp
  libgnome-speech3 outdoors-theme foo2zjs xsane-common ttf-arphic-ukai
  libgimp2.0 libwvstreams4.2-extras libdaemon0 zip libpt-plugins-alsa
  libxplc0.3.13 language-selector-common ttf-oriya-fonts hal-device-manager
  onboard slocate gstreamer0.10-plugins-base-apps libsnmp-base xorg festival
  ttf-baekmuk rss-glx libopal-2.2.0 libhsqldb-java linux-headers-2.6.17-10
  libsnmp9 gconf-editor gnome-system-tools libgnomebt0 ttf-arabeyes
  libuniconf4.2 libservlet2.3-java openoffice.org-base hotkey-setup
  legacyhuman-theme totem gnome-accessibility-themes openoffice.org-calc
  ttf-bengali-fonts gimp-data min12xxw libpt-1.10.0 libguile-ltdl-1
  libestools1.2 silicon-theme libavahi-core4 gstreamer0.10-tools
  xscreensaver-data hpijs-ppds bluez-pin example-content gimp-python
  file-roller serpentine usplash nautilus-sendto gnome-cups-manager
  ssh-askpass-gnome linux-headers-2.6.17-10-generic sound-juicer hplip-data
  lftp
The following packages will be REMOVED:
  apport at-spi avahi-daemon bittorrent bluez-cups bluez-passkey-gnome
  bluez-pin bluez-utils brltty brltty-x11 bug-buddy cdparanoia
  contact-lookup-applet cupsys-driver-gutenprint dbus-1-utils dc
  diveintopython doc-base edgy-community-wallpapers edgy-gdm-themes
  edgy-session-splashes edgy-wallpapers ekiga eog esound evince
  evolution-exchange evolution-webcal example-content f-spot festival
  festlex-cmu festlex-poslex festvox-kallpc16k file-roller
  firefox-gnome-support foo2zjs foomatic-db-hpijs fortune-mod fortunes-min
  fping gcalctool gconf-editor gdb gdebi gdm gedit gedit-common gimp gimp-data
  gimp-print gimp-python gnome-accessibility-themes gnome-btdownload
  gnome-cups-manager gnome-games gnome-games-data gnome-keyring-manager
  gnome-mag gnome-nettool gnome-screensaver gnome-spell gnome-system-tools
  gnome-themes gnome-volume-manager gray-theme gstreamer0.10-plugins-base-apps
  gstreamer0.10-tools gthumb gtk2-engines gtk2-engines-ubuntulooks gucharmap
  guile-1.6-libs hal-device-manager hotkey-setup hpijs hpijs-ppds hplip
  hplip-data human-cursors-theme human-gtk-theme human-icon-theme human-theme
  hwdb-client-common hwdb-client-gnome industrialtango-theme landscape-client
  language-selector language-selector-common legacyhuman-theme lftp
  libavahi-core4 libbluetooth2 libbrlapi1 libbtctl4 libdaemon0 libdbus-1-cil
  libdjvulibre15 libestools1.2 libgimp2.0 libgnome-mag2 libgnome-speech3
  libgnomebt0 libgnomecupsui1.0-1c2a libgnomevfs2-bin libgpod0 libguile-ltdl-1
  libgutenprint2 libgutenprintui2-1 libhsqldb-java libmdbtools libnss-mdns
  libopal-2.2.0 libopenobex-1.0-0 libpoppler1-glib libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12
  librecode0 libscim8c2a libservlet2.3-java libsnmp-base libsnmp9
  libuniconf4.2 libwvstreams4.2-base libwvstreams4.2-extras libxevie1
  libxplc0.3.13 linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic min12xxw nautilus-sendto onboard openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-draw
  openoffice.org-evolution openoffice.org-gtk openoffice.org-impress
  openoffice.org-math outdoors-theme pnm2ppa powernowd python-apport-utils
  python-problem-report python-virtkey rdesktop readahead resilience-theme
  rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket screen
  screensaver-default-images serpentine silicon-theme slocate sound-juicer
  ssh-askpass-gnome tangerine-icon-theme tomboy totem tsclient ttf-arabeyes
  ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts
  ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ubuntu-artwork ubuntu-docs
  ubuntu-sounds update-notifier usplash usplash-theme-ubuntu vino vnc-common
  whois wvdial xcursor-themes xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-scalable xorg xsane xsane-common xscreensaver-data xscreensaver-gl
  xvncviewer zenity zip
0 upgraded, 0 newly installed, 212 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 634MB disk space will be freed.
Do you want to continue [Y/n]? 

```

So, what do I do now?

---

### Post by Lord Illidan on 2007-01-19
What did you do prior to this step?

---

### Post by Anonii on 2007-01-19
I think I removed totem-firefox.

Here are the lines  I found in dpkg.log, for today:

```
2007-01-19 07:22:03 status installed beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 remove beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status half-configured beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status half-installed beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status config-files beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status config-files beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status config-files beryl-settings-bindings 0.1.5+svn20070113-r2643+3v1ubuntu3
2007-01-19 07:22:13 status not-installed beryl-settings-bindings <none>
2007-01-19 07:22:13 status installed libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 remove libegroupwise1.2-dev 1.8.1-0ubuntu3 1.8.1-0ubuntu3
2007-01-19 07:22:13 status half-configured libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status half-installed libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libegroupwise1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status not-installed libegroupwise1.2-dev <none>
2007-01-19 07:22:13 status installed libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 remove libexchange-storage1.2-dev 1.8.1-0ubuntu3 1.8.1-0ubuntu3
2007-01-19 07:22:13 status half-configured libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status half-installed libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status config-files libexchange-storage1.2-dev 1.8.1-0ubuntu3
2007-01-19 07:22:13 status not-installed libexchange-storage1.2-dev <none>
2007-01-19 07:22:13 status installed python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 remove python-all 2.4.3-11ubuntu3 2.4.3-11ubuntu3
2007-01-19 07:22:13 status half-configured python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 status half-installed python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 status config-files python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 status config-files python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 status config-files python-all 2.4.3-11ubuntu3
2007-01-19 07:22:13 status not-installed python-all <none>
2007-01-19 07:22:13 status installed python2.5 2.5-2ubuntu2
2007-01-19 07:22:13 remove python2.5 2.5-2ubuntu2 2.5-2ubuntu2
2007-01-19 07:22:13 status half-configured python2.5 2.5-2ubuntu2
2007-01-19 07:22:14 status half-installed python2.5 2.5-2ubuntu2
2007-01-19 07:22:19 status config-files python2.5 2.5-2ubuntu2
2007-01-19 07:22:19 status config-files python2.5 2.5-2ubuntu2
2007-01-19 07:22:19 status installed python2.5-minimal 2.5-2ubuntu2
2007-01-19 07:22:19 remove python2.5-minimal 2.5-2ubuntu2 2.5-2ubuntu2
2007-01-19 07:22:19 status half-configured python2.5-minimal 2.5-2ubuntu2
2007-01-19 07:22:22 status half-installed python2.5-minimal 2.5-2ubuntu2
2007-01-19 07:22:22 status config-files python2.5-minimal 2.5-2ubuntu2
2007-01-19 07:22:22 status config-files python2.5-minimal 2.5-2ubuntu2
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:28 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:29 status installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:45 remove totem-gstreamer 2.16.2-0ubuntu1 2.16.2-0ubuntu1
2007-01-19 15:11:45 status half-configured totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:11:53 status half-installed totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:12:01 status config-files totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:12:01 status config-files totem-gstreamer 2.16.2-0ubuntu1
2007-01-19 15:12:02 install faac <none> 1.24clean-0ubuntu4
2007-01-19 15:12:02 status half-installed faac 1.24clean-0ubuntu4
2007-01-19 15:12:02 status unpacked faac 1.24clean-0ubuntu4
2007-01-19 15:12:02 status unpacked faac 1.24clean-0ubuntu4
2007-01-19 15:12:02 install faad <none> 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:02 status half-installed faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:02 status unpacked faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:02 status unpacked faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:02 install ffmpeg <none> 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:02 status half-installed ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:02 status unpacked ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:02 status unpacked ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:02 install gstreamer0.10-fluendo-mp3 <none> 0.10.2.debian-1
2007-01-19 15:12:02 status half-installed gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:02 status unpacked gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:02 status unpacked gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:02 install gstreamer0.10-fluendo-mpegdemux <none> 0.10.4-0ubuntu1
2007-01-19 15:12:02 status half-installed gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:02 install gstreamer0.10-gl <none> 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:02 status half-installed gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:02 install gstreamer0.10-gnonlin <none> 0.10.5-1ubuntu1
2007-01-19 15:12:02 status half-installed gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:02 status unpacked gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:02 install gstreamer0.10-plugins-bad-multiverse <none> 0.10.3+cvs20060918-1
2007-01-19 15:12:02 status half-installed gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:02 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:02 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:02 install gstreamer0.10-plugins-ugly-multiverse <none> 0.10.4-2
2007-01-19 15:12:02 status half-installed gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:02 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:02 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:03 install gstreamer0.10-sdl <none> 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:03 status half-installed gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:03 status unpacked gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:03 status unpacked gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:03 install lame <none> 3.96.1-2
2007-01-19 15:12:03 status half-installed lame 3.96.1-2
2007-01-19 15:12:03 status unpacked lame 3.96.1-2
2007-01-19 15:12:03 status unpacked lame 3.96.1-2
2007-01-19 15:12:03 install libcurl3-gnutls <none> 7.15.4-1ubuntu2
2007-01-19 15:12:03 status half-installed libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:03 status unpacked libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:03 status unpacked libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:03 install libmjpegtools0c2a <none> 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status half-installed libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status unpacked libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status unpacked libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 install liboggflac3 <none> 1.1.2-5ubuntu1
2007-01-19 15:12:03 status half-installed liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:03 status unpacked liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:03 status unpacked liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:03 install libxine-extracodecs <none> 1.1.2-0ubuntu2
2007-01-19 15:12:03 status half-installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:03 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:03 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:03 install mjpegtools <none> 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status half-installed mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status unpacked mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 status unpacked mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:03 install mpg321 <none> 0.2.10.3
2007-01-19 15:12:03 status half-installed mpg321 0.2.10.3
2007-01-19 15:12:04 status unpacked mpg321 0.2.10.3
2007-01-19 15:12:04 status unpacked mpg321 0.2.10.3
2007-01-19 15:12:04 install totem-xine <none> 2.16.2-0ubuntu1
2007-01-19 15:12:04 status half-installed totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:04 status unpacked totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:04 status unpacked totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:04 install vorbis-tools <none> 1.1.1-5
2007-01-19 15:12:04 status half-installed vorbis-tools 1.1.1-5
2007-01-19 15:12:04 status unpacked vorbis-tools 1.1.1-5
2007-01-19 15:12:04 status unpacked vorbis-tools 1.1.1-5
2007-01-19 15:12:04 status unpacked faac 1.24clean-0ubuntu4
2007-01-19 15:12:04 status half-configured faac 1.24clean-0ubuntu4
2007-01-19 15:12:04 status installed faac 1.24clean-0ubuntu4
2007-01-19 15:12:04 status unpacked faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:04 status half-configured faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:04 status installed faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-01-19 15:12:04 status unpacked ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:04 status unpacked ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:04 status half-configured ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:04 status installed ffmpeg 3:0.cvs20060823-3.1ubuntu1
2007-01-19 15:12:04 status unpacked gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:04 status half-configured gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:04 status installed gstreamer0.10-fluendo-mp3 0.10.2.debian-1
2007-01-19 15:12:04 status unpacked gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:04 status half-configured gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:04 status installed gstreamer0.10-fluendo-mpegdemux 0.10.4-0ubuntu1
2007-01-19 15:12:05 status unpacked gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status half-configured gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status installed gstreamer0.10-gl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status unpacked gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:05 status half-configured gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:05 status installed gstreamer0.10-gnonlin 0.10.5-1ubuntu1
2007-01-19 15:12:05 status unpacked gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:05 status half-configured gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:05 status installed gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
2007-01-19 15:12:05 status unpacked gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:05 status half-configured gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:05 status installed gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
2007-01-19 15:12:05 status unpacked gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status half-configured gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status installed gstreamer0.10-sdl 0.10.3+cvs20060918-0ubuntu1
2007-01-19 15:12:05 status unpacked lame 3.96.1-2
2007-01-19 15:12:05 status half-configured lame 3.96.1-2
2007-01-19 15:12:07 status installed lame 3.96.1-2
2007-01-19 15:12:07 status unpacked libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:07 status half-configured libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:07 status installed libcurl3-gnutls 7.15.4-1ubuntu2
2007-01-19 15:12:07 status unpacked libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status half-configured libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status installed libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status unpacked liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:07 status half-configured liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:07 status installed liboggflac3 1.1.2-5ubuntu1
2007-01-19 15:12:07 status unpacked libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:07 status half-configured libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:07 status installed libxine-extracodecs 1.1.2-0ubuntu2
2007-01-19 15:12:07 status unpacked mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status half-configured mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status installed mjpegtools 1:1.8.0-0.2ubuntu2
2007-01-19 15:12:07 status unpacked mpg321 0.2.10.3
2007-01-19 15:12:07 status half-configured mpg321 0.2.10.3
2007-01-19 15:12:08 status installed mpg321 0.2.10.3
2007-01-19 15:12:08 status unpacked totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:08 status half-configured totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:12 status installed totem-xine 2.16.2-0ubuntu1
2007-01-19 15:12:14 status unpacked vorbis-tools 1.1.1-5
2007-01-19 15:12:14 status half-configured vorbis-tools 1.1.1-5
2007-01-19 15:12:14 status installed vorbis-tools 1.1.1-5
2007-01-19 15:12:24 install libdivx0-binary <none> 6.1.1-1duo1
2007-01-19 15:12:24 status half-installed libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:24 status unpacked libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:24 status unpacked libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:24 status unpacked libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:24 status half-configured libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:24 status installed libdivx0-binary 6.1.1-1duo1
2007-01-19 15:12:28 install libdivxdecore0-binary <none> 5.0.5-1duo1
2007-01-19 15:12:28 status half-installed libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:28 status unpacked libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:28 status unpacked libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:28 status unpacked libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:28 status half-configured libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:28 status installed libdivxdecore0-binary 5.0.5-1duo1
2007-01-19 15:12:33 install libdivxencore0-binary <none> 5.0.5-1duo1
2007-01-19 15:12:33 status half-installed libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:12:34 status unpacked libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:12:34 status unpacked libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:12:34 status unpacked libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:12:34 status half-configured libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:12:34 status installed libdivxencore0-binary 5.0.5-1duo1
2007-01-19 15:20:36 upgrade w32codecs 20060611-1plf1 1:20061022-0.0
2007-01-19 15:20:36 status half-configured w32codecs 20060611-1plf1
2007-01-19 15:20:36 status unpacked w32codecs 20060611-1plf1
2007-01-19 15:20:36 status half-installed w32codecs 20060611-1plf1
2007-01-19 15:20:36 status unpacked w32codecs 20060611-1plf1
2007-01-19 15:20:36 status installed w32codecs 20060611-1plf1
2007-01-19 15:20:39 install libdvdcss2 <none> 1.2.9-0.0
2007-01-19 15:20:39 status half-installed libdvdcss2 1.2.9-0.0
2007-01-19 15:20:39 status unpacked libdvdcss2 1.2.9-0.0
2007-01-19 15:20:39 status unpacked libdvdcss2 1.2.9-0.0
2007-01-19 15:20:39 status unpacked libdvdcss2 1.2.9-0.0
2007-01-19 15:20:39 status half-configured libdvdcss2 1.2.9-0.0
2007-01-19 15:20:40 status installed libdvdcss2 1.2.9-0.0
2007-01-19 15:20:45 install libdvdplay0 <none> 1.0.1-7
2007-01-19 15:20:45 status half-installed libdvdplay0 1.0.1-7
2007-01-19 15:20:46 status unpacked libdvdplay0 1.0.1-7
2007-01-19 15:20:46 status unpacked libdvdplay0 1.0.1-7
2007-01-19 15:20:46 status unpacked libdvdplay0 1.0.1-7
2007-01-19 15:20:46 status half-configured libdvdplay0 1.0.1-7
2007-01-19 15:20:47 status installed libdvdplay0 1.0.1-7
2007-01-19 15:21:24 status installed ubuntu-desktop 1.30
2007-01-19 15:21:24 remove ubuntu-desktop 1.30 1.30
2007-01-19 15:21:24 status half-configured ubuntu-desktop 1.30
2007-01-19 15:21:24 status half-installed ubuntu-desktop 1.30
2007-01-19 15:21:24 status config-files ubuntu-desktop 1.30
2007-01-19 15:21:24 status config-files ubuntu-desktop 1.30
2007-01-19 15:21:24 status config-files ubuntu-desktop 1.30
2007-01-19 15:21:24 status not-installed ubuntu-desktop <none>
2007-01-19 15:21:24 status installed totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 remove totem-mozilla 2.16.2-0ubuntu1 2.16.2-0ubuntu1
2007-01-19 15:21:24 status half-configured totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 status half-installed totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 status config-files totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 status config-files totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 status config-files totem-mozilla 2.16.2-0ubuntu1
2007-01-19 15:21:24 status not-installed totem-mozilla <none>
2007-01-19 15:21:39 install mozilla-mplayer <none> 3.31-1
2007-01-19 15:21:39 status half-installed mozilla-mplayer 3.31-1
2007-01-19 15:21:39 status unpacked mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status unpacked mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status unpacked mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status unpacked mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status unpacked mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status half-configured mozilla-mplayer 3.31-1
2007-01-19 15:21:40 status installed mozilla-mplayer 3.31-1
2007-01-19 15:21:50 status installed acpi 0.09-1
2007-01-19 15:21:50 remove acpi 0.09-1 0.09-1
2007-01-19 15:21:50 status half-configured acpi 0.09-1
2007-01-19 15:21:50 status half-installed acpi 0.09-1
2007-01-19 15:21:50 status config-files acpi 0.09-1
2007-01-19 15:21:50 status config-files acpi 0.09-1
2007-01-19 15:21:50 status config-files acpi 0.09-1
2007-01-19 15:21:50 status not-installed acpi <none>
2007-01-19 15:21:50 status installed apport-gtk 0.28
2007-01-19 15:21:50 remove apport-gtk 0.28 0.28
2007-01-19 15:21:50 status half-configured apport-gtk 0.28
2007-01-19 15:21:50 status half-installed apport-gtk 0.28
2007-01-19 15:21:50 status config-files apport-gtk 0.28
2007-01-19 15:21:51 status config-files apport-gtk 0.28
2007-01-19 15:21:51 status config-files apport-gtk 0.28
2007-01-19 15:21:51 status not-installed apport-gtk <none>
2007-01-19 15:21:51 status installed apport 0.28
2007-01-19 15:21:51 remove apport 0.28 0.28
2007-01-19 15:21:51 status half-configured apport 0.28
2007-01-19 15:21:51 status installed apport 0.28
2007-01-19 15:21:51 status installed gnome-orca 1.0.0-0ubuntu4
2007-01-19 15:21:51 remove gnome-orca 1.0.0-0ubuntu4 1.0.0-0ubuntu4
2007-01-19 15:21:51 status half-configured gnome-orca 1.0.0-0ubuntu4
2007-01-19 15:21:51 status half-installed gnome-orca 1.0.0-0ubuntu4
2007-01-19 15:21:52 status config-files gnome-orca 1.0.0-0ubuntu4
2007-01-19 15:21:52 status config-files gnome-orca 1.0.0-0ubuntu4
2007-01-19 15:21:52 status installed python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 remove python-at-spi 0.5.5-0ubuntu1 0.5.5-0ubuntu1
2007-01-19 15:21:52 status half-configured python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 status half-installed python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 status config-files python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 status config-files python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 status config-files python-at-spi 0.5.5-0ubuntu1
2007-01-19 15:21:52 status not-installed python-at-spi <none>
2007-01-19 15:21:52 status installed openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 remove openoffice.org-gnome 2.0.4-0ubuntu4 2.0.4-0ubuntu4
2007-01-19 15:21:52 status half-configured openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 status half-installed openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 status config-files openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 status config-files openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 status config-files openoffice.org-gnome 2.0.4-0ubuntu4
2007-01-19 15:21:52 status not-installed openoffice.org-gnome <none>
2007-01-19 15:21:52 status installed at-spi 1.7.12-0ubuntu1
2007-01-19 15:21:52 remove at-spi 1.7.12-0ubuntu1 1.7.12-0ubuntu1
2007-01-19 15:21:52 status half-configured at-spi 1.7.12-0ubuntu1
2007-01-19 15:21:52 status half-installed at-spi 1.7.12-0ubuntu1
2007-01-19 15:21:52 status installed avahi-daemon 0.6.13-2ubuntu2.4
2007-01-19 15:21:52 remove avahi-daemon 0.6.13-2ubuntu2.4 0.6.13-2ubuntu2.4
2007-01-19 15:21:52 status half-configured avahi-daemon 0.6.13-2ubuntu2.4
2007-01-19 15:21:52 status installed avahi-daemon 0.6.13-2ubuntu2.4
2007-01-19 15:21:52 status installed gnome-btdownload 0.0.24-0ubuntu1
2007-01-19 15:21:52 remove gnome-btdownload 0.0.24-0ubuntu1 0.0.24-0ubuntu1
2007-01-19 15:21:52 status half-configured gnome-btdownload 0.0.24-0ubuntu1
2007-01-19 15:21:53 status installed gnome-btdownload 0.0.24-0ubuntu1
2007-01-19 15:21:53 status installed bittorrent 3.4.2-6ubuntu3
2007-01-19 15:21:53 status installed bluez-cups 3.7-1ubuntu4
2007-01-19 15:21:53 remove bluez-cups 3.7-1ubuntu4 3.7-1ubuntu4
2007-01-19 15:21:53 status half-configured bluez-cups 3.7-1ubuntu4

```

---

### Post by Anonii on 2007-01-25
Bump.

What should I do? :/

---

### Post by maxamillion on 2007-01-25
use aptitude from now on ;)

---

### Post by neuromancer on 2007-02-28
This has happened to me when I removed a depedency package of ubuntu-desktop (not remember which one), and then everytime I used apt-get it told me that the other dependency of ubuntu-desktop could be safely removed.... Had to reinstall ubuntu-desktop with its dependencies.

I don't know if this was a bug that has been fixed, because I has just removed a dependency of ubuntu-desktop, but there is no more this list of safely removable packages.
Or maybe this happens only when you remove "critical" packages, don't know.

---

