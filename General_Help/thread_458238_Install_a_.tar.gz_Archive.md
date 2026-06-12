---
title: "Install a .tar.gz Archive"
date: 2007-05-29
forum: General Help
---

### Post by RelativelyQuantum on 2007-05-29
Hi all.

I have a quick question concerning .tar.gz archives. I have downloaded a number of them lately, but being comparatively new to Ubuntu do not know how to install their contents. Any help would be appreciated.

---

### Post by meng on 2007-05-29
Start by telling us what it is that you want to install. If it's something that is already in the Ubuntu repositories, then you're likely wasting your time by installing from source (that's what is in the .tar.gz files).

---

### Post by RelativelyQuantum on 2007-05-29
I'm actually trying to install Cwiid, a driver which allows interface via the Nintendo Wii controller. I searched for it using Synaptics, but found nothing. The exact filename is cwiid-0.5.03, and is a .tgz file. I thought is might install similarly to a .tar.gz, which is the one I hear about more frequently.

---

### Post by taurus on 2007-05-29
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf cwiid-0.5.03.tgz
cd cwiid-0.5.03
```
and look at either INSTALL or README on how to build/install it on your machine.

```
more INSTALL
```
Otherwise, post the output of this command here.

---

### Post by RelativelyQuantum on 2007-05-29
I navigated to the unpackaged folder, but when I typed "./configure" as it said to in INSTALL, I got this:
```

reece@Mycroft:~/Desktop/cwiid-0.5.03$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Not sure what that means...I had read that I needed to install *build-essential*, but can't do that since I do not have my installation CD at current.

---

### Post by taurus on 2007-05-29
You need the build-essential package before you can build anything from source.

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo checkinstall
```

---

### Post by RelativelyQuantum on 2007-05-29
Is there any way to install build-essential without my installation cd?

---

### Post by meng on 2007-05-29
Sure, you'd need an internet connection though. Just use Synaptic Package Manager, but before you select anything to install, go to Repositories and uncheck the CD. Then it will be forced to install from the intar-web!

---

### Post by RelativelyQuantum on 2007-05-29
OK, I'll try that. Thanks ALOT! This cd problem was driving me crazy.

---

### Post by RelativelyQuantum on 2007-05-29
Alright:

```
reece@Mycroft:~/Desktop/cwiid-0.5.03$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... no
checking for mawk... mawk
checking for flex... no
checking for lex... no
configure: error: flex not found
```

"flex not found"?

---

### Post by meng on 2007-05-29
Well, some progress made anyway.
Try "sudo apt-get install flex"
and then try configuring again.

---

### Post by RelativelyQuantum on 2007-05-29
Alright, now I have this:

```
reece@Mycroft:~/Desktop/cwiid-0.5.03$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... gawk
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for pthread_create in -lpthread... yes
checking for hci_devid in -lbluetooth... yes
checking for dlopen in -ldl... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdint.h... (cached) yes
checking bluetooth/bluetooth.h usability... yes
checking bluetooth/bluetooth.h presence... yes
checking for bluetooth/bluetooth.h... yes
checking for bluetooth/l2cap.h... yes
checking for bluetooth/hci.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking for linux/uinput.h... yes
checking for library containing strerror... none required
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.0.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

No idea what to do from here. I can't find the pkg-config file. Help!

---

### Post by meng on 2007-05-29
Try installing gtk+-2.0, and gthread-2.0
(I don't know if they come installed by default, or not.)

---

### Post by RelativelyQuantum on 2007-05-29
I tried to install those using synaptics, but they were not listed. Until I find out definitively what the problem is, I think I'll try to unpack the other program which does something similar. That's a .tar.gz archive, which would presumably be easier to deal with. Thanks for all the help, in any case; I really appreciate it :D

---

### Post by prankst3r on 2007-05-29
> **meng said:**
> Try installing gtk+-2.0, and gthread-2.0
(I don't know if they come installed by default, or not.)

I think you will need to install libgtk2.0-0 and libpthread2:
```
sudo aptitude install libgtk2.0-0 libpthread2
```

---

### Post by donteatthefish on 2007-05-29
i started trying to install this 2 days ago... and i couldn't do it.  this solution has solved all of my problems, thank you for helping us both :)

ok well now i cant run uinput...

---

### Post by RelativelyQuantum on 2007-05-30
I positively have those installed, as I just ran

```
sudo aptitude remove libgtk2.0-0 libpthread2
```

This was the output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  at-spi bluez-pin bug-buddy celestia-gnome compiz-gnome compiz-gtk 
  compiz-plugins contact-lookup-applet deskbar-applet desktop-effects ekiga 
  eog evince evolution evolution-exchange evolution-plugins 
  evolution-webcal f-spot file-roller firefox firefox-gnome-support 
  flashplugin-nonfree gaim gcalctool gconf-editor gcursor gdm gedit gimp 
  gimp-print gimp-python gksu gnome-about gnome-applets gnome-bluetooth 
  gnome-control-center gnome-cups-manager gnome-games gnome-keyring 
  gnome-keyring-manager gnome-mag gnome-media gnome-mount 
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session 
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-utils gnome-volume-manager gstreamer0.10-plugins-good gthumb 
  gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtk2.0-examples 
  gtkhtml3.14 gucharmap libatspi1.0-0 libbonoboui2-0 libedataserverui1.2-8 
  libeel2-2 libexchange-storage1.2-3 libgail-common libgail-gnome-module 
  libgail18 libgdl-1-0 libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0 
  libglade2.0-cil libgnome-desktop-2 libgnome-window-settings1 
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomebt0 
  libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomekbd1 libgnomekbdui1 
  libgnomeprintui2.2-0 libgnomeui-0 libgpod1 libgtk2-perl libgtk2.0-bin 
  libgtk2.0-cil libgtk2.0-common libgtkglext1 libgtkhtml2-0 
  libgtkhtml3.14-19 libgtksourceview1.0-0 libgtkspell0 libgucharmap6 
  libgutenprintui2-1 liblaunchpad-integration0 liblpint-bonobo0 
  libmetacity0 libnautilus-burn4 libnautilus-extension1 libnotify1 
  libpanel-applet2-0 libpoppler1-glib librsvg2-2 librsvg2-common libsexy2 
  libslab0 libtotem-plparser1 libvte9 libwnck18 libwxgtk2.6-0 metacity 
  nautilus nautilus-cd-burner nautilus-sendto network-manager-gnome 
  notification-daemon openoffice.org-core openoffice.org-gtk python-glade2 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gtk2 python-gtkhtml2 python-vte rhythmbox scim 
  scim-gtk2-immodule scim-modules-table sound-juicer ssh-askpass-gnome 
  synaptic tomboy totem-gstreamer tsclient update-notifier vino xsane 
  xscreensaver-data xscreensaver-gl yelp zenity 
The following packages will be REMOVED:
  libgtk2.0-0 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5501kB will be freed.
The following packages have unmet dependencies:
  gnome-keyring: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  f-spot: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomecupsui1.0-1c2a: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtk2.0-common: Depends: libgtk2.0-0 but it is not installable
  libgnomekbd1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  liblaunchpad-integration0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  tomboy: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  evolution-webcal: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  ekiga: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gimp-print: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  notification-daemon: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gcalctool: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gthumb: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgail18: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  openoffice.org-core: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gnome2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-nettool: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  scim-modules-table: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-media: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  metacity: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  nautilus: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgail-gnome-module: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libglade2.0-cil: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  xsane: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gnome2-extras: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gucharmap: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gnomecanvas: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  zenity: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgksuui1.0-1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-games: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgail-common: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  xscreensaver-gl: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  evolution-exchange: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-bluetooth: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  evolution: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libwxgtk2.6-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  openoffice.org-gtk: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  desktop-effects: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-power-manager: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libexchange-storage1.2-3: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-screensaver: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-mag: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtksourceview1.0-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  rhythmbox: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  compiz-gtk: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gedit: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gtk2-engines-pixbuf: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-control-center: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libbonoboui2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnome2-perl: Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
  gnome-pilot-conduits: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libnotify1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-pilot: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  scim: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  update-notifier: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  celestia-gnome: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgpod1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gstreamer0.10-plugins-good: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-terminal: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  network-manager-gnome: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gtkhtml3.14: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libpanel-applet2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libpoppler1-glib: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnome2.0-cil: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gtkhtml2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libwnck18: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  scim-gtk2-immodule: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libsexy2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-utils: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgutenprintui2-1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  compiz-plugins: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libatspi1.0-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  firefox: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-about: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-volume-manager: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  nautilus-cd-burner: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gtk2-engines: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomekbdui1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  eog: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gdm: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libslab0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomecanvas2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-glade2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gtk2-engines-ubuntulooks: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtk2.0-bin: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-spell: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  bug-buddy: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtk2.0-cil: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-vte: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libvte9: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomeui-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtk2-perl: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  at-spi: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  tsclient: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gaim: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  vino: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-keyring-manager: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-system-monitor: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  firefox-gnome-support: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libglade2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  evince: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtkhtml2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  evolution-plugins: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libedataserverui1.2-8: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gtk2.0-examples: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  totem-gstreamer: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  contact-lookup-applet: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnome-window-settings1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  flashplugin-nonfree: Depends: libgtk2.0-0 but it is not installable
  libmetacity0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gimp: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  liblpint-bonobo0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgimp2.0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  yelp: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  synaptic: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gksu: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libeel2-2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-netstatus-applet: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  librsvg2-2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgucharmap6: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgksu2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-applets: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gcursor: Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
  gconf-editor: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libtotem-plparser1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-system-tools: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomebt0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtkspell0: Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
  gnome-panel: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  deskbar-applet: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libnautilus-burn4: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gnome2-desktop: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libnautilus-extension1: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-mount: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-session: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnome-desktop-2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtkglext1: Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
  librsvg2-common: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  python-gtk2: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  xscreensaver-data: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnomeprintui2.2-0: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgdl-1-0: Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
  bluez-pin: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgnome2-canvas-perl: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  libgtkhtml3.14-19: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gimp-python: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  file-roller: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  compiz-gnome: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  nautilus-sendto: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  gnome-cups-manager: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  ssh-askpass-gnome: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
  sound-juicer: Depends: libgtk2.0-0 (>= 2.10.3) but it is not installable
Resolving dependencies...
open: 3532; closed: 3013; defer: 0; conflict/break: 2                          oThe following actions will resolve these dependencies:

Remove the following packages:
alacarte
apport-gtk
at-spi
bluez-pin
brltty-x11
bug-buddy
celestia-gnome
compiz
compiz-gnome
compiz-gtk
compiz-plugins
contact-lookup-applet
deskbar-applet
desktop-effects
drpython
ekiga
eog
evince
evolution
evolution-exchange
evolution-plugins
evolution-webcal
f-spot
file-roller
firefox
firefox-gnome-support
flashplugin-nonfree
gaim
gcalctool
gconf-editor
gcursor
gdebi
gdm
gedit
gimp
gimp-print
gimp-python
gksu
gnome-about
gnome-accessibility-themes
gnome-app-install
gnome-applets
gnome-bluetooth
gnome-btdownload
gnome-control-center
gnome-cups-manager
gnome-games
gnome-icon-theme
gnome-keyring
gnome-keyring-manager
gnome-mag
gnome-media
gnome-menus
gnome-mount
gnome-netstatus-applet
gnome-nettool
gnome-orca
gnome-panel
gnome-pilot
gnome-pilot-conduits
gnome-power-manager
gnome-screensaver
gnome-session
gnome-spell
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-themes
gnome-user-guide
gnome-utils
gnome-volume-manager
gstreamer0.10-plugins-good
gthumb
gtk2-engines
gtk2-engines-pixbuf
gtk2-engines-ubuntulooks
gtk2.0-examples
gtkhtml3.14
gucharmap
hal-device-manager
human-theme
hwdb-client-gnome
kicad
language-selector
language-support-en
libatspi1.0-0
libbonoboui2-0
libedataserverui1.2-8
libeel2-2
libexchange-storage1.2-3
libgail-common
libgail-gnome-module
libgail18
libgdl-1-0
libgdl-1-common
libgimp2.0
libgksu2-0
libgksuui1.0-1
libglade2-0
libglade2.0-cil
libgnome-desktop-2
libgnome-keyring0
libgnome-window-settings1
libgnome2-canvas-perl
libgnome2-perl
libgnome2.0-cil
libgnomebt0
libgnomecanvas2-0
libgnomecupsui1.0-1c2a
libgnomekbd1
libgnomekbdui1
libgnomeprintui2.2-0
libgnomeui-0
libgpod1
libgtk2-perl
libgtk2.0-bin
libgtk2.0-cil
libgtk2.0-common
libgtkglext1
libgtkhtml2-0
libgtkhtml3.14-19
libgtksourceview1.0-0
libgtkspell0
libgucharmap6
libgutenprintui2-1
liblaunchpad-integration0
liblpint-bonobo0
libmetacity0
libnautilus-burn4
libnautilus-extension1
libnotify1
libpanel-applet2-0
libpoppler1-glib
librsvg2-2
librsvg2-common
libsexy2
libslab0
libtotem-plparser1
libvte9
libwnck18
libwxgtk2.6-0
metacity
mozilla-firefox-locale-en-gb
nautilus
nautilus-cd-burner
nautilus-sendto
network-manager-gnome
notification-daemon
onboard
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-filter-mobiledev
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-java-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-style-andromeda
openoffice.org-style-default
openoffice.org-style-human
openoffice.org-style-industrial
openoffice.org-thesaurus-en-us
openoffice.org-writer
python-at-spi
python-glade2
python-gnome2
python-gnome2-desktop
python-gnome2-extras
python-gnomecanvas
python-gtk2
python-gtkhtml2
python-launchpad-integration
python-notify
python-uno
python-vte
python-wxgtk2.6
restricted-manager
rhythmbox
scim
scim-gtk2-immodule
scim-modules-table
scim-tables-additional
screensaver-default-images
serpentine
software-properties-gtk
sound-juicer
ssh-askpass-gnome
synaptic
tangerine-icon-theme
tango-icon-theme-common
thunderbird-locale-en-gb
tomboy
totem
totem-gstreamer
totem-mozilla
tsclient
ubuntu-artwork
ubuntu-desktop
ubuntu-docs
update-manager
update-notifier
vino
xsane
xscreensaver-data
xscreensaver-gl
yelp
zenity

Downgrade the following packages:
capplets-data [1:2.18.1-0ubuntu2.1 (feisty-updates, now) -> 1:2.18.1-0ubuntu2
(feisty)]

Leave the following dependencies unresolved:
capplets-data recommends gnome-control-center (>= 1:2.18.1-0ubuntu2)
compiz-core recommends compiz-plugins (= 1:0.3.6-1ubuntu13)
evolution-common recommends evolution
gaim-data recommends gaim
gconf2 recommends libgtk2.0-0
gimp-data recommends gimp
gnome-games-data recommends gnome-games
gnome-media-common recommends gnome-media
gnome-terminal-data recommends gnome-terminal
language-pack-en-base recommends language-support-en
language-pack-gnome-en-base recommends language-support-en
libeel2-data recommends libeel2-2
libgnomeprintui2.2-common recommends gnome-icon-theme
nautilus-data recommends nautilus
network-manager recommends network-manager-gnome | network-manager-kde
xsane-common recommends xsane
kicad-common recommends kicad
gnome-panel-data recommends gnome-panel
Score is -79095

```

Since it would need to remove just about every *single* one of my applications, I assume that it's somewhere in my program files. It also said something about modifying other system files:

```
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

That graphical interface is looking *really* good right about now.

---

