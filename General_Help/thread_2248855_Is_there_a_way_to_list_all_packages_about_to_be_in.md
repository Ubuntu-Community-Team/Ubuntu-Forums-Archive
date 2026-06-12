---
title: "Is there a way to list all packages about to be installed as a dependency?"
date: 2014-10-17
forum: General Help
---

### Post by CaptainMark on 2014-10-17
When installing a new package is there an easy way to obtain a list of new packages that will be installed as dependencies? Much like apt-get does when asking "if you're sure you want to install?" but without the all the special formatting and newline characters?

Note I don't want all dependencies, just ones that are about to be pulled in to install that are new. 
The reason is I want to try out some new desktops and they often pull in hundreds of dependencies which will remain even if you uninstall the desktop package and use auto-remove, getting a list of new packages means I can remove them all easily and revert all changes.

Regards
Mark

---

### Post by nerdtron on 2014-10-17
I think you are looking for the "apt-get autoremove" command. See the #25 command here [http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/](http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/)

---

### Post by papibe on 2014-10-17
Hi CaptainMark.

This may work for you (it gets the full name of the packages with versions).

Let's say you want to install 'nemo':
```
$ apt-get install --print-uris -qq nemo | awk '{print $2}'

libnemo-extension1_1.8.4-1.1_amd64.deb
nemo-data_1.8.4-1.1_all.deb
nemo_1.8.4-1.1_amd64.deb
nemo-fileroller_1.8.0-1_amd64.deb

```
Hope it helps. Let us know if that is what you are looking for.
Regards.

---

### Post by matt_symes on 2014-10-17
Hi

I generally use this. You can pipe it into another command if you just want the installed packages.

```
sudo apt-get install --assume-no unity
```

BTW: The above command install 223 packages.

> 0 to upgrade, 223 to newly install, 0 to remove and 0 not to upgrade.

Kind regads

---

### Post by oldos2er on 2014-10-17
```
apt-cache show <package>
``` lists dependencies, including recommended ones and suggested ones. ```
sudo apt-get install --no-install-recommends
 <package>
``` is what you're looking for if I'm understanding you correctly.

---

