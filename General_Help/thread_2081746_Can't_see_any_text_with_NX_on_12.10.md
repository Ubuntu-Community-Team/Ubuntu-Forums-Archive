---
title: "Can't see any text with NX on 12.10"
date: 2012-11-07
forum: General Help
---

### Post by Zoide7777 on 2012-11-07
There is something wrong with NX for remote access.  It was working fine on 12.04, but on 12.10 all of the text on menus, etc. is missing.

Apparently there is a known issue with 12.10 + NX ([http://www.nomachine.com/tr/view.php?id=TR10J02752]("http://www.nomachine.com/tr/view.php?id=TR10J02752")), but I tried some of the workarounds mentioned in the link and the text is still invisible.

I can see the text just fine through VNC, though.

This issue might be related to the one Maphrox reported in another thread ([http://ubuntuforums.org/showthread.php?t=2081531]("http://ubuntuforums.org/showthread.php?t=2081531")).

Any ideas?

Thanks

---

### Post by mayhan on 2012-11-08
Same problem here.

---

### Post by Zoide7777 on 2012-11-09
Workaround found!  Many thanks to ice9 and boof from the ArchLinux forums ([https://alderaan.archlinux.org/viewtopic.php?pid=1107447](https://alderaan.archlinux.org/viewtopic.php?pid=1107447)) for the idea of downgrading the libcairo library.

Here are the steps I followed for my 64-bit install of Ubuntu 12.10.  I suppose the workaround is the same for the 32-bit version, except you change the libcairo package and the file system paths accordingly:

[LIST=1]
[*]Terminate your NX sessions

[*]cd ~/Downloads

[*]wget [http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb)

[*]mkdir libcairo

[*]dpkg -x libcairo2_1.10.2-6.1ubuntu2_amd64.deb libcairo/

[*]sudo mkdir /usr/lib/x86_64-linux-gnu/libcairo_orig

[*]sudo mv /usr/lib/x86_64-linux-gnu/libcairo.so.2* /usr/lib/x86_64-linux-gnu/libcairo_orig/

[*]sudo cp ~/Downloads/libcairo/usr/lib/x86_64-linux-gnu/libcairo.so.2* /usr/lib/x86_64-linux-gnu/

[*]Re-connect to your machine via NX.
[/LIST]

---

### Post by mikewse on 2012-11-12
Thanks for the workaround, fixes my issues too!

I'm on Xubuntu 12.10 though, and text is correct initially. It is only after disconnecting and resuming a session that text disappears.

---

### Post by mayhan on 2012-11-12
Awesome.  Thanks.  Worked great.

---

### Post by jianboli on 2012-12-08
The workaround leads to evince not being able to open any pdf files.  I think the disabling Disable the render extension in client works: [http://askubuntu.com/questions/214580/nx-client-win-fonts-not-rendering-after-ubuntu-upgrade](http://askubuntu.com/questions/214580/nx-client-win-fonts-not-rendering-after-ubuntu-upgrade)

---

### Post by Zoide7777 on 2012-12-13
Just as a heads-up, you may have to downgrade libcairo-gobject as well using the one at [libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb]("libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb")

---

### Post by satosh on 2012-12-13
Amazing! Thanks for the downgrade-tip!

---

### Post by mikewse on 2012-12-14
I tried jianboli's solution and disabled Render Extension instead. Works fine so I have now restored libcairo to the original version.
I think this is much better as I can now view PDF files with evince again (which was broken by the libcairo downgrade).

---

### Post by ahoro on 2012-12-28
> **Zoide7777 said:**
> Just as a heads-up, you may have to downgrade libcairo-gobject as well using the one at [libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb]("http://libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb")

I can confirm that downgrade works for me
- ubuntu 12.10 server 64-bit, headless with mate-desktop

both libraries:
wget [http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo-gobject2_1.10.2-6ubuntu3_amd64.deb)
wget [http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb)


By the way disabling render extension did not help - fonts were still missing after session reconnect.
Is there an open bug report created for libcairo ?

---

### Post by jeverest on 2012-12-31
> **Zoide7777 said:**
> Workaround found!  Many thanks to ice9 and boof from the ArchLinux forums ([https://alderaan.archlinux.org/viewtopic.php?pid=1107447](https://alderaan.archlinux.org/viewtopic.php?pid=1107447)) for the idea of downgrading the libcairo library.

Here are the steps I followed for my 64-bit install of Ubuntu 12.10.  I suppose the workaround is the same for the 32-bit version, except you change the libcairo package and the file system paths accordingly:

[LIST=1]
[*]Terminate your NX sessions

[*]cd ~/Downloads

[*]wget [http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_amd64.deb)

[*]mkdir libcairo

[*]dpkg -x libcairo2_1.10.2-6.1ubuntu2_amd64.deb libcairo/

[*]sudo mkdir /usr/lib/x86_64-linux-gnu/libcairo_orig

[*]sudo mv /usr/lib/x86_64-linux-gnu/libcairo.so.2* /usr/lib/x86_64-linux-gnu/libcairo_orig/

[*]sudo cp ~/Downloads/libcairo/usr/lib/x86_64-linux-gnu/libcairo.so.2* /usr/lib/x86_64-linux-gnu/

[*]Re-connect to your machine via NX.
[/LIST]

The modified for 32-bit instructions:

[LIST=1]
[*]Terminate your NX sessions

[*]cd ~/Downloads

[*]wget [http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/c/cairo/libcairo2_1.10.2-6.1ubuntu2_i386.deb)

[*]mkdir libcairo

[*]dpkg -x libcairo2_1.10.2-6.1ubuntu2_i386.deb libcairo/

[*]sudo mkdir /usr/lib/i386-linux-gnu/libcairo_orig

[*]sudo mv /usr/lib/i386-linux-gnu/libcairo.so.2* /usr/lib/i386-linux-gnu/libcairo_orig/

[*]sudo cp ~/Downloads/libcairo/usr/lib/i386-linux-gnu/libcairo.so.2* /usr/lib/i386-linux-gnu/

[*]Re-connect to your machine via NX.
[/LIST]

Worked great for me.  Thanks for the instructions!

---

### Post by teward on 2013-01-01
Okay, time for reasons why this workaround should NOT be done:

**BEGIN**

There apparently seems to be the following happening here:
(1) Downgrading libraries to older releases' versions
(2) Doing this manually.

As of Precise, the rdepends on libcairo2 (which you seem to be downgrading) are:
```
libcairo2
Reverse Depends:
  chromium-browser
  unity-2d-panel
  libunity-2d-private0
  librhythmbox-core5
  tickr
  conky-std
  libreoffice-core:i386
  libcairo2:i386
  libcairo2:i386
  flashplugin-installer
  winff
  vinagre
  synapse
  quadrapassel
  psensor
  lightsoff
  lightdm-gtk-greeter
  libreoffice-gtk3
  libpanel-applet-4-0
  libjava-gnome-jni
  libgldi3
  libfm-gtk1
  libcheese-gtk21
  indicator-sound-gtk2
  indicator-messages-gtk2
  iagno
  gstreamer0.10-plugins-bad
  gnotski
  gnotravex
  gnomeradio
  gnome-themes-standard
  gnome-panel
  gnome-dictionary
  gnobots2
  gnect
  glom
  glines
  glchess
  evince-gtk
  epiphany-browser
  empathy-call
  clutter-1.0-tests
  chromium-browser
  cairo-perf-utils
  cairo-dock-core
  banshee
  audacious-plugins
  activity-log-manager
  xchat-gnome
  vino
  unity-greeter
  unity-2d-panel
  unity
  ubiquity-frontend-gtk
  totem
  thunderbird
  simple-scan
  shotwell
  remmina-plugin-vnc
  remmina-plugin-rdp
  python3-gi-dbg
  python3-gi-cairo
  python-gi-dbg
  python-gi-cairo
  poppler-utils
  pidgin
  nautilus
  mahjongg
  lsb-desktop
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libunity-2d-private0
  libtotem0
  librhythmbox-core5
  libreoffice-core
  libreoffice-core
  libpoppler-glib8
  libpango1.0-dev
  libpango1.0-0
  liboverlay-scrollbar3-0.2-0
  liboverlay-scrollbar-0.2-0
  libnux-2.0-0
  libmono-cairo4.0-cil
  libmono-cairo2.0-cil
  libmagickcore4-extra
  libgwibber-gtk2
  libgtksourceview-3.0-0
  libgtkhtml-editor-4.0-0
  libgtkhtml-4.0-0
  libgtk-3-0
  libgnome-desktop-3-2
  libgladeui-2-0
  libgimp2.0
  libevince3-3
  libedataserverui-3.0-1
  libclutter-1.0-0
  libcairo2-dev
  libcairo2-dbg
  libcairo-script-interpreter2
  libcairo-gobject2
  libbrasero-media3-1
  ldm
  indicator-sound
  indicator-messages
  gwibber
  gtk2-engines-oxygen
  gtk-3-examples
  gstreamer0.10-x
  gnomine
  gnome-settings-daemon
  gnome-power-manager
  gnome-control-center
  gimp
  firefox
  evince
  eog
  compiz-plugins
  compiz-gnome
  brasero
  activity-log-manager-control-center
  libreoffice-core:i386
  libcairo2:i386
  libcairo2:i386
  xvid4conf
  uae
  kcemu
  gtktrain
  flashplugin-installer
  easyspice
  e-uae
  darksnow
  avidemux
  zita-rev1
  zita-at1
  zathura
  yersinia
  xvattr
  xsynth-dssi
  xsunpinyin
  xsensors
  xournal
  xmlroff
  xmedcon
  xlog
  xiphos
  xfswitch-plugin
  xfdesktop4
  xfce4-xkb-plugin
  xfce4-wmdock-plugin
  xfce4-weather-plugin
  xfce4-wavelan-plugin
  xfce4-verve-plugin
  xfce4-timer-plugin
  xfce4-time-out-plugin
  xfce4-taskmanager
  xfce4-systemload-plugin
  xfce4-settings
  xfce4-session
  xfce4-sensors-plugin
  xfce4-screenshooter
  xfce4-radio-plugin
  xfce4-power-manager-plugins
  xfce4-power-manager
  xfce4-places-plugin
  xfce4-panel
  xfce4-notifyd
  xfce4-notes-plugin
  xfce4-notes
  xfce4-netload-plugin
  xfce4-mpc-plugin
  xfce4-mount-plugin
  xfce4-mixer
  xfce4-messenger-plugin
  xfce4-mailwatch-plugin
  xfce4-linelight-plugin
  xfce4-indicator-plugin
  xfce4-hdaps
  xfce4-genmon-plugin
  xfce4-fsguard-plugin
  xfce4-eyes-plugin
  xfce4-diskperf-plugin
  xfce4-dict
  xfce4-cpugraph-plugin
  xfce4-cpufreq-plugin
  xfce4-cellmodem-plugin
  xfce4-battery-plugin
  xcowsay
  xcfa
  xcdroast
  xarchiver
  workrave
  wmressel
  wmbubble
  winwrangler
  winff
  winefish
  weston
  wesnoth-1.10-core
  webkit2pdf
  wavbreaker
  vinagre
  viking
  vala-gen-project
  v-sim
  upnp-router-control
  ukopp
  uim-gtk3
  uim-gtk2.0
  uget
  tuxtype
  tuxpaint
  tuxmath
  tumbler
  transgui
  tint2
  tilp2
  tilda
  tiemu-skinedit
  tickr
  thunar-vcs-plugin
  thunar
  threadscope
  thewidgetfactory
  tenace
  telepathy-inspector
  sync-ui
  synapse
  sylpheed
  sugar-artwork-0.92
  sugar-artwork-0.90
  sugar-artwork-0.88
  sugar-artwork-0.86
  sugar-artwork-0.84
  ssh-askpass-fullscreen
  squeak-plugins-scratch
  spotlighter
  spek
  spectools
  sndfile-tools
  snd-gtk-pulse
  snd-gtk-jack
  sm
  simdock
  shoes
  sgt-puzzles
  screentest
  scite
  scim-skk
  scim-prime
  scim-kmfl-imengine
  scim-canna
  sane
  sanduhr
  sagcad
  ruby-pango
  ruby-gtk2
  ruby-cairo
  rox-filer
  ristretto
  rgbpaint
  resapplet
  rep-gtk
  rawstudio
  rasmol
  radare-gtk
  r-cran-rgtk2
  r-cran-cairodevice
  r-base-core
  qxw
  quarry
  quadrapassel
  python-sugar-toolkit-0.90
  python-sugar-toolkit-0.88
  python-sugar-toolkit-0.86
  python-sugar-toolkit-0.84
  python-mapscript
  python-libavg
  python-hippocanvas
  python-gtk-gnash
  python-awn
  pureadmin
  pspp
  psensor
  praat
  pqiv
  postler
  plymouth-x11
  plplot11-driver-cairo
  planner
  pioneers
  pinpoint
  pidgin-gmchess
  picviz
  php5-mapscript
  petri-foo
  performous
  pegsolitaire
  pdfmod
  pdfcube
  pdf2svg
  pdf-presenter-console
  pcmanfm
  pcb2gcode
  pcb-gtk
  parole
  pan
  osmo
  oregano
  orage
  optgeo
  ocamlviz
  ocaml-melt
  nvtv
  nted
  nitrogen
  netsurf-gtk
  netspeed
  nautilus-ideviceinfo
  mysql-workbench
  mx44
  mutter
  multiget
  mrwtoppm-gimp
  mricron
  mp3splt-gtk
  mp3info-gtk
  monodevelop
  mlterm-common
  mistelix
  midori
  medit
  medcon
  mathwar
  mapserver-bin
  mango-lassi
  mail-notification
  macopix-gtk2
  lxsession
  lxlauncher
  lxdm
  lostirc
  lombard
  lives
  linsmith
  lightspark-common
  lightsoff
  lightdm-gtk-greeter
  libwxsvg0
  libswt-cairo-gtk-3-jni
  libswami0
  libspice-client-gtk-3.0-1
  libspice-client-gtk-2.0-1
  libseed-gtk3-0
  libreoffice-gtk3
  libpigment0.3-11
  libpanel-applet-4-0
  libosmgpsmap2
  libopenslide0
  libopenscenegraph80
  libmx-1.0-2
  libmutter0
  libmemphis-0.2-0
  libmdc2
  libmapscript-ruby1.9.1
  libmapscript-ruby1.8
  libmapscript-perl
  libmapnik2-2.0
  libmagplus3
  liblunar-1-0
  liblua5.1-oocairo0
  libjava-gnome-jni
  libjana-gtk0
  libipe7.1.1
  libinfgtk-0.5-0
  libhyena-cil
  libhippocanvas-1-0
  libgxps2
  libgxps-utils
  libgwyddion2-0
  libgvc5-plugins-gtk
  libgv-tcl
  libguac1
  libguac-client-vnc0
  libgtksourceview2.0-0
  libgtkimageview0
  libgtkhtml3.14-19
  libgtkhtml-editor0
  libgtkhex-3-0
  libgtkdatabox-0.9.1-1
  libgtkada2.24.1
  libgtk2-gst
  libgrits4
  libgranite0
  libgpewidget1
  libgpepimc0
  libgoocanvas-2.0-9
  libgoo-canvas-perl
  libgoffice-0.8-8
  libgnomeuimm-2.6-1c2a
  libgnomescan0
  libgnomemm-2.6-1c2
  libgnomecanvasmm-2.6-1c2a
  libgmtk0
  libgldi3
  libgladeui-1-11
  libglademm-2.4-1c2a
  libgjs0c
  libgdl-3-2
  libgcu0
  libfm-gtk1
  libfltk-cairo1.3
  libexo-1-0
  libevas1
  libdisplaymigration0
  libclinica0
  libcheese-gtk21
  libchamplain-0.12-0
  libccss-1-5
  libcairo5c-0
  libcairo-ocaml
  libbakery-2.6-1
  libawn1
  libaosd2
  libaosd-text2
  libanjuta-3-0
  libabiword-2.9
  leafpad
  lazarus-ide-gtk2-0.9.30.2
  lazarus-ide-0.9.30.2
  langdrill
  kompozer
  kmplayer
  klash
  keynav
  keyboardcast
  katoob
  kanatest
  jpilot-backup
  jeex
  jackeq
  jackbeat
  ir.lv2
  ipe
  invada-studio-plugins-lv2
  indicator-sound-gtk2
  indicator-session-gtk2
  indicator-network
  indicator-multiload
  indicator-messages-gtk2
  imagination
  iagno
  i3lock
  hwloc
  hoz-gui
  homebank
  hledger-chart
  hitori
  hexxagon
  gyrus
  gxtuner
  gxneur
  gxmessage
  gworldclock
  gwhere
  gwaterfall
  gwaei
  gummi
  guitarix
  guile-gnome2-gtk
  guile-cairo
  gtrayicon
  gtkrsync
  gtkpool
  gtkpod
  gtkballs
  gtkatlantic
  gtk2-engines-wonderland
  gtk2-engines-qtcurve
  gtk2-engines-pixbuf
  gtk2-engines-nodoka
  gtk2-engines-moblin
  gtk2-engines-equinox
  gtk2-engines-cleanice
  gtk2-engines-aurora
  gtk-vector-screenshot
  gtk-theme-switch
  gthumb
  gtans
  gstreamer0.10-plugins-bad
  gstreamer0.10-hplugins
  gsoko
  gsmc
  gsetroot
  grpn
  groundhog
  grisbi
  gringotts
  gretl
  grcm
  grass
  gprompter
  gpredict
  gpomme
  gplanarity
  gpiv-mpi
  gpiv
  gpicview
  gpick
  gpe-watch
  gpe-todo
  gpe-timesheet
  gpe-tetris
  gpe-su
  gpe-soundbite
  gpe-question
  gpe-othello
  gpe-mininet
  gpe-lights
  gpe-julia
  gpe-go
  gpe-edit
  gpe-contacts
  gpe-clock
  gpe-appmgr
  gpe-announce
  gpdftext
  gpaint
  gpaco
  gnustep-back0.20-cairo
  gnuspool
  gnuplot-x11
  gnuplot-nox
  gnumeric
  gnucash
  gnubg
  gnotski
  gnotravex
  gnomeradio
  gnomekiss
  gnome-web-photo
  gnome-time-admin
  gnome-themes-standard
  gnome-sushi
  gnome-shell
  gnome-pie
  gnome-panel
  gnome-paint
  gnome-mplayer
  gnome-mastermind
  gnome-documents
  gnome-dictionary
  gnome-contacts
  gnome-color-manager
  gnome-applets
  gnobots2
  gnect
  gnat-gps
  gnash-common
  gnash
  gmult
  gmrun
  gmpc
  gmfsk
  glurp
  glom
  glines
  glchess
  glabels
  gkrellweather
  gkrellshoot
  gkrellmoon
  gkrellmitime
  gkrellm-xkb
  gkrellm-reminder
  gkrellm-leds
  gjiten
  gitg
  ginkgocadx
  gimp-resynthesizer
  gimp-gluas
  gimp-dimage-color
  gimp-dcraw
  giggle
  ghostess
  ghex
  ggobi
  gfm
  gexec
  gerbv
  gegl
  geda-gschem
  geany
  gdm
  gcursor
  gcu-bin
  gcrystal
  gconjugue
  gcompris
  gchempaint
  gcc-snapshot
  gbemol
  gbase
  gamine
  gamazons
  gabedit
  g3data
  fyre
  fvwm
  fprint-demo
  fped
  fotoxx
  foo-yc20
  fntsample
  firestarter
  fillmore
  fdclock
  fcitx-ui-classic
  fcitx-module-x11
  f-spot
  evince-gtk
  epiphany-browser
  epdfview
  eog-plugins
  empathy-call
  emilda-print
  efax-gtk
  easymp3gain-gtk
  dvdisaster
  dozzaqueux
  dkopp
  dia
  desmume
  deskscribe
  deskmenu
  denemo
  darktable-plugins-experimental
  darktable
  cutter-report-module
  curtain
  cqrlog
  conky-std
  conky-all
  conglomerate
  compiz-plugins-extra
  clutter-1.0-tests
  claws-mail
  chromium-browser
  cgi-mapserver
  cellwriter
  celestia-gnome
  cccd
  carettah
  calf-plugins
  calcoo
  cairo-perf-utils
  cairo-dock-plug-ins
  cairo-dock-core
  cairo-clock
  bygfoot
  buzztard
  bustle
  buici-clock
  bsnes
  browser-plugin-vlc
  browser-plugin-packagekit
  bombono-dvd
  bluefish
  bitmeter
  bist
  bibledit-gtk
  banshee
  balsa
  awn-applet-sysmon
  awn-applet-shinyswitcher
  awn-applet-places
  awn-applet-notification-area
  awn-applet-indicator
  awn-applet-cairo-main-menu
  awn-applet-awn-system-monitor
  awn-applet-awn-notification-daemon
  awesome
  avant-window-navigator
  audacious-plugins
  aterm-ml
  aterm
  ardour
  ardesia
  aqualung
  apwal
  apvlv
  anypaper
  anjuta-extras
  anjuta
  angband
  alsaplayer-gtk
  almanah
  agave
  activity-log-manager
  abraca
  xchat-gnome
  vino
  unity-greeter
  unity-2d-panel
  unity
  ubiquity-frontend-gtk
  totem
  thunderbird
  simple-scan
  shotwell
  scribus
  remmina-plugin-vnc
  remmina-plugin-rdp
  python3-gi-dbg
  python3-gi-cairo
  python3-cairo
  python-pygoocanvas
  python-gtk2-dbg
  python-gtk2
  python-gi-dbg
  python-gi-cairo
  python-cairo-dbg
  python-cairo
  poppler-utils
  plymouth-label
  pidgin
  notify-osd
  notification-daemon
  nautilus
  mousetweaks
  metacity
  malaga-bin
  mahjongg
  lsb-desktop
  liferea
  libwnck22
  libwnck-3-0
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libvte9
  libvte-2.90-9
  libunity-misc4
  libunity-2d-private0
  libtotem0
  libtimezonemap1
  libsexy2
  librsvg2-bin
  librsvg2-2
  librrd4
  librhythmbox-core5
  libreoffice-core
  libreoffice-core
  libpoppler-glib8
  libpango1.0-dev
  libpango1.0-0
  libpango-perl
  liboverlay-scrollbar3-0.2-0
  liboverlay-scrollbar-0.2-0
  libnux-2.0-0
  libmono-cairo4.0-cil
  libmono-cairo2.0-cil
  libmetacity-private0
  libmagickcore4-extra
  libgwibber-gtk2
  libgvc5
  libgucharmap-2-90-7
  libgtksourceview-3.0-0
  libgtkhtml-editor-4.0-0
  libgtkhtml-4.0-0
  libgtk2.0-cil
  libgtk2.0-0
  libgtk2-perl
  libgtk-vnc-2.0-0
  libgtk-vnc-1.0-0
  libgtk-3-0
  libgoocanvas3
  libgnomekbd7
  libgnome-desktop-3-2
  libgnome-desktop-2-17
  libgladeui-2-0
  libgksu2-0
  libgimp2.0
  libgegl-0.0-0
  libgdu-gtk0
  libgdraw4
  libgdiplus
  libgcr-3-1
  libgcj12-awt
  libevolution
  libevince3-3
  libedataserverui-3.0-1
  libcogl-pango0
  libclutter-gtk-1.0-0
  libclutter-1.0-0
  libcairomm-1.0-1
  libcairo2-dev
  libcairo2-dbg
  libcairo-script-interpreter2
  libcairo-perl
  libcairo-gobject2
  libbrasero-media3-1
  libbonoboui2-dev
  libbonoboui2-0
  ldm
  inkscape
  indicator-sound
  indicator-session
  indicator-printers
  indicator-messages
  indicator-datetime
  gwibber
  gucharmap
  gtk3-engines-unico
  gtk3-engines-oxygen
  gtk2.0-examples
  gtk2-engines-oxygen
  gtk2-engines-murrine
  gtk2-engines
  gtk-3-examples
  gstreamer0.10-x
  gstreamer0.10-plugins-good
  gnomine
  gnome-system-monitor
  gnome-settings-daemon
  gnome-session-bin
  gnome-screenshot
  gnome-screensaver
  gnome-power-manager
  gnome-nettool
  gnome-font-viewer
  gnome-control-center
  gimp
  gedit
  firefox
  file-roller
  evolution-plugins
  evince
  eog
  dia-libs
  dia-gnome
  compiz-plugins-main-default
  compiz-plugins-main
  compiz-plugins
  compiz-gnome
  brasero
  baobab
  aisleriot
  activity-log-manager-control-center
```What rdepends means is that all these things depend at some point on libcairo2.  Assuming that these rdepends are the same on Quantal (and the probably are, except for removed packages), downgrading can have serious repercussions for all the software listed on this system.  So while downgrading may repair this issue for you guys, you're now: (1) unable to get bug reports filed for the software i just listed because you're using older libraries using ubuntu-bug, (2) making a HUGE list of potential problems for newer software using older libraries (because functionality likely depends on the newer libraries), and (3) diverging somewhat from the release of Ubuntu you are on.

**This type of workaround is ill-advised.  As a member of Bug Squad and Bug Control, I do *not* suggest you downgrade your libraries as you did here by hand, since it can introduce a whole mess of other bugs.**

**DONE**

---

### Post by Zoide7777 on 2013-01-03
> **Lord of Time said:**
> Okay, time for reasons why this workaround should NOT be done:

**BEGIN**

There apparently seems to be the following happening here:
(1) Downgrading libraries to older releases' versions
(2) Doing this manually.

As of Precise, the rdepends on libcairo2 (which you seem to be downgrading) are:
```
libcairo2
Reverse Depends:
  chromium-browser
  unity-2d-panel
  libunity-2d-private0
  librhythmbox-core5
  tickr
  conky-std
  libreoffice-core:i386
  libcairo2:i386
  libcairo2:i386
  flashplugin-installer
  winff
  vinagre
  synapse
  quadrapassel
  psensor
  lightsoff
  lightdm-gtk-greeter
  libreoffice-gtk3
  libpanel-applet-4-0
  libjava-gnome-jni
  libgldi3
  libfm-gtk1
  libcheese-gtk21
  indicator-sound-gtk2
  indicator-messages-gtk2
  iagno
  gstreamer0.10-plugins-bad
  gnotski
  gnotravex
  gnomeradio
  gnome-themes-standard
  gnome-panel
  gnome-dictionary
  gnobots2
  gnect
  glom
  glines
  glchess
  evince-gtk
  epiphany-browser
  empathy-call
  clutter-1.0-tests
  chromium-browser
  cairo-perf-utils
  cairo-dock-core
  banshee
  audacious-plugins
  activity-log-manager
  xchat-gnome
  vino
  unity-greeter
  unity-2d-panel
  unity
  ubiquity-frontend-gtk
  totem
  thunderbird
  simple-scan
  shotwell
  remmina-plugin-vnc
  remmina-plugin-rdp
  python3-gi-dbg
  python3-gi-cairo
  python-gi-dbg
  python-gi-cairo
  poppler-utils
  pidgin
  nautilus
  mahjongg
  lsb-desktop
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libunity-2d-private0
  libtotem0
  librhythmbox-core5
  libreoffice-core
  libreoffice-core
  libpoppler-glib8
  libpango1.0-dev
  libpango1.0-0
  liboverlay-scrollbar3-0.2-0
  liboverlay-scrollbar-0.2-0
  libnux-2.0-0
  libmono-cairo4.0-cil
  libmono-cairo2.0-cil
  libmagickcore4-extra
  libgwibber-gtk2
  libgtksourceview-3.0-0
  libgtkhtml-editor-4.0-0
  libgtkhtml-4.0-0
  libgtk-3-0
  libgnome-desktop-3-2
  libgladeui-2-0
  libgimp2.0
  libevince3-3
  libedataserverui-3.0-1
  libclutter-1.0-0
  libcairo2-dev
  libcairo2-dbg
  libcairo-script-interpreter2
  libcairo-gobject2
  libbrasero-media3-1
  ldm
  indicator-sound
  indicator-messages
  gwibber
  gtk2-engines-oxygen
  gtk-3-examples
  gstreamer0.10-x
  gnomine
  gnome-settings-daemon
  gnome-power-manager
  gnome-control-center
  gimp
  firefox
  evince
  eog
  compiz-plugins
  compiz-gnome
  brasero
  activity-log-manager-control-center
  libreoffice-core:i386
  libcairo2:i386
  libcairo2:i386
  xvid4conf
  uae
  kcemu
  gtktrain
  flashplugin-installer
  easyspice
  e-uae
  darksnow
  avidemux
  zita-rev1
  zita-at1
  zathura
  yersinia
  xvattr
  xsynth-dssi
  xsunpinyin
  xsensors
  xournal
  xmlroff
  xmedcon
  xlog
  xiphos
  xfswitch-plugin
  xfdesktop4
  xfce4-xkb-plugin
  xfce4-wmdock-plugin
  xfce4-weather-plugin
  xfce4-wavelan-plugin
  xfce4-verve-plugin
  xfce4-timer-plugin
  xfce4-time-out-plugin
  xfce4-taskmanager
  xfce4-systemload-plugin
  xfce4-settings
  xfce4-session
  xfce4-sensors-plugin
  xfce4-screenshooter
  xfce4-radio-plugin
  xfce4-power-manager-plugins
  xfce4-power-manager
  xfce4-places-plugin
  xfce4-panel
  xfce4-notifyd
  xfce4-notes-plugin
  xfce4-notes
  xfce4-netload-plugin
  xfce4-mpc-plugin
  xfce4-mount-plugin
  xfce4-mixer
  xfce4-messenger-plugin
  xfce4-mailwatch-plugin
  xfce4-linelight-plugin
  xfce4-indicator-plugin
  xfce4-hdaps
  xfce4-genmon-plugin
  xfce4-fsguard-plugin
  xfce4-eyes-plugin
  xfce4-diskperf-plugin
  xfce4-dict
  xfce4-cpugraph-plugin
  xfce4-cpufreq-plugin
  xfce4-cellmodem-plugin
  xfce4-battery-plugin
  xcowsay
  xcfa
  xcdroast
  xarchiver
  workrave
  wmressel
  wmbubble
  winwrangler
  winff
  winefish
  weston
  wesnoth-1.10-core
  webkit2pdf
  wavbreaker
  vinagre
  viking
  vala-gen-project
  v-sim
  upnp-router-control
  ukopp
  uim-gtk3
  uim-gtk2.0
  uget
  tuxtype
  tuxpaint
  tuxmath
  tumbler
  transgui
  tint2
  tilp2
  tilda
  tiemu-skinedit
  tickr
  thunar-vcs-plugin
  thunar
  threadscope
  thewidgetfactory
  tenace
  telepathy-inspector
  sync-ui
  synapse
  sylpheed
  sugar-artwork-0.92
  sugar-artwork-0.90
  sugar-artwork-0.88
  sugar-artwork-0.86
  sugar-artwork-0.84
  ssh-askpass-fullscreen
  squeak-plugins-scratch
  spotlighter
  spek
  spectools
  sndfile-tools
  snd-gtk-pulse
  snd-gtk-jack
  sm
  simdock
  shoes
  sgt-puzzles
  screentest
  scite
  scim-skk
  scim-prime
  scim-kmfl-imengine
  scim-canna
  sane
  sanduhr
  sagcad
  ruby-pango
  ruby-gtk2
  ruby-cairo
  rox-filer
  ristretto
  rgbpaint
  resapplet
  rep-gtk
  rawstudio
  rasmol
  radare-gtk
  r-cran-rgtk2
  r-cran-cairodevice
  r-base-core
  qxw
  quarry
  quadrapassel
  python-sugar-toolkit-0.90
  python-sugar-toolkit-0.88
  python-sugar-toolkit-0.86
  python-sugar-toolkit-0.84
  python-mapscript
  python-libavg
  python-hippocanvas
  python-gtk-gnash
  python-awn
  pureadmin
  pspp
  psensor
  praat
  pqiv
  postler
  plymouth-x11
  plplot11-driver-cairo
  planner
  pioneers
  pinpoint
  pidgin-gmchess
  picviz
  php5-mapscript
  petri-foo
  performous
  pegsolitaire
  pdfmod
  pdfcube
  pdf2svg
  pdf-presenter-console
  pcmanfm
  pcb2gcode
  pcb-gtk
  parole
  pan
  osmo
  oregano
  orage
  optgeo
  ocamlviz
  ocaml-melt
  nvtv
  nted
  nitrogen
  netsurf-gtk
  netspeed
  nautilus-ideviceinfo
  mysql-workbench
  mx44
  mutter
  multiget
  mrwtoppm-gimp
  mricron
  mp3splt-gtk
  mp3info-gtk
  monodevelop
  mlterm-common
  mistelix
  midori
  medit
  medcon
  mathwar
  mapserver-bin
  mango-lassi
  mail-notification
  macopix-gtk2
  lxsession
  lxlauncher
  lxdm
  lostirc
  lombard
  lives
  linsmith
  lightspark-common
  lightsoff
  lightdm-gtk-greeter
  libwxsvg0
  libswt-cairo-gtk-3-jni
  libswami0
  libspice-client-gtk-3.0-1
  libspice-client-gtk-2.0-1
  libseed-gtk3-0
  libreoffice-gtk3
  libpigment0.3-11
  libpanel-applet-4-0
  libosmgpsmap2
  libopenslide0
  libopenscenegraph80
  libmx-1.0-2
  libmutter0
  libmemphis-0.2-0
  libmdc2
  libmapscript-ruby1.9.1
  libmapscript-ruby1.8
  libmapscript-perl
  libmapnik2-2.0
  libmagplus3
  liblunar-1-0
  liblua5.1-oocairo0
  libjava-gnome-jni
  libjana-gtk0
  libipe7.1.1
  libinfgtk-0.5-0
  libhyena-cil
  libhippocanvas-1-0
  libgxps2
  libgxps-utils
  libgwyddion2-0
  libgvc5-plugins-gtk
  libgv-tcl
  libguac1
  libguac-client-vnc0
  libgtksourceview2.0-0
  libgtkimageview0
  libgtkhtml3.14-19
  libgtkhtml-editor0
  libgtkhex-3-0
  libgtkdatabox-0.9.1-1
  libgtkada2.24.1
  libgtk2-gst
  libgrits4
  libgranite0
  libgpewidget1
  libgpepimc0
  libgoocanvas-2.0-9
  libgoo-canvas-perl
  libgoffice-0.8-8
  libgnomeuimm-2.6-1c2a
  libgnomescan0
  libgnomemm-2.6-1c2
  libgnomecanvasmm-2.6-1c2a
  libgmtk0
  libgldi3
  libgladeui-1-11
  libglademm-2.4-1c2a
  libgjs0c
  libgdl-3-2
  libgcu0
  libfm-gtk1
  libfltk-cairo1.3
  libexo-1-0
  libevas1
  libdisplaymigration0
  libclinica0
  libcheese-gtk21
  libchamplain-0.12-0
  libccss-1-5
  libcairo5c-0
  libcairo-ocaml
  libbakery-2.6-1
  libawn1
  libaosd2
  libaosd-text2
  libanjuta-3-0
  libabiword-2.9
  leafpad
  lazarus-ide-gtk2-0.9.30.2
  lazarus-ide-0.9.30.2
  langdrill
  kompozer
  kmplayer
  klash
  keynav
  keyboardcast
  katoob
  kanatest
  jpilot-backup
  jeex
  jackeq
  jackbeat
  ir.lv2
  ipe
  invada-studio-plugins-lv2
  indicator-sound-gtk2
  indicator-session-gtk2
  indicator-network
  indicator-multiload
  indicator-messages-gtk2
  imagination
  iagno
  i3lock
  hwloc
  hoz-gui
  homebank
  hledger-chart
  hitori
  hexxagon
  gyrus
  gxtuner
  gxneur
  gxmessage
  gworldclock
  gwhere
  gwaterfall
  gwaei
  gummi
  guitarix
  guile-gnome2-gtk
  guile-cairo
  gtrayicon
  gtkrsync
  gtkpool
  gtkpod
  gtkballs
  gtkatlantic
  gtk2-engines-wonderland
  gtk2-engines-qtcurve
  gtk2-engines-pixbuf
  gtk2-engines-nodoka
  gtk2-engines-moblin
  gtk2-engines-equinox
  gtk2-engines-cleanice
  gtk2-engines-aurora
  gtk-vector-screenshot
  gtk-theme-switch
  gthumb
  gtans
  gstreamer0.10-plugins-bad
  gstreamer0.10-hplugins
  gsoko
  gsmc
  gsetroot
  grpn
  groundhog
  grisbi
  gringotts
  gretl
  grcm
  grass
  gprompter
  gpredict
  gpomme
  gplanarity
  gpiv-mpi
  gpiv
  gpicview
  gpick
  gpe-watch
  gpe-todo
  gpe-timesheet
  gpe-tetris
  gpe-su
  gpe-soundbite
  gpe-question
  gpe-othello
  gpe-mininet
  gpe-lights
  gpe-julia
  gpe-go
  gpe-edit
  gpe-contacts
  gpe-clock
  gpe-appmgr
  gpe-announce
  gpdftext
  gpaint
  gpaco
  gnustep-back0.20-cairo
  gnuspool
  gnuplot-x11
  gnuplot-nox
  gnumeric
  gnucash
  gnubg
  gnotski
  gnotravex
  gnomeradio
  gnomekiss
  gnome-web-photo
  gnome-time-admin
  gnome-themes-standard
  gnome-sushi
  gnome-shell
  gnome-pie
  gnome-panel
  gnome-paint
  gnome-mplayer
  gnome-mastermind
  gnome-documents
  gnome-dictionary
  gnome-contacts
  gnome-color-manager
  gnome-applets
  gnobots2
  gnect
  gnat-gps
  gnash-common
  gnash
  gmult
  gmrun
  gmpc
  gmfsk
  glurp
  glom
  glines
  glchess
  glabels
  gkrellweather
  gkrellshoot
  gkrellmoon
  gkrellmitime
  gkrellm-xkb
  gkrellm-reminder
  gkrellm-leds
  gjiten
  gitg
  ginkgocadx
  gimp-resynthesizer
  gimp-gluas
  gimp-dimage-color
  gimp-dcraw
  giggle
  ghostess
  ghex
  ggobi
  gfm
  gexec
  gerbv
  gegl
  geda-gschem
  geany
  gdm
  gcursor
  gcu-bin
  gcrystal
  gconjugue
  gcompris
  gchempaint
  gcc-snapshot
  gbemol
  gbase
  gamine
  gamazons
  gabedit
  g3data
  fyre
  fvwm
  fprint-demo
  fped
  fotoxx
  foo-yc20
  fntsample
  firestarter
  fillmore
  fdclock
  fcitx-ui-classic
  fcitx-module-x11
  f-spot
  evince-gtk
  epiphany-browser
  epdfview
  eog-plugins
  empathy-call
  emilda-print
  efax-gtk
  easymp3gain-gtk
  dvdisaster
  dozzaqueux
  dkopp
  dia
  desmume
  deskscribe
  deskmenu
  denemo
  darktable-plugins-experimental
  darktable
  cutter-report-module
  curtain
  cqrlog
  conky-std
  conky-all
  conglomerate
  compiz-plugins-extra
  clutter-1.0-tests
  claws-mail
  chromium-browser
  cgi-mapserver
  cellwriter
  celestia-gnome
  cccd
  carettah
  calf-plugins
  calcoo
  cairo-perf-utils
  cairo-dock-plug-ins
  cairo-dock-core
  cairo-clock
  bygfoot
  buzztard
  bustle
  buici-clock
  bsnes
  browser-plugin-vlc
  browser-plugin-packagekit
  bombono-dvd
  bluefish
  bitmeter
  bist
  bibledit-gtk
  banshee
  balsa
  awn-applet-sysmon
  awn-applet-shinyswitcher
  awn-applet-places
  awn-applet-notification-area
  awn-applet-indicator
  awn-applet-cairo-main-menu
  awn-applet-awn-system-monitor
  awn-applet-awn-notification-daemon
  awesome
  avant-window-navigator
  audacious-plugins
  aterm-ml
  aterm
  ardour
  ardesia
  aqualung
  apwal
  apvlv
  anypaper
  anjuta-extras
  anjuta
  angband
  alsaplayer-gtk
  almanah
  agave
  activity-log-manager
  abraca
  xchat-gnome
  vino
  unity-greeter
  unity-2d-panel
  unity
  ubiquity-frontend-gtk
  totem
  thunderbird
  simple-scan
  shotwell
  scribus
  remmina-plugin-vnc
  remmina-plugin-rdp
  python3-gi-dbg
  python3-gi-cairo
  python3-cairo
  python-pygoocanvas
  python-gtk2-dbg
  python-gtk2
  python-gi-dbg
  python-gi-cairo
  python-cairo-dbg
  python-cairo
  poppler-utils
  plymouth-label
  pidgin
  notify-osd
  notification-daemon
  nautilus
  mousetweaks
  metacity
  malaga-bin
  mahjongg
  lsb-desktop
  liferea
  libwnck22
  libwnck-3-0
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libvte9
  libvte-2.90-9
  libunity-misc4
  libunity-2d-private0
  libtotem0
  libtimezonemap1
  libsexy2
  librsvg2-bin
  librsvg2-2
  librrd4
  librhythmbox-core5
  libreoffice-core
  libreoffice-core
  libpoppler-glib8
  libpango1.0-dev
  libpango1.0-0
  libpango-perl
  liboverlay-scrollbar3-0.2-0
  liboverlay-scrollbar-0.2-0
  libnux-2.0-0
  libmono-cairo4.0-cil
  libmono-cairo2.0-cil
  libmetacity-private0
  libmagickcore4-extra
  libgwibber-gtk2
  libgvc5
  libgucharmap-2-90-7
  libgtksourceview-3.0-0
  libgtkhtml-editor-4.0-0
  libgtkhtml-4.0-0
  libgtk2.0-cil
  libgtk2.0-0
  libgtk2-perl
  libgtk-vnc-2.0-0
  libgtk-vnc-1.0-0
  libgtk-3-0
  libgoocanvas3
  libgnomekbd7
  libgnome-desktop-3-2
  libgnome-desktop-2-17
  libgladeui-2-0
  libgksu2-0
  libgimp2.0
  libgegl-0.0-0
  libgdu-gtk0
  libgdraw4
  libgdiplus
  libgcr-3-1
  libgcj12-awt
  libevolution
  libevince3-3
  libedataserverui-3.0-1
  libcogl-pango0
  libclutter-gtk-1.0-0
  libclutter-1.0-0
  libcairomm-1.0-1
  libcairo2-dev
  libcairo2-dbg
  libcairo-script-interpreter2
  libcairo-perl
  libcairo-gobject2
  libbrasero-media3-1
  libbonoboui2-dev
  libbonoboui2-0
  ldm
  inkscape
  indicator-sound
  indicator-session
  indicator-printers
  indicator-messages
  indicator-datetime
  gwibber
  gucharmap
  gtk3-engines-unico
  gtk3-engines-oxygen
  gtk2.0-examples
  gtk2-engines-oxygen
  gtk2-engines-murrine
  gtk2-engines
  gtk-3-examples
  gstreamer0.10-x
  gstreamer0.10-plugins-good
  gnomine
  gnome-system-monitor
  gnome-settings-daemon
  gnome-session-bin
  gnome-screenshot
  gnome-screensaver
  gnome-power-manager
  gnome-nettool
  gnome-font-viewer
  gnome-control-center
  gimp
  gedit
  firefox
  file-roller
  evolution-plugins
  evince
  eog
  dia-libs
  dia-gnome
  compiz-plugins-main-default
  compiz-plugins-main
  compiz-plugins
  compiz-gnome
  brasero
  baobab
  aisleriot
  activity-log-manager-control-center
```What rdepends means is that all these things depend at some point on libcairo2.  Assuming that these rdepends are the same on Quantal (and the probably are, except for removed packages), downgrading can have serious repercussions for all the software listed on this system.  So while downgrading may repair this issue for you guys, you're now: (1) unable to get bug reports filed for the software i just listed because you're using older libraries using ubuntu-bug, (2) making a HUGE list of potential problems for newer software using older libraries (because functionality likely depends on the newer libraries), and (3) diverging somewhat from the release of Ubuntu you are on.

**This type of workaround is ill-advised.  As a member of Bug Squad and Bug Control, I do *not* suggest you downgrade your libraries as you did here by hand, since it can introduce a whole mess of other bugs.**

**DONE**

That's a very fair point.  What do you recommend?

Somebody else found a workaround which lets you use the latest libcairo libraries as long as you disable the render extension on the NX client.  The problem I found is that it's so sluggish as to be almost unusable :(

---

### Post by gambit73 on 2013-02-26
If anyone is interested, I solved this issue by installing the Raring Ringtail version of libcairo and libcairo-gobject2, combined with one dependency update of libpixman.

Cairo debs found here:
[https://launchpad.net/ubuntu/+source/cairo](https://launchpad.net/ubuntu/+source/cairo)
and the libpixman deb here:
[https://launchpad.net/ubuntu/raring/i386/libpixman-1-0/0.28.2-0ubuntu1](https://launchpad.net/ubuntu/raring/i386/libpixman-1-0/0.28.2-0ubuntu1)

Install the three debs and restart nxserver.

Hope this will help some.

Imar.

---

### Post by Zoide7777 on 2013-02-26
> **gambit73 said:**
> If anyone is interested, I solved this issue by installing the Raring Ringtail version of libcairo and libcairo-gobject2, combined with one dependency update of libpixman.

Cairo debs found here:
[https://launchpad.net/ubuntu/+source/cairo](https://launchpad.net/ubuntu/+source/cairo)
and the libpixman deb here:
[https://launchpad.net/ubuntu/raring/i386/libpixman-1-0/0.28.2-0ubuntu1](https://launchpad.net/ubuntu/raring/i386/libpixman-1-0/0.28.2-0ubuntu1)

Install the three debs and restart nxserver.

Hope this will help some.

Imar.

Thanks for the links!  Here's the reason for the fix:

[[https://bugs.eclipse.org/bugs/show_bug.cgi?id=386955#c22](https://bugs.eclipse.org/bugs/show_bug.cgi?id=386955#c22)]

"It's a problem with cairo and described here: [http://permalink.gmane.org/gmane.comp.lib.cairo/23403](http://permalink.gmane.org/gmane.comp.lib.cairo/23403)
Basically cairo ignores that NX does not support libxender < 0.11. It might do so again in the future: Last section of "Bug fixes": [http://www.cairographics.org/news/cairo-1.12.10/](http://www.cairographics.org/news/cairo-1.12.10/)"

You can actually install quantal-labeled packages from PPA repos, as long as it's >= cairo-1.12.10.

But it just so happens that in the official repos the quantal packages only go up to 1.12.2, so you may have to use the ones from raring, which are currently at version 1.12.14.

Here are the Ubuntu packages for libcairo2: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libcairo2&searchon=names](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libcairo2&searchon=names)
And the Ubuntu packages for libcairo-gobject2: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libcairo-gobject2&searchon=names](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libcairo-gobject2&searchon=names)

---

### Post by nito2 on 2014-01-14
For anyone interesed in 13.10 with libcairo2 version 1.12.16-0ubuntu2

After exploring 

[http://cgit.freedesktop.org/cairo/tree/src/cairo-xlib-display.c?id=1.12.16#n217](http://cgit.freedesktop.org/cairo/tree/src/cairo-xlib-display.c?id=1.12.16#n217)

And 

nito@qvd-vm:~ $ 
xdpyinfo -queryExtensions -ext RENDER | grep -i render
    RENDER  (opcode: 149, base error: 167)
RENDER version 0.10 opcode: 149, base error: 167
  Render formats :
nito@qvd-vm:~ $ 


It worked for me setting the environment variable before launching the Xsession 

export CAIRO_DEBUG=xrender-version=0.9

(not debugged why 0.10 didn't work).

---