### Post by CantankRus on 2014-10-18
I think I understand what you mean.
When you install something like lubuntu-desktop you get a block of formatted text showing new packages but you want these packages all in one line to save if you decide to remove.
eg
```
glen@Trusty:~$ sudo apt-get install lubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  liblightdm-qt-3-0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  audacious audacious-plugins audacious-plugins-data blueman bluez-cups cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-driver-gutenprint cups-filters cups-filters-core-drivers cups-ppdc
  cups-server-common ffmpegthumbnailer fonts-lyx galculator gecko-mediaplayer
  gnome-desktop-data gnome-mplayer gnome-system-tools gnumeric gnumeric-common
  gnumeric-doc gpicview gtk2-engines guvcview hardinfo hplip
  indicator-application-gtk2 leafpad libabiword-3.0 libaudcore1 libbinio1ldbl
  libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libdiscid0
  libffmpegthumbnailer4 libgda-5.0-4 libgda-5.0-common libgdome2-0
  libgdome2-cpp-smart0c2a libgmlib1 libgmtk1 libgmtk1-data libgoffice-0.10-10
  libgoffice-0.10-10-common libgtkmathview0c2a libguess1 libgutenprint2
  liblink-grammar4 libloudmouth1-0 libmowgli2 libmusicbrainz3-6 libonig2
  liboobs-1-5 libopts25 libots0 libpisock9 libsidplayfp libuniconf4.6
  libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras
  light-locker light-locker-settings lightdm-gtk-greeter
  link-grammar-dictionaries-en lubuntu-artwork lubuntu-artwork-14-04
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-icon-theme lubuntu-lxpanel-icons lubuntu-software-center
  lxappearance lxappearance-obconf lxinput lxlauncher
  lxpanel-indicator-applet-plugin lxrandr lxsession-default-apps lxshortcut
  lxtask lxterminal ntp pidgin pidgin-data pidgin-libnotify
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text
  printer-driver-foo2zjs printer-driver-gutenprint printer-driver-hpcups
  printer-driver-postscript-hp printer-driver-pxljr printer-driver-splix
  python-gudev python-pysqlite2 sylpheed sylpheed-doc sylpheed-i18n
  sylpheed-plugins system-config-printer-gnome system-tools-backends
  transmission uvcdynctrl uvcdynctrl-data wvdial xfburn xfce4-power-manager
  xfce4-power-manager-data xfonts-100dpi xpad
Suggested packages:
  cups-pdf xpp gnumeric-plugins-extra docbook-xsl hplip-gui hplip-doc
  system-config-printer evince-gtk libdiscid0-dbg libgda-5.0-bin
  libgda-5.0-mysql libgda-5.0-postgres libgmlib1-dbg libgmtk1-dbg
  gutenprint-locales jpilot pilot-link kpilot gnome-pilot evolution claws-mail
  sidplay2fp amixer xscreensaver indicator-messages-gtk2 indicator-sound-gtk2
  ntp-doc evolution-data-server psutils hannah-foo2zjs gutenprint-doc
  python-pysqlite2-doc python-pysqlite2-dbg claws-mail-tools bogofilter
  bsfilter xfce4-power-manager-plugins udisks
The following packages will be REMOVED:
  cups-filters-core-drivers:i386 libgutenprint2:i386 lpr
The following NEW packages will be installed:
  [COLOR="#FF0000"]abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  audacious audacious-plugins audacious-plugins-data blueman bluez-cups cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-driver-gutenprint cups-filters cups-filters-core-drivers cups-ppdc
  cups-server-common ffmpegthumbnailer fonts-lyx galculator gecko-mediaplayer
  gnome-desktop-data gnome-mplayer gnome-system-tools gnumeric gnumeric-common
  gnumeric-doc gpicview gtk2-engines guvcview hardinfo hplip
  indicator-application-gtk2 leafpad libabiword-3.0 libaudcore1 libbinio1ldbl
  libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libdiscid0
  libffmpegthumbnailer4 libgda-5.0-4 libgda-5.0-common libgdome2-0
  libgdome2-cpp-smart0c2a libgmlib1 libgmtk1 libgmtk1-data libgoffice-0.10-10
  libgoffice-0.10-10-common libgtkmathview0c2a libguess1 libgutenprint2
  liblink-grammar4 libloudmouth1-0 libmowgli2 libmusicbrainz3-6 libonig2
  liboobs-1-5 libopts25 libots0 libpisock9 libsidplayfp libuniconf4.6
  libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras
  light-locker light-locker-settings lightdm-gtk-greeter
  link-grammar-dictionaries-en lubuntu-artwork lubuntu-artwork-14-04
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-desktop lubuntu-icon-theme lubuntu-lxpanel-icons
  lubuntu-software-center lxappearance lxappearance-obconf lxinput lxlauncher
  lxpanel-indicator-applet-plugin lxrandr lxsession-default-apps lxshortcut
  lxtask lxterminal ntp pidgin pidgin-data pidgin-libnotify
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text
  printer-driver-foo2zjs printer-driver-gutenprint printer-driver-hpcups
  printer-driver-postscript-hp printer-driver-pxljr printer-driver-splix
  python-gudev python-pysqlite2 sylpheed sylpheed-doc sylpheed-i18n
  sylpheed-plugins system-config-printer-gnome system-tools-backends
  transmission uvcdynctrl uvcdynctrl-data wvdial xfburn xfce4-power-manager
  xfce4-power-manager-data xfonts-100dpi xpad[/COLOR]
0 to upgrade, 126 to newly install, 3 to remove and 0 not to upgrade.
Need to get 48.5 MB/53.8 MB of archives.
After this operation, 201 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```
I found that if you highlight the packages with left mouse then save the clipboard buffer to a file using xsel, the formating is removed.

ie highlight the text block of new packages then run....
```
echo $(xsel) >> notes.txt
```
Saves to **~/notes.txt**

If you want the formatting, enclose **$(xsel)** in double quotes.

I discovered this by accident because I already had a quicklist item to add the clipboard to a notes file.
Need to install xsel.

---

### Post by ian-weisser on 2014-10-18
All dependencies:
```
apt-cache depends <packagename>
```

What will be installed (all dependencies minus what is already installed)
```
apt-get install --simulate <packagename>
```

Sorry, I don't know of any better formatting options without doing a lot of script-fu and making lots of individual dpkg database lookups.

If you discover orphaned packages that are:
1) Not autoremoved by 'autoremove',
2) Were not part of the original hardware install (those are ineligble for autoremoval - apt-mark set to 'manual'), and
3) Are not a dependency of the current running kernel,
then please file a bug report.

---

