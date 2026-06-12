---
title: "upgrade switch to 64 bit ubuntu from 32 bit?"
date: 2012-12-04
forum: General Help
---

### Post by sdowney717 on 2012-12-04
I currently run 32 bit ubuntu 12.04
Can I switch to 64 bit and how to do it?

I can run 64 bit win7 on this pc

Interested in trying chromeOS but it is only 64 bit
[http://www.omgubuntu.co.uk/2012/11/how-to-run-chromeos-in-ubuntu](http://www.omgubuntu.co.uk/2012/11/how-to-run-chromeos-in-ubuntu)

---

### Post by sdowney717 on 2012-12-04
[http://www.ehow.com/how_6779551_update-32-64-bit-ubuntu.html](http://www.ehow.com/how_6779551_update-32-64-bit-ubuntu.html)
here is a suggestion.

Ok if you backed up with tar/ 
What are you getting?
then what are you restoring?

---

### Post by oldos2er on 2012-12-04
That link makes no sense to me--you back up your entire current 32-bit installation, install 64-bit, then un-tar your old 32-bit backup over it? Backing up your /home/user settings and configs would make far more sense.

---

### Post by oldfred on 2012-12-05
The settings in /home is most of it. If you made any custom system wide settings for grub, Internet, video  those may be in /etc. But sometimes with a new install the old settings may conflict so I do not automatically copy those back.

You also want to make a list of installed applications to easily reinstall the 64 bit versions.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
Oldfred only plans a total reinstall as his backup plan so he backs up what he thinks he needs.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

    
       Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

    
       More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by sdowney717 on 2012-12-05
interesting idea to get packages

So how do you handle the ubuntu addon's from other software sources?
Can you keep the software sources? For example I have cinammon desktop

here is a list of my packages
```
accountsservice					install
acl						install
acpi-support					install
acpid						install
activity-log-manager-common			install
activity-log-manager-control-center		install
adduser						install
adium-theme-ubuntu				install
aisleriot					install
akonadi-backend-mysql				install
akonadi-server					install
alacarte					install
alien						install
alsa-base					install
alsa-utils					install
anacron						install
apache2.2-bin					install
apg						install
app-install-data				install
app-install-data-partner			install
apparmor					install
apparmor-utils					install
appmenu-gtk					install
appmenu-gtk3					install
appmenu-qt					install
apport						install
apport-gtk					install
apport-hooks-medibuntu				deinstall
apport-symptoms					install
apt						install
apt-transport-https				install
apt-utils					install
apt-xapian-index				install
aptdaemon					install
aptdaemon-data					install
apturl						install
apturl-common					install
arj						install
aspell						install
aspell-en					install
at						install
at-spi						deinstall
at-spi2-core					install
autotools-dev					install
avahi-autoipd					install
avahi-daemon					install
avahi-utils					install
bamfdaemon					install
banshee						install
banshee-extension-soundmenu			install
baobab						install
base-files					install
base-passwd					install
bash						install
bash-completion					install
bc						install
bind9-host					install
binfmt-support					install
binutils					install
bison						install
blender						install
bluez						install
bluez-alsa					install
bluez-cups					install
bluez-gstreamer					install
bogofilter					install
bogofilter-bdb					install
bogofilter-common				install
branding-ubuntu					install
brasero						install
brasero-cdrkit					install
brasero-common					install
brltty						install
brltty-x11					install
bsd-mailx					install
bsdmainutils					install
bsdutils					install
build-essential					install
busybox-initramfs				install
busybox-static					install
bzip2						install
c2esp						install
ca-certificates					install
ca-certificates-java				install
cabextract					install
capplets-data					deinstall
caribou						install
cdck						install
cdparanoia					install
cdrdao						install
checkbox					install
checkbox-gtk					install
checkbox-qt					install
cheese						install
cheese-common					install
cinnamon					install
cinnamon-applet-screenshotandrecording		install
cinnamon-applet-utilitiesmenu			install
cinnamon-applet-windowiconlist			install
cinnamon-extension-weather			deinstall
clementine					install
cli-common					install
cmap-adobe-japan1				install
cmap-adobe-japan2				install
colord						install
comerr-dev					install
command-not-found				install
command-not-found-data				install
compiz						install
compiz-core					install
compiz-gnome					install
compiz-plugins					install
compiz-plugins-default				install
compiz-plugins-main				install
compiz-plugins-main-default			install
compizconfig-backend-gconf			install
computer-janitor				install
computer-janitor-gtk				install
console-setup					install
consolekit					install
coreutils					install
cpio						install
cpp						install
cpp-4.5						install
cpp-4.6						install
crda						install
cron						install
cryptsetup-bin					install
cups						install
cups-bsd					install
cups-client					install
cups-common					install
cups-driver-gutenprint				install
cups-filters					install
cups-pk-helper					install
cups-ppdc					install
curl						install
darktable					install
darktable-plugins-experimental			install
dash						install
dbus						install
dbus-x11					install
dc						install
dconf-gsettings-backend				install
dconf-service					install
dconf-tools					install
debconf						install
debconf-i18n					install
debhelper					install
debianutils					install
defoma						install
deja-dup					install
desktop-file-utils				install
desktop-webmail					install
dh-apparmor					install
dictionaries-common				install
diffstat					install
diffutils					install
dkms						install
dmidecode					install
dmsetup						install
dmucs						install
dmz-cursor-theme				install
dnsmasq-base					install
dnsutils					install
doc-base					install
docbook						install
docbook-dsssl					install
docbook-to-man					install
docbook-utils					install
docbook-xml					install
docbook-xsl					install
dolphin						install
dosfstools					install
dpkg						install
dpkg-dev					install
dragondisk					install
duplicity					install
dvd+rw-tools					install
e2fslibs					install
e2fsprogs					install
ed						install
eject						install
empathy						install
empathy-common					install
enchant						install
eog						install
esound-common					install
espeak						install
espeak-data					install
evince						install
evince-common					install
evolution					install
evolution-common				install
evolution-data-server				install
evolution-data-server-common			install
evolution-exchange				install
evolution-indicator				install
evolution-plugins				install
evolution-webcal				install
example-content					install
execstack					install
exiv2						install
fakeroot					install
ffmpeg						install
file						install
file-roller					install
findutils					install
firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install
flac						install
flashplugin-installer				install
flex						install
folks-common					install
fontconfig					install
fontconfig-config				install
fontforge					install
fonts-droid					install
fonts-horai-umefont				install
fonts-kacst					install
fonts-kacst-one					install
fonts-khmeros-core				install
fonts-lao					install
fonts-liberation				install
fonts-nanum					install
fonts-opensymbol				install
fonts-takao-pgothic				install
fonts-thai-tlwg					install
fonts-tlwg-garuda				install
fonts-tlwg-kinnari				install
fonts-tlwg-loma					install
fonts-tlwg-mono					install
fonts-tlwg-norasi				install
fonts-tlwg-purisa				install
fonts-tlwg-sawasdee				install
fonts-tlwg-typewriter				install
fonts-tlwg-typist				install
fonts-tlwg-typo					install
fonts-tlwg-umpush				install
fonts-tlwg-waree				install
fonts-unfonts-core				install
foo2zjs						install
foomatic-db-compressed-ppds			install
foomatic-db-engine				install
foomatic-filters				install
foxtrotgps					install
freedroidrpg					install
freedroidrpg-data				install
freepats					install
freespacenotifier				install
frei0r-plugins					install
friendly-recovery				install
ftp						install
fuse						install
fuse-utils					install
g++						install
g++-4.5						install
g++-4.6						install
galculator					install
gamin						install
gbrainy						install
gcalctool					install
gcc						install
gcc-4.5						install
gcc-4.5-base					install
gcc-4.6						install
gcc-4.6-base					install
gconf-defaults-service				install
gconf-editor					install
gconf-service					install
gconf-service-backend				install
gconf2						install
gconf2-common					install
gcr						install
gdb						install
gdm						install
gdm-guest-session				deinstall
gecko-mediaplayer				install
gedit						install
gedit-common					install
genisoimage					install
geoclue						install
geoclue-ubuntu-geoip				install
geoip-database					install
gettext						install
gettext-base					install
ghostscript					install
ghostscript-cups				install
ghostscript-x					install
giblib1						install
gimp						install
gimp-data					install
ginn						install
gir1.2-accountsservice-1.0			install
gir1.2-appindicator-0.1				install
gir1.2-appindicator3-0.1			install
gir1.2-atk-1.0					install
gir1.2-atspi-2.0				install
gir1.2-caribou-1.0				install
gir1.2-clutter-1.0				install
gir1.2-cogl-1.0					install
gir1.2-coglpango-1.0				install
gir1.2-dbusmenu-glib-0.4			install
gir1.2-dbusmenu-gtk-0.4				install
gir1.2-dee-1.0					install
gir1.2-folks-0.6				install
gir1.2-freedesktop				install
gir1.2-gconf-2.0				install
gir1.2-gdesktopenums-3.0			install
gir1.2-gdkpixbuf-2.0				install
gir1.2-gee-1.0					install
gir1.2-gjsdbus-1.0				install
gir1.2-gkbd-3.0					install
gir1.2-glib-2.0					install
gir1.2-gmenu-3.0				install
gir1.2-gnomebluetooth-1.0			install
gir1.2-gnomekeyring-1.0				install
gir1.2-gst-plugins-base-0.10			install
gir1.2-gstreamer-0.10				install
gir1.2-gtk-2.0					install
gir1.2-gtk-3.0					install
gir1.2-gtksource-3.0				install
gir1.2-gtop-2.0					install
gir1.2-gudev-1.0				install
gir1.2-indicate-0.7				install
gir1.2-javascriptcoregtk-3.0			install
gir1.2-json-1.0					install
gir1.2-launchpad-integration-3.0		install
gir1.2-muffin-3.0				install
gir1.2-mutter-3.0				install
gir1.2-nautilus-3.0				install
gir1.2-networkmanager-1.0			install
gir1.2-notify-0.7				install
gir1.2-panelapplet-4.0				install
gir1.2-pango-1.0				install
gir1.2-peas-1.0					install
gir1.2-polkit-1.0				install
gir1.2-rb-3.0					install
gir1.2-soup-2.4					install
gir1.2-telepathyglib-0.12			install
gir1.2-telepathylogger-0.2			install
gir1.2-totem-1.0				install
gir1.2-totem-plparser-1.0			install
gir1.2-ubuntuoneui-3.0				install
gir1.2-unity-5.0				install
gir1.2-upowerglib-1.0				install
gir1.2-vte-2.90					install
gir1.2-webkit-3.0				install
gir1.2-wnck-3.0					install
gir1.2-xkl-1.0					install
git						install
git-man						install
gjs						install
gkbd-capplet					install
gksu						install
glib-networking					install
glib-networking-common				install
glib-networking-services			install
gnome-accessibility-themes			install
gnome-applets					install
gnome-applets-data				install
gnome-bluetooth					install
gnome-contacts					install
gnome-control-center				install
gnome-control-center-data			install
gnome-desktop-data				install
gnome-desktop3-data				install
gnome-disk-utility				install
gnome-doc-utils					install
gnome-font-viewer				install
gnome-games-common				deinstall
gnome-games-data				install
gnome-icon-theme				install
gnome-icon-theme-full				install
gnome-icon-theme-symbolic			install
gnome-keyring					install
gnome-mag					install
gnome-media					install
gnome-menus					install
gnome-mime-data					install
gnome-mplayer					install
gnome-nettool					install
gnome-online-accounts				install
gnome-orca					install
gnome-panel					install
gnome-panel-bonobo				deinstall
gnome-panel-data				install
gnome-power-manager				install
gnome-screensaver				install
gnome-screenshot				install
gnome-search-tool				install
gnome-session					install
gnome-session-bin				install
gnome-session-canberra				install
gnome-session-common				install
gnome-session-fallback				install
gnome-settings-daemon				install
gnome-shell					install
gnome-shell-common				install
gnome-shell-extensions				install
gnome-shell-extensions-common			install
gnome-sudoku					install
gnome-system-log				install
gnome-system-monitor				install
gnome-system-tools				install
gnome-terminal					install
gnome-terminal-data				install
gnome-themes-standard				install
gnome-themes-ubuntu				install
gnome-tweak-tool				install
gnome-user-guide				install
gnome-user-share				install
gnome-utils-common				install
gnome-video-effects				install
gnomine						install
gnupg						install
google-chrome-beta				deinstall
google-chrome-stable				install
google-earth-stable				deinstall
google-musicmanager-beta			install
google-talkplugin				install
gparted						install
gpgv						install
gpicview					install
gpsbabel					install
gpsbabel-doc					install
gpsd						install
gpsd-clients					install
gpsd-dbg					install
gpsdrive					install
gpsdrive-data					install
gpsdrive-scripts				install
graphviz					install
grep						install
grive						install
groff-base					install
growisofs					install
grub-common					install
grub-gfxpayload-lists				install
grub-pc						install
grub-pc-bin					install
grub2-common					install
gs-cjk-resource					install
gsettings-desktop-schemas			install
gsfonts						install
gstreamer0.10-alsa				install
gstreamer0.10-ffmpeg				install
gstreamer0.10-fluendo-mp3			install
gstreamer0.10-gconf				install
gstreamer0.10-gnonlin				install
gstreamer0.10-nice				install
gstreamer0.10-plugins-bad			install
gstreamer0.10-plugins-bad-multiverse		install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good			install
gstreamer0.10-plugins-ugly			install
gstreamer0.10-pulseaudio			install
gstreamer0.10-tools				install
gstreamer0.10-x					install
gtk-recordmydesktop				install
gtk2-engines					install
gtk2-engines-murrine				install
gtk2-engines-pixbuf				install
gtk3-engines-unico				install
gucharmap					install
guile-1.8-libs					install
guile-2.0-libs					install
gvfs						install
gvfs-backends					install
gvfs-bin					install
gvfs-common					install
gvfs-daemons					install
gvfs-fuse					install
gvfs-libs					install
gwibber						install
gwibber-service					install
gwibber-service-facebook			install
gwibber-service-identica			install
gwibber-service-twitter				install
gzip						install
hal						install
hal-info					install
hdparm						install
hicolor-icon-theme				install
hostname					install
hpijs						install
hplip						install
hplip-cups					install
hplip-data					install
html2text					install
htop						install
huludesktop					install
humanity-icon-theme				install
hunspell-en-ca					install
hunspell-en-us					install
hwdata						install
hyphen-en-us					install
ibus						install
ibus-gtk					install
ibus-gtk3					install
ibus-pinyin					install
ibus-pinyin-db-android				install
ibus-table					install
icedtea-6-jre-cacao				install
icedtea-6-jre-jamvm				install
icedtea-7-jre-jamvm				install
icedtea-7-plugin				install
icedtea-netx					install
icedtea-netx-common				install
icoutils					install
ifupdown					install
im-switch					install
imagemagick					install
imagemagick-common				install
indicator-applet				deinstall
indicator-applet-complete			install
indicator-application				install
indicator-appmenu				install
indicator-datetime				install
indicator-messages				install
indicator-power					install
indicator-printers				install
indicator-session				install
indicator-sound					install
indicator-status-provider-mc5			install
indicator-ubuntuone				install
info						install
initramfs-tools					install
initramfs-tools-bin				install
initscripts					install
inputattach					install
insserv						install
install-info					install
insync-beta-ubuntu				install
intel-gpu-tools					install
intltool-debian					install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
irqbalance					install
isc-dhcp-client					install
isc-dhcp-common					install
iso-codes					install
iw						install
jadetex						install
java-common					install
jockey-common					install
jockey-gtk					install
k3b						install
k3b-data					install
k3b-extrathemes					install
kate-data					install
katepart					install
kazam						install
kbd						install
kde-baseapps-bin				install
kde-baseapps-data				install
kde-runtime					install
kde-runtime-data				install
kde-style-oxygen				install
kde-wallpapers-default				install
kde-window-manager				install
kde-window-manager-common			install
kde-workspace					install
kde-workspace-bin				install
kde-workspace-data				install
kde-workspace-kgreet-plugins			install
kdebase-runtime					install
kdelibs-bin					install
kdelibs5-data					install
kdelibs5-plugins				install
kdepasswd					install
kdepim-runtime					install
kdepimlibs-kio-plugins				install
kdm						install
kdoctools					install
kerneloops-daemon				install
keyboard-configuration				install
kfind						install
kinfocenter					install
klibc-utils					install
klipper						install
kmenuedit					install
konqueror					install
konqueror-nsplugins				install
konsole						install
krb5-locales					install
krb5-multidev					install
ksnapshot					install
ksysguard					install
ksysguardd					install
kubuntu-debug-installer				install
landscape-client-ui-install			install
language-pack-en				install
language-pack-en-base				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-selector-common			install
language-selector-gnome				install
language-support-en				install
language-support-writing-en			install
laptop-detect					install
launchpad-integration				install
leafpad						install
less						install
lftp						install
liba52-0.7.4					install
libaa1						install
libaacs0					install
libaccess-bridge-java-jni			deinstall
libaccountsservice0				install
libacl1						install
libakonadi-calendar4				install
libakonadi-contact4				install
libakonadi-kabc4				install
libakonadi-kcal4				install
libakonadi-kde4					install
libakonadi-kmime4				install
libakonadi-notes4				install
libakonadiprotocolinternals1			install
libalgorithm-diff-perl				install
libalgorithm-diff-xs-perl			install
libalgorithm-merge-perl				install
libamd2.2.0					install
libao-common					install
libao4						install
libapache2-mod-dnssd				install
libapparmor-perl				install
libapparmor1					install
libappindicator0.1-cil				install
libappindicator1				install
libappindicator3-1				install
libapr1						install
libaprutil1					install
libaprutil1-dbd-sqlite3				install
libaprutil1-ldap				install
libapt-inst1.3					deinstall
libapt-inst1.4					install
libapt-pkg-perl					install
libapt-pkg4.11					deinstall
libapt-pkg4.12					install
libarchive1					install
libarchive12					install
libart-2.0-2					install
libart2.0-cil					install
libasn1-8-heimdal				install
libasound2					install
libasound2-dev					install
libasound2-plugins				install
libaspell15					install
libass4						install
libasyncns0					install
libatasmart4					install
libatk-adaptor					install
libatk-adaptor-schemas				install
libatk-wrapper-java				install
libatk-wrapper-java-jni				install
libatk1.0-0					install
libatk1.0-data					install
libatkmm-1.6-1					install
libatm1						install
libatspi1.0-0					install
libatspi2.0-0					install
libattica0					deinstall
libattica0.3					install
libattr1					install
libaudio2					install
libaudiofile0					deinstall
libaudiofile1					install
libav-tools					install
libavahi-client-dev				install
libavahi-client3				install
libavahi-common-data				install
libavahi-common-dev				install
libavahi-common3				install
libavahi-core7					install
libavahi-glib1					install
libavahi-gobject0				install
libavahi-ui-gtk3-0				install
libavahi-ui0					install
libavc1394-0					install
libavcodec-extra-53				install
libavcodec52					deinstall
libavcodec53					deinstall
libavdevice53					install
libavfilter2					install
libavformat52					deinstall
libavformat53					install
libavifile-0.7c2				deinstall
libavutil-extra-51				install
libavutil50					deinstall
libavutil51					deinstall
libbabl-0.0-0					deinstall
libbabl-0.1-0					install
libbamf0					install
libbamf3-0					install
libbind9-60					deinstall
libbind9-80					install
libbison-dev					install
libblas3gf					install
libblkid1					install
libbluetooth3					install
libbluray1					install
libbonobo2-0					install
libbonobo2-common				install
libbonoboui2-0					install
libbonoboui2-common				install
libboost-filesystem1.46.1			install
libboost-program-options1.46.1			install
libboost-serialization1.42.0			deinstall
libboost-serialization1.46.1			install
libboost-system1.46.1				install
libbrasero-media1				deinstall
libbrasero-media3-1				install
libbrlapi0.5					install
libbsd0						install
libburn4					install
libbz2-1.0					install
libc-bin					install
libc-dev-bin					install
libc6						install
libc6-dbg					install
libc6-dev					install
libcaca0					install
libcairo-gobject2				install
libcairo-perl					install
libcairo2					install
libcairomm-1.0-1				install
libcamel-1.2-29					install
libcamel1.2-19					deinstall
libcanberra-gtk-module				install
libcanberra-gtk0				install
libcanberra-gtk3-0				install
libcanberra-gtk3-module				install
libcanberra-pulse				install
libcanberra0					install
libcap-ng0					install
libcap2						install
libcap2-bin					install
libcapi20-3					install
libcapi20-dev					install
libcaribou-common				install
libcaribou0					install
libcdaudio1					install
libcddb2					install
libcdio-cdda0					deinstall
libcdio-cdda1					install
libcdio-paranoia0				deinstall
libcdio-paranoia1				install
libcdio10					deinstall
libcdio13					install
libcdparanoia0					install
libcdt4						install
libcelt0-0					install
libcgraph5					install
libcheese-gtk21					install
libcheese3					install
libchromaprint0					install
libck-connector0				install
libclass-accessor-perl				install
libclass-factory-util-perl			install
libclass-isa-perl				install
libclass-load-perl				install
libclass-singleton-perl				install
libcln6						install
libclone-perl					install
libcloog-ppl0					install
libclucene0ldbl					install
libclutter-1.0-0				install
libclutter-1.0-common				install
libclutter-gst-1.0-0				install
libclutter-gtk-1.0-0				install
libclutter-imcontext-0.1-0			install
libcluttergesture-0.0.2-0			install
libcmis-0.2-0					install
libcogl-common					install
libcogl-pango0					install
libcogl5					deinstall
libcogl8					deinstall
libcogl9					install
libcolamd2.7.1					install
libcolord1					install
libcomerr2					install
libcompizconfig0				install
libconfig-inifiles-perl				install
libcroco3					install
libcrypt-passwdmd5-perl				install
libcryptsetup4					install
libcryptui0					deinstall
libcrystalhd3					install
libcups2					install
libcups2-dev					install
libcupscgi1					install
libcupsdriver1					install
libcupsfilters1					install
libcupsimage2					install
libcupsmime1					install
libcupsppdc1					install
libcurl3					install
libcurl3-gnutls					install
libcurl3-nss					install
libdaemon0					install
libdata-optlist-perl				install
libdate-manip-perl				install
libdatetime-format-builder-perl			install
libdatetime-format-iso8601-perl			install
libdatetime-format-strptime-perl		install
libdatetime-locale-perl				install
libdatetime-perl				install
libdatetime-timezone-perl			install
libdatrie1					install
libdb4.8					install
libdb5.1					install
libdbd-mysql-perl				install
libdbi-perl					install
libdbus-1-3					install
libdbus-1-dev					install
libdbus-glib-1-2				install
libdbus-glib1.0-cil				install
libdbus1.0-cil					install
libdbusmenu-glib3				deinstall
libdbusmenu-glib4				install
libdbusmenu-gtk3				deinstall
libdbusmenu-gtk3-4				install
libdbusmenu-gtk4				install
libdbusmenu-qt2					install
libdc1394-22					install
libdca0						install
libdconf-dbus-1-0				install
libdconf-qt0					install
libdconf0					install
libdecoration0					install
libdee-1.0-1					deinstall
libdee-1.0-4					install
libdevmapper-event1.02.1			install
libdevmapper1.02.1				install
libdigest-hmac-perl				install
libdirac-encoder0				install
libdirectfb-1.2-9				install
libdiscid0					install
libdjvulibre-text				install
libdjvulibre21					install
libdlrestrictions1				install
libdmapsharing-3.0-2				install
libdmtx0a					install
libdns69					deinstall
libdns81					install
libdotconf1.0					install
libdpkg-perl					install
libdrm-dev					install
libdrm-intel1					install
libdrm-nouveau1a				install
libdrm-nouveau2					install
libdrm-radeon1					install
libdrm2						install
libdv4						install
libdvbpsi7					install
libdvdcss2					install
libdvdnav-dev					install
libdvdnav4					install
libdvdread-dbg					install
libdvdread-dev					install
libdvdread4					install
libebackend-1.2-1				install
libebackend1.2-0				deinstall
libebml3					install
libebook-1.2-12					install
libebook1.2-10					deinstall
libebook1.2-12					deinstall
libecal-1.2-10					install
libecal1.2-10					deinstall
libecal1.2-8					deinstall
libechonest1.2					install
libedata-book-1.2-11				install
libedata-book1.2-8				deinstall
libedata-cal-1.2-13				install
libedata-cal1.2-10				deinstall
libedataserver-1.2-15				install
libedataserver1.2-14				deinstall
libedataserver1.2-15				deinstall
libedataserverui-3.0-1				install
libedataserverui1.2-11				deinstall
libedit2					install
libegroupwise1.2-13				deinstall
libelf1						install
libelfg0					install
libemail-valid-perl				install
libenca0					install
libenchant1c2a					install
libencode-locale-perl				install
libept1						deinstall
libept1.4.12					install
liberror-perl					install
libesd0						install
libespeak1					install
libevdocument3					deinstall
libevent-1.4-2					install
libevent-2.0-5					install
libevince3-3					install
libevolution					install
libevview3					deinstall
libexempi3					install
libexif-dev					install
libexif12					install
libexiv2-10					deinstall
libexiv2-11					install
libexpat1					install
libexpat1-dev					install
libexttextcat-data				install
libexttextcat0					install
libfaac0					install
libfaad2					install
libfarstream-0.1-0				install
libffi5						deinstall
libffi6						install
libfftw3-3					install
libfile-basedir-perl				install
libfile-copy-recursive-perl			install
libfile-desktopentry-perl			install
libfile-listing-perl				install
libfile-mimeinfo-perl				install
libfile-slurp-perl				install
libfl-dev					install
libflac++6					install
libflac8					install
libflickcurl0					install
libflite1					install
libfm-data					install
libfm-gtk-data					install
libfm-gtk0					deinstall
libfm-gtk1					install
libfm0						deinstall
libfm1						install
libfolks-eds25					install
libfolks-telepathy22				deinstall
libfolks-telepathy25				install
libfolks22					deinstall
libfolks25					install
libfont-afm-perl				install
libfontconfig1					install
libfontconfig1-dev				install
libfontenc1					install
libfontforge1					install
libframe6					install
libfreerdp-plugins-standard			install
libfreerdp1					install
libfreetype6					install
libfreetype6-dev				install
libfreezethaw-perl				install
libfribidi0					install
libfs6						install
libftgl2					install
libfuse2					install
libgadu3					install
libgail-3-0					install
libgail-common					install
libgail18					install
libgamin0					install
libgavl1					install
libgc1c2					install
libgcc1						install
libgck-1-0					install
libgconf-2-4					install
libgconf2-4					install
libgconf2.0-cil					install
libgcr-3-1					install
libgcr-3-common					install
libgcr0						deinstall
libgcrypt11					install
libgcrypt11-dev					install
libgd2-xpm					install
libgdata-common					install
libgdata1.9-cil					install
libgdata11					deinstall
libgdata13					install
libgdbm3					install
libgdiplus					install
libgdk-pixbuf2.0-0				install
libgdk-pixbuf2.0-common				install
libgdraw4					install
libgdu-gtk0					install
libgdu0						install
libgee2						install
libgegl-0.0-0					deinstall
libgegl-0.2-0					install
libgeis1					install
libgeoclue0					install
libgeoip1					install
libgettextpo0					install
libgexiv2-0					install
libgexiv2-1					install
libgif-dev					install
libgif4						install
libgimp2.0					install
libgirepository-1.0-1				install
libgjs0c					install
libgkeyfile1.0-cil				install
libgksu2-0					install
libgl1-mesa-dev					install
libgl1-mesa-dri					install
libgl1-mesa-glx					install
libglade2-0					install
libglade2.0-cil					install
libgladeui-1-11					install
libglapi-mesa					install
libglew1.5					install
libglew1.6					install
libglewmx1.5					install
libglewmx1.6					install
libglib-perl					install
libglib2.0-0					install
libglib2.0-bin					install
libglib2.0-cil					install
libglib2.0-data					install
libglib2.0-dev					install
libglibmm-2.4-1c2a				install
libglu1-mesa					install
libglu1-mesa-dev				install
libgme0						install
libgmime-2.4-2					install
libgmime-2.6-0					install
libgmime2.4-cil					install
libgmime2.6-cil					install
libgmlib0					install
libgmp10					install
libgmp3c2					install
libgmpxx4ldbl					install
libgmtk0					install
libgmtk0-data					install
libgnome-bluetooth8				install
libgnome-control-center1			install
libgnome-desktop-2-17				install
libgnome-desktop-3-2				install
libgnome-keyring-common				install
libgnome-keyring0				install
libgnome-mag2					install
libgnome-media-profiles-3.0-0			install
libgnome-media0					deinstall
libgnome-menu-3-0				install
libgnome-menu2					install
libgnome-vfs2.0-cil				install
libgnome-window-settings1			deinstall
libgnome2-0					install
libgnome2-bin					install
libgnome2-canvas-perl				install
libgnome2-common				install
libgnome2-perl					install
libgnome2-vfs-perl				install
libgnome2.24-cil				install
libgnomecanvas2-0				install
libgnomecanvas2-common				install
libgnomekbd-common				install
libgnomekbd4					deinstall
libgnomekbd7					install
libgnomeui-0					install
libgnomeui-common				install
libgnomevfs2-0					install
libgnomevfs2-common				install
libgnomevfs2-extra				install
libgnutls-dev					install
libgnutls-openssl27				install
libgnutls26					install
libgnutlsxx27					install
libgoa-1.0-0					install
libgoa-1.0-common				install
libgomp1					install
libgoocanvas-common				install
libgoocanvas3					install
libgp11-0					deinstall
libgpg-error-dev				install
libgpg-error0					install
libgpgme11					install
libgphoto2-2					install
libgphoto2-2-dev				install
libgphoto2-l10n					install
libgphoto2-port0				install
libgpm2						install
libgpod-common					install
libgpod4					install
libgps19					deinstall
libgps20					install
libgrail5					install
libgraph4					install
libgraphite3					install
libgrip0					install
libgs9						install
libgs9-common					install
libgsl0ldbl					install
libgsm1						install
libgsm1-dev					install
libgssapi-krb5-2				install
libgssapi3-heimdal				install
libgssdp-1.0-2					deinstall
libgssdp-1.0-3					install
libgssglue1					install
libgssrpc4					install
libgstfarsight0.10-0				deinstall
libgstreamer-plugins-bad0.10-0			install
libgstreamer-plugins-base0.10-0			install
libgstreamer-plugins-base0.10-dev		install
libgstreamer0.10-0				install
libgstreamer0.10-dev				install
libgtk-3-0					install
libgtk-3-bin					install
libgtk-3-common					install
libgtk-sharp-beans-cil				install
libgtk-vnc-1.0-0				install
libgtk-vnc-2.0-0				install
libgtk2-gladexml-perl				install
libgtk2-perl					install
libgtk2.0-0					install
libgtk2.0-bin					install
libgtk2.0-cil					install
libgtk2.0-common				install
libgtkhtml-4.0-0				install
libgtkhtml-4.0-common				install
libgtkhtml-editor-4.0-0				install
libgtkhtml-editor-common			install
libgtkhtml-editor0				install
libgtkhtml3.14-19				install
libgtkmm-2.4-1c2a				install
libgtkmm-3.0-1					install
libgtksourceview-3.0-0				install
libgtksourceview-3.0-common			install
libgtksourceview2.0-0				install
libgtksourceview2.0-common			install
libgtkspell-3-0					install
libgtkspell0					install
libgtkspell3-0					deinstall
libgtop2-7					install
libgtop2-common					install
libgucharmap-2-90-7				install
libgucharmap7					deinstall
libgudev-1.0-0					install
libgudev1.0-cil					install
libgupnp-1.0-3					deinstall
libgupnp-1.0-4					install
libgupnp-igd-1.0-3				deinstall
libgupnp-igd-1.0-4				install
libgutenprint2					install
libgvc5						install
libgvfscommon0					deinstall
libgvnc-1.0-0					install
libgvpr1					install
libgweather-3-0					install
libgweather-common				install
libgweather1					deinstall
libgwibber-gtk2					install
libgwibber1					deinstall
libgwibber2					install
libhal-storage1					install
libhal1						install
libhcrypto4-heimdal				install
libheimbase1-heimdal				install
libheimntlm0-heimdal				install
libhpmud0					install
libhtml-form-perl				install
libhtml-format-perl				install
libhtml-parser-perl				install
libhtml-tagset-perl				install
libhtml-tree-perl				install
libhttp-cookies-perl				install
libhttp-daemon-perl				install
libhttp-date-perl				install
libhttp-message-perl				install
libhttp-negotiate-perl				install
libhttp-server-simple-perl			install
libhunspell-1.2-0				deinstall
libhunspell-1.3-0				install
libhx509-5-heimdal				install
libhyphen0					install
libibus-1.0-0					install
libibus2					deinstall
libical0					install
libice-dev					install
libice6						install
libicu44					deinstall
libicu48					install
libid3tag0					install
libidl-common					install
libidl0						install
libidn11					install
libido-0.1-0					install
libido3-0.1-0					install
libiec61883-0					install
libieee1284-3					install
libieee1284-3-dev				install
libijs-0.35					install
libilmbase6					install
libimlib2					install
libimobiledevice2				install
libindicate-gtk2				deinstall
libindicate-gtk3				install
libindicate-qt1					install
libindicate5					install
libindicator-messages-status-provider1		install
libindicator3					deinstall
libindicator3-6					deinstall
libindicator3-7					install
libindicator6					deinstall
libindicator7					install
libio-pty-perl					install
libio-socket-inet6-perl				install
libio-socket-ssl-perl				install
libio-string-perl				install
libiodbc2					deinstall
libipc-run-perl					install
libisc62					deinstall
libisc83					install
libisccc60					deinstall
libisccc80					install
libisccfg62					deinstall
libisccfg82					install
libiso9660-7					deinstall
libiso9660-8					install
libisoburn1					install
libisofs6					install
libiw30						install
libjack-jackd2-0				install
libjasper1					install
libjavascriptcoregtk-1.0-0			install
libjavascriptcoregtk-3.0-0			install
libjbig2dec0					install
libjpeg-dev					install
libjpeg-turbo8					install
libjpeg-turbo8-dev				install
libjpeg62					install
libjpeg8					install
libjpeg8-dev					install
libjs-jquery					install
libjson-glib-1.0-0				install
libjson0					install
libjte1						install
libk3b6						install
libk3b6-extracodecs				install
libk5crypto3					install
libkabc4					install
libkactivities-bin				install
libkactivities6					install
libkadm5clnt-mit8				install
libkadm5srv-mit8				install
libkalarmcal2					install
libkate1					install
libkatepartinterfaces4				install
libkcal4					install
libkcalcore4					install
libkcalutils4					install
libkcddb4					install
libkcmutils4					install
libkdb5-6					install
libkde3support4					install
libkdeclarative5				install
libkdecorations4				install
libkdecore5					install
libkdesu5					install
libkdeui5					install
libkdewebkit5					install
libkdnssd4					install
libkemoticons4					install
libkephal4abi1					install
libkeyutils1					install
libkfile4					install
libkholidays4					install
libkhtml5					install
libkidletime4					install
libkimap4					install
libkio5						install
libkipi-data					install
libkipi8					install
libkjsapi4					install
libkjsembed4					install
libkldap4					install
libklibc					install
libkmbox4					install
libkmediaplayer4				install
libkmime4					install
libkms1						install
libknewstuff3-4					install
libknotifyconfig4				install
libkntlm4					install
libkonq-common					install
libkonq5-templates				install
libkonq5abi1					install
libkonqsidebarplugin4a				install
libkparts4					install
libkpathsea5					install
libkpimidentities4				install
libkpimtextedit4				install
libkpimutils4					install
libkpty4					install
libkrb5-26-heimdal				install
libkrb5-3					install
libkrb5-dev					install
libkrb5support0					install
libkresources4					install
libkrosscore4					install
libkscreensaver5				install
libksgrd4					install
libksignalplotter4				install
libktexteditor4					install
libkunitconversion4				install
libkwineffects1abi3				install
libkwinglutils1					install
libkwinnvidiahack4				install
libkworkspace4abi1				install
liblastfm0					install
liblaunchpad-integration-3.0-1			install
liblaunchpad-integration-common			install
liblaunchpad-integration1			install
liblaunchpad-integration1.0-cil			install
liblcms1					install
liblcms1-dev					install
liblcms2-2					install
libldap-2.4-2					install
libldap2-dev					install
liblensfun-data					install
liblensfun0					install
liblightdm-gobject-1-0				install
liblircclient0					install
liblist-moreutils-perl				install
libllvm2.9					deinstall
libllvm3.0					deinstall
libllvm3.1					install
liblocale-gettext-perl				install
liblockfile-bin					install
liblockfile1					install
liblouis-data					install
liblouis2					install
liblqr-1-0					install
libltdl-dev					install
libltdl7					install
liblua5.1-0					install
liblvm2app2.2					install
liblwp-mediatypes-perl				install
liblwp-protocol-https-perl			install
liblwres60					deinstall
liblwres80					install
liblzma2					deinstall
liblzma5					install
liblzo2-2					install
libmad0						install
libmagic1					install
libmagickcore3					deinstall
libmagickcore4					install
libmagickcore4-extra				install
libmagickwand3					deinstall
libmagickwand4					install
libmail-sendmail-perl				install
libmailtools-perl				install
libmailtransport4				install
libmath-round-perl				install
libmatroska4					deinstall
libmatroska5					install
libmeanwhile1					install
libmenu-cache1					install
libmetacity-private0				install
libmhash2					install
libmicroblog4					install
libmikmod2					install
libmimic0					install
libminiupnpc5					deinstall
libminiupnpc8					install
libmission-control-plugins0			install
libmjpegtools-1.9				install
libmldbm-perl					install
libmlt++3					install
libmlt-data					install
libmlt4						install
libmms0						install
libmng1						install
libmodplug1					install
libmodule-runtime-perl				install
libmono-addins-gui0.2-cil			install
libmono-addins0.2-cil				install
libmono-cairo2.0-cil				install
libmono-cairo4.0-cil				install
libmono-corlib2.0-cil				install
libmono-corlib4.0-cil				install
libmono-csharp4.0-cil				install
libmono-i18n-west2.0-cil			install
libmono-i18n-west4.0-cil			install
libmono-i18n4.0-cil				install
libmono-management2.0-cil			install
libmono-management4.0-cil			install
libmono-posix2.0-cil				install
libmono-posix4.0-cil				install
libmono-security2.0-cil				install
libmono-security4.0-cil				install
libmono-sharpzip2.84-cil			install
libmono-sharpzip4.84-cil			install
libmono-system-configuration4.0-cil		install
libmono-system-core4.0-cil			install
libmono-system-drawing4.0-cil			install
libmono-system-security4.0-cil			install
libmono-system-xml4.0-cil			install
libmono-system2.0-cil				install
libmono-system4.0-cil				install
libmono-zeroconf1.0-cil				install
libmount1					install
libmozjs185-1.0					install
libmp3lame0					install
libmpc2						install
libmpcdec6					install
libmpeg2-4					install
libmpfr4					install
libmpg123-0					install
libmpg123-dev					install
libmtdev1					install
libmtp-common					install
libmtp-runtime					install
libmtp8						deinstall
libmtp9						install
libmuffin0					install
libmusicbrainz3-6				install
libmusicbrainz4c2a				deinstall
libmusicbrainz5-0				install
libmutter0					install
libmx-1.0-2					install
libmysqlclient18				install
libmythes-1.2-0					install
libnatpmp1					install
libnautilus-extension1				deinstall
libnautilus-extension1a				install
libncurses5					install
libncurses5-dev					install
libncursesw5					install
libndesk-dbus-glib1.0-cil			install
libndesk-dbus1.0-cil				install
libnemo-extension1				install
libneon27-gnutls				install
libnepomuk4					install
libnepomukdatamanagement4			install
libnepomukquery4a				install
libnepomuksync4					install
libnepomukutils4				install
libnet-daemon-perl				install
libnet-dbus-perl				install
libnet-dns-perl					install
libnet-domain-tld-perl				install
libnet-http-perl				install
libnet-ip-perl					install
libnet-ssleay-perl				install
libnetfilter-conntrack3				install
libnetpbm10					install
libnettle4					install
libnewt0.52					install
libnfnetlink0					install
libnfsidmap2					install
libnice10					install
libnih-dbus1					install
libnih1						install
libnl-3-200					install
libnl-genl-3-200				install
libnl-route-3-200				install
libnl1						install
libnl3						deinstall
libnm-glib-vpn1					install
libnm-glib2					deinstall
libnm-glib4					install
libnm-gtk-common				install
libnm-gtk0					install
libnm-util1					deinstall
libnm-util2					install
libnotify-bin					install
libnotify0.4-cil				install
libnotify1					deinstall
libnotify4					install
libnspr4					install
libnspr4-0d					install
libnss-mdns					install
libnss3						install
libnss3-1d					install
libntfs-3g79					deinstall
libntfs10					install
libntrack-qt4-1					install
libntrack0					install
libnux-0.9-0					deinstall
libnux-1.0-0					deinstall
libnux-2.0-0					install
libnux-2.0-common				install
liboauth0					install
libobparser21					deinstall
libobrender21					deinstall
libobrender27					install
libobt0						install
libodbc1					install
libofa0						install
libogg0						install
liboil0.3					install
liboobs-1-5					install
libopenal-data					install
libopenal-dev					install
libopenal1					install
libopencc1					install
libopencore-amrnb0				install
libopencore-amrwb0				install
libopencv-calib3d2.3				install
libopencv-core2.3				install
libopencv-features2d2.3				install
libopencv-flann2.3				install
libopencv-highgui2.3				install
libopencv-imgproc2.3				install
libopencv-objdetect2.3				install
libopenexr6					install
libopenjpeg2					install
libopenobex1					install
libopenraw1					install
libopenspc0					install
liborbit2					install
liborc-0.4-0					install
libosmesa6					install
libosmesa6-dev					install
libosp5						install
libostyle1c2					install
liboverlay-scrollbar-0.1-0			deinstall
liboverlay-scrollbar-0.2-0			install
liboverlay-scrollbar3-0.2-0			install
libp11-kit-dev					install
libp11-kit0					install
libpackage-deprecationmanager-perl		install
libpackage-stash-perl				install
libpackage-stash-xs-perl			install
libpackagekit-glib2-14				install
libpam-cap					install
libpam-ck-connector				install
libpam-gnome-keyring				install
libpam-modules					install
libpam-modules-bin				install
libpam-runtime					install
libpam-smbpass					install
libpam-winbind					install
libpam0g					install
libpanel-applet-3-0				deinstall
libpanel-applet-4-0				install
libpanel-applet2-0				deinstall
libpango-perl					install
libpango1.0-0					install
libpangomm-1.4-1				install
libpaper-utils					install
libpaper1					install
libparams-classify-perl				install
libparams-util-perl				install
libparams-validate-perl				install
libparse-debianchangelog-perl			install
libparted0debian1				install
libpathplan4					install
libpcap0.8					install
libpci3						install
libpciaccess0					install
libpcre3					install
libpcre3-dev					install
libpcrecpp0					install
libpcsclite1					install
libpeas-1.0-0					install
libpeas-common					install
libperl5.14					install
libphonon4					install
libpipeline1					install
libpixman-1-0					install
libplasma-geolocation-interface4		install
libplasma3					install
libplasmaclock4abi3				install
libplasmagenericshell4				install
libplist1					install
libplrpc-perl					install
libplymouth2					install
libpng12-0					install
libpng12-dev					install
libpod-plainer-perl				install
libpolkit-agent-1-0				install
libpolkit-backend-1-0				install
libpolkit-gobject-1-0				install
libpolkit-gtk-1-0				deinstall
libpolkit-qt-1-1				install
libpoppler-glib6				deinstall
libpoppler-glib8				install
libpoppler13					deinstall
libpoppler19					install
libpopt0					install
libportaudio2					install
libpostproc51					deinstall
libpostproc52					install
libppl-c2					deinstall
libppl-c4					install
libppl7						deinstall
libppl9						install
libprison0					install
libprocesscore4abi1				install
libprocessui4a					install
libprojectm2					install
libprotobuf6					deinstall
libprotobuf7					install
libprotoc6					deinstall
libprotoc7					install
libproxy0					deinstall
libproxy1					install
libproxy1-plugin-gsettings			install
libproxy1-plugin-networkmanager			install
libpst4						install
libpth20					install
libpthread-stubs0				install
libpthread-stubs0-dev				install
libpulse-browse0				deinstall
libpulse-dev					install
libpulse-mainloop-glib0				install
libpulse0					install
libpulsedsp					install
libpurple-bin					install
libpurple0					install
libpwl5						install
libpython2.7					install
libpython3.2					install
libqalculate5					install
libqapt-runtime					install
libqapt1					install
libqca2						install
libqgpsmm19					deinstall
libqimageblitz4					install
libqjson0					install
libqrencode3					install
libqt4-dbus					install
libqt4-declarative				install
libqt4-designer					install
libqt4-help					install
libqt4-network					install
libqt4-opengl					install
libqt4-qt3support				install
libqt4-script					install
libqt4-scripttools				install
libqt4-sql					install
libqt4-sql-mysql				install
libqt4-sql-sqlite				install
libqt4-svg					install
libqt4-test					install
libqt4-webkit					install
libqt4-xml					install
libqt4-xmlpatterns				install
libqtassistantclient4				install
libqtbamf1					install
libqtcore4					install
libqtdee2					install
libqtgconf1					install
libqtgui4					install
libqtwebkit4					install
libquadmath0					install
libquicktime2					install
libquvi-scripts					install
libquvi0					install
libquvi7					install
libqxt-core0					install
libqxt-gui0					install
libraptor1					install
libraptor2-0					install
librarian0					install
librasqal2					deinstall
librasqal3					install
libraw1394-11					install
libraw5						install
librdf0						install
libreadline6					install
libreoffice-base-core				install
libreoffice-calc				install
libreoffice-common				install
libreoffice-core				install
libreoffice-draw				install
libreoffice-emailmerge				install
libreoffice-gnome				install
libreoffice-gtk					install
libreoffice-help-en-gb				install
libreoffice-help-en-us				install
libreoffice-impress				install
libreoffice-l10n-en-gb				install
libreoffice-l10n-en-za				install
libreoffice-math				install
libreoffice-style-human				install
libreoffice-style-tango				install
libreoffice-writer				install
libresid-builder0c2a				install
librest-0.7-0					install
librhythmbox-core5				install
librhythmbox-core6				install
libroken18-heimdal				install
librpc-xml-perl					install
librpcsecgss3					deinstall
librpm1						deinstall
librpm2						install
librpmbuild1					deinstall
librpmbuild2					install
librpmio1					deinstall
librpmio2					install
librpmsign0					install
librsvg2-2					install
librsvg2-common					install
librsync1					install
librtmp0					install
libsamplerate0					install
libsane						install
libsane-common					install
libsane-dev					install
libsane-hpaio					install
libsasl2-2					install
libsasl2-modules				install
libschroedinger-1.0-0				install
libsdl-image1.2					install
libsdl-mixer1.2					install
libsdl1.2debian					install
libsdl1.2debian-pulseaudio			deinstall
libselinux1					install
libsensors4					install
libsepol1					install
libsgmls-perl					install
libsgutils2-2					install
libshout3					install
libsidplay1					install
libsidplay2					install
libsigc++-2.0-0c2a				install
libsilc-1.1-2					deinstall
libsilcclient-1.1-3				deinstall
libslang2					install
libslp1						install
libslv2-9					install
libsm-dev					install
libsm6						install
libsmbclient					install
libsmpeg0					deinstall
libsndfile1					install
libsnmp-base					install
libsnmp15					install
libsocket6-perl					install
libsolid4					install
libsolidcontrol4abi2				install
libsolidcontrolifaces4abi2			install
libsonic0					install
libsoprano4					install
libsoundtouch0					install
libsoup-gnome2.4-1				install
libsoup2.4-1					install
libsox-fmt-alsa					install
libsox-fmt-base					install
libsox1b					install
libsp1c2					install
libspandsp2					install
libspectre1					install
libspeechd2					install
libspeex1					install
libspeexdsp1					install
libspiro0					install
libsqlite3-0					install
libss2						install
libssh-4					install
libssl-dev					install
libssl0.9.8					install
libssl1.0.0					install
libstartup-notification0			install
libstdc++6					install
libstdc++6-4.5-dev				install
libstdc++6-4.6-dev				install
libstlport4.6ldbl				install
libstreamanalyzer0				install
libstreams0					install
libsub-install-perl				install
libsub-name-perl				install
libsvga1					install
libswitch-perl					install
libswscale0					deinstall
libswscale2					install
libsyncdaemon-1.0-1				install
libsyndication4					install
libsys-hostname-long-perl			install
libsysfs2					install
libt1-5						install
libtag1-vanilla					install
libtag1c2a					install
libtaglib2.0-cil				install
libtalloc2					install
libtar0						install
libtaskmanager4abi3				install
libtasn1-3					install
libtasn1-3-dev					install
libtdb1						install
libtelepathy-farsight0				deinstall
libtelepathy-farstream1				deinstall
libtelepathy-farstream2				install
libtelepathy-glib0				install
libtelepathy-logger2				install
libterm-readkey-perl				install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libtextcat-data					install
libtextcat0					install
libthai-data					install
libthai0					install
libtheora0					install
libthreadweaver4				install
libtie-ixhash-perl				install
libtiff-tools					install
libtiff4					install
libtiff4-dev					install
libtiffxx0c2					install
libtimedate-perl				install
libtimezonemap1					install
libtinfo-dev					install
libtinfo5					install
libtinyxml2.6.2					install
libtirpc1					install
libtotem-plparser17				install
libtotem0					install
libtry-tiny-perl				install
libts-0.0-0					install
libtwolame0					install
libtxc-dxtn-s2tc0				install
libubuntuone-1.0-1				deinstall
libubuntuoneui-3.0-1				install
libudev0					install
libudisks2-0					install
libumfpack5.4.0					install
libuninameslist0				install
libunique-1.0-0					install
libunique-3.0-0					install
libunistring0					install
libunity-2d-private0				install
libunity-core-4.0-4				deinstall
libunity-core-5.0-5				install
libunity-misc0					deinstall
libunity-misc4					install
libunity4					deinstall
libunity6					deinstall
libunity9					install
libupnp3					install
libupower-glib1					install
liburi-perl					install
libusb-0.1-4					install
libusb-1.0-0					install
libusb-dev					install
libusbmuxd1					install
libuser1					install
libutempter0					install
libutouch-evemu1				install
libutouch-frame1				install
libutouch-geis1					install
libutouch-grail1				install
libuuid-perl					install
libuuid1					install
libv4l-0					install
libv4l-dev					install
libv4lconvert0					install
libva-x11-1					install
libva1						install
libvcdinfo0					install
libvdpau1					install
libvirtodbc0					install
libvisual-0.4-0					install
libvisual-0.4-plugins				install
libvlc5						install
libvlccore4					deinstall
libvlccore5					install
libvncserver0					install
libvo-aacenc0					install
libvo-amrwbenc0					install
libvorbis0a					install
libvorbisenc2					install
libvorbisfile3					install
libvpx0						deinstall
libvpx1						install
libvte-2.90-9					install
libvte-2.90-common				install
libvte-common					install
libvte9						install
libwacom-common					install
libwacom2					install
libwavpack1					install
libwbclient0					install
libweather-ion6					install
libwebkitgtk-1.0-0				install
libwebkitgtk-1.0-common				install
libwebkitgtk-3.0-0				install
libwebkitgtk-3.0-common				install
libwildmidi-config				install
libwildmidi1					install
libwind0-heimdal				install
libwmf0.2-7					install
libwmf0.2-7-gtk					install
libwnck-3-0					install
libwnck-3-common				install
libwnck-common					install
libwnck22					install
libwpd-0.9-9					install
libwpg-0.2-2					install
libwps-0.2-2					install
libwrap0					install
libwww-curl-perl				install
libwww-mechanize-perl				install
libwww-perl					install
libwww-robotrules-perl				install
libwxbase2.8-0					install
libwxgtk2.8-0					install
libx11-6					install
libx11-data					install
libx11-dev					install
libx11-xcb-dev					install
libx11-xcb1					install
libx264-116					deinstall
libx264-120					install
libx86-1					install
libxapian22					install
libxatracker1					install
libxau-dev					install
libxau6						install
libxaw7						install
libxcb-atom1					deinstall
libxcb-aux0					deinstall
libxcb-composite0				install
libxcb-dri2-0					install
libxcb-event1					deinstall
libxcb-glx0					install
libxcb-glx0-dev					install
libxcb-keysyms1					install
libxcb-randr0					install
libxcb-render0					install
libxcb-shape0					install
libxcb-shm0					install
libxcb-util0					install
libxcb-xv0					install
libxcb1						install
libxcb1-dev					install
libxcomposite-dev				install
libxcomposite1					install
libxcursor-dev					install
libxcursor1					install
libxdamage-dev					install
libxdamage1					install
libxdmcp-dev					install
libxdmcp6					install
libxdo2						install
libxext-dev					install
libxext6					install
libxfixes-dev					install
libxfixes3					install
libxfont1					install
libxft2						install
libxi-dev					install
libxi6						install
libxinerama-dev					install
libxinerama1					install
libxkbfile1					install
libxklavier16					install
libxml-namespacesupport-perl			install
libxml-parser-perl				install
libxml-sax-base-perl				install
libxml-sax-expat-perl				install
libxml-sax-perl					install
libxml-simple-perl				install
libxml-twig-perl				install
libxml-writer-perl				install
libxml-xpath-perl				install
libxml2						install
libxml2-dev					install
libxml2-utils					install
libxmmsclient-glib1				install
libxmmsclient6					install
libxmu6						install
libxmuu1					install
libxp6						install
libxpm4						install
libxrandr-dev					install
libxrandr2					install
libxrender-dev					install
libxrender1					install
libxres1					install
libxslt1-dev					install
libxslt1.1					install
libxss1						install
libxt-dev					install
libxt6						install
libxtst6					install
libxv1						install
libxvidcore4					install
libxvmc1					install
libxxf86dga1					install
libxxf86vm-dev					install
libxxf86vm1					install
libyajl1					install
libyaml-syck-perl				install
libyaml-tiny-perl				install
libyelp0					install
libzbar0					install
libzeitgeist-1.0-1				install
libzephyr4					install
libzvbi-common					install
libzvbi0					install
light-themes					install
lightdm						install
lintian						install
linux-firmware					install
linux-generic-pae				install
linux-headers-3.2.0-17				install
linux-headers-3.2.0-17-generic-pae		install
linux-headers-3.2.0-18				install
linux-headers-3.2.0-18-generic-pae		install
linux-headers-3.2.0-19				install
linux-headers-3.2.0-19-generic-pae		install
linux-headers-3.2.0-20				install
linux-headers-3.2.0-20-generic-pae		install
linux-headers-3.2.0-21				install
linux-headers-3.2.0-21-generic-pae		install
linux-headers-3.2.0-22				install
linux-headers-3.2.0-22-generic-pae		install
linux-headers-3.2.0-23				install
linux-headers-3.2.0-23-generic-pae		install
linux-headers-3.2.0-24				install
linux-headers-3.2.0-24-generic-pae		install
linux-headers-3.2.0-25				install
linux-headers-3.2.0-25-generic-pae		install
linux-headers-3.2.0-26				install
linux-headers-3.2.0-26-generic-pae		install
linux-headers-3.2.0-27				install
linux-headers-3.2.0-27-generic-pae		install
linux-headers-3.2.0-29				install
linux-headers-3.2.0-29-generic-pae		install
linux-headers-3.2.0-30				install
linux-headers-3.2.0-30-generic-pae		install
linux-headers-3.2.0-31				install
linux-headers-3.2.0-31-generic-pae		install
linux-headers-3.2.0-32				install
linux-headers-3.2.0-32-generic-pae		install
linux-headers-3.2.0-33				install
linux-headers-3.2.0-33-generic-pae		install
linux-headers-3.2.0-34				install
linux-headers-3.2.0-34-generic-pae		install
linux-headers-generic-pae			install
linux-image-2.6.38-10-generic-pae		deinstall
linux-image-2.6.38-11-generic-pae		deinstall
linux-image-2.6.38-12-generic-pae		install
linux-image-2.6.38-8-generic-pae		deinstall
linux-image-3.0.0-12-generic-pae		deinstall
linux-image-3.0.0-13-generic-pae		deinstall
linux-image-3.0.0-14-generic-pae		deinstall
linux-image-3.0.0-15-generic-pae		deinstall
linux-image-3.0.0-16-generic-pae		install
linux-image-3.2.0-17-generic-pae		install
linux-image-3.2.0-18-generic-pae		install
linux-image-3.2.0-19-generic-pae		install
linux-image-3.2.0-20-generic-pae		install
linux-image-3.2.0-21-generic-pae		install
linux-image-3.2.0-22-generic-pae		install
linux-image-3.2.0-23-generic-pae		install
linux-image-3.2.0-24-generic-pae		install
linux-image-3.2.0-25-generic-pae		install
linux-image-3.2.0-26-generic-pae		install
linux-image-3.2.0-27-generic-pae		install
linux-image-3.2.0-29-generic-pae		install
linux-image-3.2.0-30-generic-pae		install
linux-image-3.2.0-31-generic-pae		install
linux-image-3.2.0-32-generic-pae		install
linux-image-3.2.0-33-generic-pae		install
linux-image-3.2.0-34-generic-pae		install
linux-image-generic-pae				install
linux-libc-dev					install
linux-sound-base				install
locales						install
lockfile-progs					install
login						install
logrotate					install
lp-solve					install
lsb-base					install
lsb-core					install
lsb-invalid-mta					install
lsb-release					install
lshw						install
lsof						install
ltrace						install
luatex						install
lxappearance					install
lxde						install
lxde-common					install
lxde-core					install
lxde-icon-theme					install
lxdm						install
lxinput						install
lxmenu-data					install
lxmusic						install
lxpanel						install
lxrandr						install
lxsession					install
lxsession-edit					install
lxshortcut					install
lxterminal					install
lynx						install
lynx-cur					install
m4						install
mahjongg					install
make						install
makedev						install
man-db						install
manpages					install
manpages-dev					install
mawk						install
media-player-info				install
medibuntu-keyring				install
melt						install
memtest86+					install
mencoder					install
menu						install
menu-xdg					install
mesa-common-dev					install
mesa-utils					install
metacity					install
metacity-common					install
mime-support					install
min12xxw					install
minitube					install
mlocate						install
mobile-broadband-provider-info			install
modemmanager					install
module-init-tools				install
mono-2.0-gac					install
mono-4.0-gac					install
mono-csharp-shell				install
mono-gac					install
mono-gmcs					install
mono-runtime					install
mount						install
mountall					install
mousetweaks					install
movixmaker-2					install
mozilla-tiff-plugin				install
mozplugger					install
mplayer						install
mscompress					install
mtools						install
mtr-tiny					install
muffin-common					install
multiarch-support				install
mutter-common					install
myspell-en-au					install
myspell-en-gb					install
myspell-en-za					install
mysql-client-core-5.5				install
mysql-common					install
mysql-server-core-5.5				install
mythes-en-us					install
nano						install
nautilus					install
nautilus-data					install
nautilus-sendto					install
nautilus-sendto-empathy				install
nautilus-share					install
ncurses-base					install
ncurses-bin					install
ncurses-term					install
nemo						install
nemo-data					install
nemo-fileroller					install
nerolinux					install
net-tools					install
netbase						install
netcat-openbsd					install
netflix-desktop					install
netpbm						install
network-manager					install
network-manager-gnome				install
network-manager-pptp				install
network-manager-pptp-gnome			install
nfs-common					install
nfs-kernel-server				install
nmap						install
normalize-audio					install
notify-osd					install
notify-osd-icons				install
ntfs-3g						install
ntfsprogs					install
ntpdate						install
ntrack-module-libnl-0				install
nux-tools					install
nvidia-173					deinstall
nvidia-common					install
nvidia-current					install
nvidia-settings					install
obconf						install
obex-data-server				install
obexd-client					install
odbcinst					install
odbcinst1debian2				install
onboard						install
oneconf						install
openbox						install
openbox-themes					install
opencl-headers					install
opencpn						install
openjade					install
openjdk-6-jre					install
openjdk-6-jre-headless				install
openjdk-6-jre-lib				install
openjdk-7-jre					install
openjdk-7-jre-headless				install
openjdk-7-jre-lib				install
openoffice.org-hyphenation			install
openprinting-ppds				install
openshot					install
openshot-doc					install
openssh-client					install
openssh-server					install
openssl						install
openstreetmap-map-icons-classic			install
openstreetmap-map-icons-square			install
os-prober					install
oss-compat					install
oss4-dev					install
overlay-scrollbar				install
oxygen-cursor-theme				install
oxygen-icon-theme				install
p7zip-full					install
parted						install
passwd						install
patch						install
patchutils					install
pavucontrol					install
pax						install
pciutils					install
pcmanfm						install
pcmciautils					install
perl						install
perl-base					install
perl-modules					install
perl-tk						install
perlmagick					install
phonon						install
phonon-backend-gstreamer			install
pitivi						install
pkg-config					install
plasma-dataengines-workspace			install
plasma-desktop					install
plasma-scriptengine-javascript			install
plasma-widgets-workspace			install
plymouth					install
plymouth-label					install
plymouth-theme-ubuntu-logo			install
plymouth-theme-ubuntu-text			install
pm-utils					install
pnm2ppa						install
po-debconf					install
policykit-1					install
policykit-1-gnome				install
policykit-desktop-privileges			install
poppler-utils					install
popularity-contest				install
portmap						deinstall
powermgmt-base					install
ppp						install
pppconfig					install
pppoeconf					install
pptp-linux					install
prelink						install
printer-driver-c2esp				install
printer-driver-foo2zjs				install
printer-driver-gutenprint			install
printer-driver-hpcups				install
printer-driver-hpijs				install
printer-driver-min12xxw				install
printer-driver-pnm2ppa				install
printer-driver-postscript-hp			install
printer-driver-ptouch				install
printer-driver-pxljr				install
printer-driver-sag-gdi				install
printer-driver-splix				install
procps						install
projectm-data					install
protobuf-compiler				install
psmisc						install
ptouch-driver					install
pulseaudio					install
pulseaudio-esound-compat			install
pulseaudio-module-bluetooth			install
pulseaudio-module-gconf				install
pulseaudio-module-x11				install
pulseaudio-utils				install
pxljr						install
python						install
python-appindicator				install
python-apport					install
python-apt					install
python-apt-common				install
python-aptdaemon				install
python-aptdaemon-gtk				install
python-aptdaemon.gtk3widgets			install
python-aptdaemon.gtkwidgets			install
python-aptdaemon.pkcompat			install
python-brlapi					install
python-cairo					install
python-central					install
python-chardet					install
python-configglue				install
python-crypto					install
python-cups					install
python-cupshelpers				install
python-dateutil					install
python-dbg					install
python-dbus					install
python-dbus-dev					install
python-debian					install
python-debtagshw				install
python-defer					install
python-dirspec					install
python-egenix-mxdatetime			install
python-egenix-mxtools				install
python-gconf					install
python-gdbm					install
python-gi					install
python-gi-cairo					install
python-glade2					install
python-gmenu					install
python-gnome2					install
python-gnomekeyring				install
python-gnupginterface				install
python-gobject					install
python-gobject-2				install
python-gps					install
python-gst0.10					install
python-gtk2					install
python-gtksourceview2				install
python-gtkspell					install
python-httplib2					install
python-ibus					install
python-imaging					install
python-indicate					install
python-keyring					install
python-launchpad-integration			install
python-launchpadlib				install
python-lazr.restfulclient			install
python-lazr.uri					install
python-libproxy					install
python-libuser					install
python-libxml2					install
python-louis					install
python-lxml					install
python-mako					install
python-markupsafe				install
python-minimal					install
python-mlt3					install
python-nautilus					install
python-notify					install
python-oauth					install
python-openssl					install
python-packagekit				install
python-pam					install
python-paramiko					install
python-pexpect					install
python-piston-mini-client			install
python-pkg-resources				install
python-problem-report				install
python-protobuf					install
python-pyatspi2					install
python-pycurl					install
python-pygoocanvas				install
python-pyinotify				install
python-pyorbit					install
python-qt4					install
python-qt4-dbus					install
python-rdflib					install
python-renderpm					install
python-reportlab				install
python-reportlab-accel				install
python-serial					install
python-simplejson				install
python-sip					install
python-smbc					install
python-software-properties			install
python-speechd					install
python-support					install
python-telepathy				install
python-twisted-bin				install
python-twisted-core				install
python-twisted-names				install
python-twisted-web				install
python-ubuntu-sso-client			install
python-ubuntuone-client				install
python-ubuntuone-control-panel			install
python-ubuntuone-storageprotocol		install
python-uno					install
python-virtkey					install
python-vte					install
python-wadllib					install
python-webkit					install
python-wnck					install
python-wsgi-intercept				install
python-xapian					install
python-xdg					install
python-xkit					install
python-zeitgeist				install
python-zope.interface				install
python2.7					install
python2.7-dbg					install
python2.7-minimal				install
python3.2					install
python3.2-minimal				install
qapt-batch					install
qdbus						install
qt-at-spi					install
radeontool					install
rar						install
rarian-compat					install
rastertosag-gdi					install
rdesktop					install
read-edid					install
readline-common					install
recordmydesktop					install
remmina						install
remmina-common					install
remmina-plugin-rdp				install
remmina-plugin-vnc				install
resolvconf					install
rfkill						install
rhythmbox					install
rhythmbox-data					install
rhythmbox-mozilla				install
rhythmbox-plugin-cdrecorder			install
rhythmbox-plugin-magnatune			install
rhythmbox-plugin-zeitgeist			install
rhythmbox-plugins				install
rhythmbox-ubuntuone				install
rpcbind						install
rpm						install
rpm-common					install
rpm2cpio					install
rsync						install
rsyslog						install
rtkit						install
samba						install
samba-common					install
samba-common-bin				install
sane-utils					install
screen-resolution-extra				install
screensaver-default-images			install
scrot						install
seahorse					install
sed						install
sensible-utils					install
sessioninstaller				install
set-cd-rom-speed				install
setcd						install
sgml-base					install
sgml-data					install
sgmlspl						install
shared-desktop-ontologies			install
shared-mime-info				install
shotwell					install
simple-scan					install
skype						install
skype-bin					install
smbclient					install
sni-qt						install
software-center					install
software-center-aptdaemon-plugins		install
software-properties-common			install
software-properties-gtk				install
soprano-daemon					install
sound-theme-freedesktop				install
sox						install
sp						install
speech-dispatcher				install
splix						install
ssh						install
ssh-askpass-gnome				install
ssh-import-id					install
ssl-cert					install
strace						install
sudo						install
synaptic					install
syslinux					install
syslinux-common					install
syslinux-legacy					install
system-config-printer-common			install
system-config-printer-gnome			install
system-config-printer-udev			install
system-config-samba				install
system-tools-backends				install
systemsettings					install
sysv-rc						install
sysvinit-utils					install
tar						install
tcl						install
tcl8.4						install
tcl8.5						install
tcpd						install
tcpdump						install
tdb-tools					install
telepathy-gabble				install
telepathy-haze					install
telepathy-idle					install
telepathy-indicator				install
telepathy-logger				install
telepathy-mission-control-5			install
telepathy-salut					install
telnet						install
tex-common					install
texlive-base					install
texlive-binaries				install
texlive-common					install
texlive-doc-base				install
texlive-fonts-recommended			install
texlive-latex-base				install
texlive-latex-recommended			install
thunderbird					install
thunderbird-globalmenu				install
thunderbird-gnome-support			install
time						install
tipa						install
tomboy						install
toshset						install
totem						install
totem-common					install
totem-mozilla					install
totem-plugins					install
transmission-common				install
transmission-gtk				install
tsclient					deinstall
tsconf						install
ttf-aenigma					install
ttf-dejavu-core					install
ttf-dejavu-extra				install
ttf-droid					install
ttf-freefont					install
ttf-indic-fonts-core				install
ttf-kacst-one					install
ttf-khmeros-core				install
ttf-lao						install
ttf-liberation					install
ttf-mscorefonts-installer			install
ttf-opensymbol					install
ttf-punjabi-fonts				install
ttf-takao-pgothic				install
ttf-thai-tlwg					install
ttf-ubuntu-font-family				install
ttf-umefont					install
ttf-unfonts-core				install
ttf-wqy-microhei				install
tzdata						install
tzdata-java					install
ubuntu-artwork					install
ubuntu-desktop					install
ubuntu-docs					install
ubuntu-extras-keyring				install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-mono					install
ubuntu-restricted-addons			install
ubuntu-restricted-extras			install
ubuntu-sounds					install
ubuntu-sso-client				install
ubuntu-sso-client-gtk				install
ubuntu-sso-client-qt				install
ubuntu-standard					install
ubuntu-system-service				install
ubuntu-wallpapers				install
ubuntu-wallpapers-precise			install
ubuntuone-client				install
ubuntuone-client-gnome				install
ubuntuone-control-panel				install
ubuntuone-control-panel-common			install
ubuntuone-control-panel-gtk			install
ubuntuone-control-panel-qt			install
ubuntuone-couch					install
ubuntuone-installer				install
ucf						install
udev						install
udisks						install
udisks2						install
ufw						install
unattended-upgrades				install
unity						install
unity-2d					install
unity-2d-common					install
unity-2d-launcher				install
unity-2d-panel					install
unity-2d-places					install
unity-2d-shell					install
unity-2d-spread					install
unity-asset-pool				install
unity-common					install
unity-greeter					install
unity-lens-applications				install
unity-lens-files				install
unity-lens-music				install
unity-lens-video				install
unity-place-applications			install
unity-place-files				install
unity-scope-musicstores				install
unity-scope-video-remote			install
unity-services					install
unixodbc					install
unixodbc-dev					install
uno-libs3					install
unrar						install
unzip						install
update-inetd					install
update-manager					install
update-manager-core				install
update-notifier					install
update-notifier-common				install
upower						install
upstart						install
ure						install
ureadahead					install
usb-creator-common				install
usb-creator-gtk					install
usb-modeswitch					install
usb-modeswitch-data				install
usbmuxd						install
usbutils					install
util-linux					install
uuid-runtime					install
valgrind					install
vbetool						install
vcdimager					install
viking						install
vim-common					install
vim-tiny					install
vinagre						install
vino						install
virtualbox-4.1					install
virtuoso-minimal				install
virtuoso-opensource-6.1-bin			install
virtuoso-opensource-6.1-common			install
vlc						install
vlc-data					install
vlc-nox						install
vlc-plugin-notify				install
vlc-plugin-pulse				install
vorbis-tools					install
w32codecs					install
wamerican					install
wbritish					install
wget						install
whiptail					install
whois						install
whoopsie					install
winbind						install
wine						install
wine-compholio					install
wine-gecko1.8					install
wine-mono0.0.8					install
wine1.4						deinstall
wine1.4-i386					deinstall
wine1.5						install
wine1.5-i386					install
winetricks					install
wireless-crda					install
wireless-regdb					install
wireless-tools					install
wodim						install
wpasupplicant					install
wuala						install
x-ttcidfont-conf				install
x11-apps					install
x11-common					install
x11-session-utils				install
x11-utils					install
x11-xfs-utils					install
x11-xkb-utils					install
x11-xserver-utils				install
x11proto-composite-dev				install
x11proto-core-dev				install
x11proto-damage-dev				install
x11proto-dri2-dev				install
x11proto-fixes-dev				install
x11proto-gl-dev					install
x11proto-input-dev				install
x11proto-kb-dev					install
x11proto-randr-dev				install
x11proto-render-dev				install
x11proto-xext-dev				install
x11proto-xf86vidmode-dev			install
x11proto-xinerama-dev				install
xarchiver					install
xauth						install
xbitmaps					install
xcursor-themes					install
xdg-user-dirs					install
xdg-user-dirs-gtk				install
xdg-utils					install
xdiagnose					install
xdotool						install
xfonts-base					install
xfonts-encodings				install
xfonts-mathml					install
xfonts-scalable					install
xfonts-utils					install
xinit						install
xinput						install
xkb-data					install
xml-core					install
xmms2-core					install
xmms2-plugin-alsa				install
xmms2-plugin-id3v2				install
xmms2-plugin-mad				install
xmms2-plugin-vorbis				install
xorg						install
xorg-docs-core					install
xorg-sgml-doctools				install
xorriso						install
xsane						install
xsane-common					install
xscreensaver					deinstall
xscreensaver-data				install
xscreensaver-gl					install
xserver-common					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-mouse			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-vmmouse			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-apm				install
xserver-xorg-video-ark				install
xserver-xorg-video-ati				install
xserver-xorg-video-chips			install
xserver-xorg-video-cirrus			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-geode			install
xserver-xorg-video-i128				install
xserver-xorg-video-i740				install
xserver-xorg-video-intel			install
xserver-xorg-video-mach64			install
xserver-xorg-video-mga				install
xserver-xorg-video-neomagic			install
xserver-xorg-video-nouveau			install
xserver-xorg-video-openchrome			install
xserver-xorg-video-qxl				install
xserver-xorg-video-r128				install
xserver-xorg-video-radeon			install
xserver-xorg-video-rendition			install
xserver-xorg-video-s3				install
xserver-xorg-video-s3virge			install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-trident			install
xserver-xorg-video-tseng			install
xserver-xorg-video-vesa				install
xserver-xorg-video-vmware			install
xserver-xorg-video-voodoo			install
xsltproc					install
xterm						install
xtrans-dev					install
xul-ext-ubufox					install
xz-lzma						install
xz-utils					install
yelp						install
yelp-xsl					install
zeitgeist					install
zeitgeist-core					install
zeitgeist-datahub				install
zeitgeist-extension-fts				install
zenity						install
zenity-common					install
zip						install
zlib1g						install
zlib1g-dev					install
```

---

### Post by sdowney717 on 2012-12-05
I plan to move my /home folder to a new partition
Then upgrade to 64 bit
[http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

**How much room should be left for the OS?**

I currently have a 750gb drive
100gb is for NTFS windows
320gb is an ext4 partition which will be the new home
which leaves a huge amount that currently has OS and /home

Likely way too much space will be reserved for just the OS

I plan to copy /home to the other 320gb partition
likely after booting the USB, then resize the old OS partition much smaller and expand the 320gb partition.

---

### Post by vanadium on 2012-12-05
As people mentionned before, you can not literally "upgrade" to 64 bit: you need to reinstall.

The easiest procedure for yuo would be
1) Make sure the backup of yuor data on an external medium is up to date, so you can erase existing data on yuor computer.
2) Delete existing linux partitions
3) Run the installer. At some point the isntaller gives different options, among which: "do something else". The latter option will allow you to repartition your drive.

Next to your ntfs partition, I 'd create an extended partition in the remaining space. In that extended partition, you then can create
- a 10-12 GB partition for /
- a big partition for /home
- a swap partition with a size somewhat arger than your amount of RAM.

When done, copy your data back and reinstall any software that did not come with the standard install.

This will be the fastest and safest procedure.

---

### Post by sdowney717 on 2012-12-05
Thanks. I also have an external USB 300gb drive I could use to store /home.

Now I understand what your saying. This will involve 2 large copy operations, one to USB drive, then back over to new /home folder

What happens if copy /home to new partition /home
Then install OR would that wipe out the new copy of /home with all your personal files?

*Thing is I have files currently sitting in that 319gb sda partition I dont want to loose.*
how can I just use that partition as a location for my /home folder?

here is gparted for the 2 hard drives

---

### Post by sdowney717 on 2012-12-05
appears this can be done
should be able to copy /home to that partition. then resize and install 64 bit

[http://ubuntuforums.org/showthread.php?t=1569675](http://ubuntuforums.org/showthread.php?t=1569675)

> If your /home is on a seperate partition, start the installer - pick manual at the partition stage.

Select the existing / partition - Edit partition - Use as ext4,format and Mountpoint - / then save/close that window

Select the existing /home partition - Edit partition - Use as whatever it was previously, DO NOT FORMAT and Mountpoint /home - save and close that window

Check that the only partition that is going to be formatted is the existing / partition.

Carry on - that will install over the existing installation and use the old /home.

Use the same username though.

---

### Post by 3rdalbum on 2012-12-05
> **sdowney717 said:**
> appears this can be done
should be able to copy /home to that partition. then resize and install 64 bit

[http://ubuntuforums.org/showthread.php?t=1569675](http://ubuntuforums.org/showthread.php?t=1569675)

Note, you can follow these instructions even if your /home is on the same partition as /

Just make sure you don't elect to format anything and your /home will be preserved. Yes, your settings and e-mails from 32-bit Ubuntu will work perfectly on 64-bit Ubuntu as there's nothing in them that depends on CPU architecture (i.e. you could transfer them to an ARM or SPARC or Itanium machine and they would work).

---

### Post by sdowney717 on 2012-12-05
finished copying my /home
now on to next step

> scott@scott-P5QC:~$ sudo cp -Rp /home /media/0db1fb5a-0727-4347-bfa7-a551d8db6632
[sudo] password for scott: 
cp: cannot stat `/home/scott/.gvfs': Permission denied
scott@scott-P5QC:~$ 

---

### Post by sdowney717 on 2012-12-05
I must have made an error :confused:

When I logged in after making all the changes, yes it is using the /home partition.
BUT it created another 'scott' user

Wow, at first I thought everything was gone, but it is not gone.

How do I tell it to use my old scott???
Serously?

The home folder has my old 3 users inside.
scott tricia tom

I need these back

---

### Post by oldfred on 2012-12-05
I have never fully comprehended when a trailing slash is required or not. It determines which level you are copying. 

I believe each user or name should be at the top level in the /home partition or just seen as folders when viewed unmounted as /home. Then that folder is mounted as /home in fstab and has steve or all the other users (folders) at the next level only when mounted so it is /home/steve. 

Best just to copy commands from.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
If copying /home into NTFS you will lose permissions & ownership, but for /home you can reset if needed. 
       Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

    
If dual booting with Windows, I suggest a somewhat smaller Windows and a shared NTFS data partition for data you want to share. Then set the Windows system partition as Read-Only to avoid accidents or issues.
You can just leave some unallocated on your drive if not sure what to use it for. Just include all of the unallocated in the extended partition so you can make more partitions. I kept adding 25GB / (root) partitions for test installs or next versions.

---

### Post by sdowney717 on 2012-12-05
apparently this command from the how to geek site is wrong
> sudo cp -Rp /home/* /mount/location

as it puts /home folder name onto the partition!
surprise surprise.

Listen as a test I tried copying the user folder 'tom'
over into the higher level. I got various errors saying could not copy special files like gpg ssh control etc...

I used gksu nautilus (that gave errors opening as well)
After the copy  I set up 'tom' as a new user with admin rights
 
Then when I logged out of bogus new scott user, and logged into copied over "tom", it gave no error, screen goes black for a few seconds and comes right back to the user login page

So I am busted wondering what to do for now. I can move forward likely by just starting over with tom and tricia and copy and paste etc...
But user scott has a lot more details and history.

Anyone know what I can do to remedy this?

Start over completely?

Is there a copy command that will work?

picture shows the 'tom' user copied next to the user 'scott' that the install created.

If I rebooted the LIVE usb, could I copy those folders into the right spot, delete the bogus 'scott'  user and substitute my old user?

---

### Post by sdowney717 on 2012-12-05
well, the Lve USB can not copy the folder 'tom' due to special files

any thoughts on what to do here?

---

### Post by sdowney717 on 2012-12-05
ok since gksu nautilus coughs loudly, I did the manual copy command
which terminates with no error in the live USB.
this also preserved the permissions as far as I can tell which is good

> ubuntu@ubuntu:~$ sudo cp  -Rp /media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/tom /media/0db1fb5a-0727-4347-bfa7-a551d8db6632 
ubuntu@ubuntu:~$ 


Now I will reboot and try to add a user 'tom' and see if it can log in to 'tom'

---

### Post by sdowney717 on 2012-12-05
OK it is working for both 'tom' and 'tricia' doing this!
):P

So now will get to do the huge 'scott' user.
gksu nautilus will not work, you will have to do a manual copy name using the mount location and uuid of the partition. You can get uuid from the nautilus properties page.

instead of cp, how about using mv ?????? for this 40gb in size user 'scott'

---

### Post by oldfred on 2012-12-05
I prefer the rsync, but this has an example with cp.

[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

Are you copying directly from your /home or the backup that is on a NTFS partition? If from the backup you have lost ownership & permissions and have to reset them.

---

### Post by sdowney717 on 2012-12-05
sort of a disaster happened.
I did a copy not a move on 'scott'
Totally ran out of space 0 bytes.
So I deleted the copy.
Then I still had zero bytes

So I found them in .Trash

I deleted the trash by shift-del key and got the space back.

BUT, It deleted what I was copying from and kept the copy to files and now I dont even know what is missing if anything. It shows 43gb in 'scott' 

Now when I started the cp command, I had looked at the folder in nautilus and it said 22gb (with some content unreadable!)

So I had 50gb free and though it would copy, boy was I wrong, it took it right down to zero. I am sure few of you even can really understand what I am talking about, I deleted the copy not the original using gksu nautilus and it seems to have done the opposite. Who knows what happened. I am shocked.

so the folder was in located like .local Trash scott and am trying testdisk to see what comes up if anything.

And this whole damned thing happened because some geekfest website put out a copy command that puts home in a /home subfolder which the ubuntu installer simply ignored and set up a new 'scott' user!

---

### Post by sdowney717 on 2012-12-05
following the early on procedure to reinstall things shows a lot of items!

```
scott@scott-P5QC:~$ sudo apt-get dselect-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  at cron gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-ugly gvfs-fuse libavutil51 libdirectfb-1.2-9
  libdvdnav4 libdvdread4 libevent-2.0-5 libflite1 libgpod-common
  libindicate-gtk3 libzbar0 telepathy-indicator transmission-gtk
  ubuntu-desktop ubuntu-standard xorg xserver-xorg-input-all
  xserver-xorg-input-mouse xserver-xorg-input-vmmouse zip
The following NEW packages will be installed:
  akonadi-backend-mysql apache2.2-bin:i386 arj:i386 at:i386 autotools-dev
  binfmt-support bison:i386 bogofilter-common c2esp ca-certificates-java
  cabextract cdck:i386 cdparanoia:i386 cdrdao:i386 checkbox-gtk cheese-common
  cli-common cmap-adobe-japan1 comerr-dev:i386 computer-janitor
  computer-janitor-gtk cpp-4.5:i386 cron:i386 cups-driver-gutenprint curl
  dconf-gsettings-backend:i386 dconf-tools:i386 debhelper defoma
  desktop-webmail:i386 dh-apparmor diffstat dkms dmucs:i386 docbook
  docbook-xml docbook-xsl dpkg-dev esound-common evolution-common
  evolution-webcal execstack:i386 fakeroot flac:i386 flex:i386 fonts-droid
  fonts-horai-umefont fonts-unfonts-core foo2zjs foxtrotgps:i386
  freedroidrpg-data fuse-utils galculator gamin:i386 gbrainy gcc-4.5-base
  gcc-4.5-base:i386 gcc-4.6-base:i386 gconf-defaults-service gettext
  giblib1:i386 gimp-data git-man glib-networking:i386 gnome-desktop-data
  gnome-doc-utils gnome-mag:i386 gnome-mime-data gnome-search-tool:i386
  gnome-themes-ubuntu gnome-tweak-tool gpicview gpsbabel:i386 gpsbabel-doc
  gpsd gpsdrive gpsdrive-data graphviz:i386 gstreamer0.10-alsa:i386
  gstreamer0.10-fluendo-mp3:i386 gstreamer0.10-gnonlin
  gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386
  gstreamer0.10-x:i386 gtk-recordmydesktop gtk2-engines:i386
  gtk2-engines-pixbuf gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386
  hal-info hpijs hplip-cups html2text htop:i386 hunspell-en-ca
  icedtea-6-jre-cacao icedtea-6-jre-cacao:i386 icedtea-6-jre-jamvm
  icedtea-6-jre-jamvm:i386 icedtea-7-jre-jamvm icedtea-7-jre-jamvm:i386
  icedtea-7-plugin icedtea-7-plugin:i386 icedtea-netx icedtea-netx:i386
  icedtea-netx-common icoutils imagemagick-common intltool-debian jadetex
  java-common k3b-data k3b-extrathemes kate-data kde-baseapps-data
  kde-runtime-data kde-wallpapers-default kde-workspace-data
  kde-workspace-kgreet-plugins:i386 kdelibs5-data krb5-multidev:i386
  ksysguardd:i386 lacheck latex-beamer latex-xcolor leafpad lib32z1
  libaa1:i386 libaacs0 libaacs0:i386 libacl1:i386 libakonadi-kabc4:i386
  libakonadi-notes4:i386 libakonadiprotocolinternals1 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libamd2.2.0:i386
  libao-common libao4 libao4:i386 libapache2-mod-dnssd:i386 libapparmor1:i386
  libappindicator0.1-cil libapr1:i386 libaprutil1:i386
  libaprutil1-dbd-sqlite3:i386 libaprutil1-ldap:i386 libapt-inst1.4:i386
  libapt-pkg-perl libapt-pkg4.12:i386 libart-2.0-2:i386 libart2.0-cil
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-dev:i386 libasyncns0:i386
  libatk-wrapper-java libatk-wrapper-java-jni libatk-wrapper-java-jni:i386
  libatk1.0-0:i386 libatkmm-1.6-1:i386 libatm1 libatm1:i386 libatspi1.0-0:i386
  libattica0.3:i386 libattr1:i386 libaudio2:i386 libaudiofile1
  libaudiofile1:i386 libavahi-client-dev:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common-dev:i386 libavahi-common3:i386
  libavahi-glib1:i386 libavahi-gobject0:i386 libavahi-ui-gtk3-0:i386
  libavahi-ui0 libavahi-ui0:i386 libavc1394-0:i386 libavfilter2
  libavutil-extra-51 libavutil-extra-51:i386 libbison-dev libbison-dev:i386
  libblas3gf:i386 libblkid1:i386 libbluetooth3:i386 libbluray1 libbluray1:i386
  libbonobo2-0 libbonobo2-0:i386 libbonobo2-common libbonoboui2-0
  libbonoboui2-0:i386 libbonoboui2-common libboost-filesystem1.46.1:i386
  libboost-program-options1.46.1 libboost-system1.46.1:i386 libbsd0:i386
  libbz2-1.0:i386 libc6:i386 libc6-dbg libc6-dbg:i386 libc6-dev:i386
  libc6-i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386
  libcairomm-1.0-1:i386 libcanberra-gtk3-0:i386 libcanberra-gtk3-module:i386
  libcanberra0:i386 libcap2:i386 libcapi20-3 libcapi20-3:i386 libcapi20-dev
  libcapi20-dev:i386 libcddb2:i386 libcdparanoia0:i386 libcdt4:i386
  libcgraph5:i386 libcheese-gtk21 libcheese3 libchromaprint0 libcitadel2:i386
  libclass-accessor-perl libclass-factory-util-perl libclass-load-perl
  libclass-singleton-perl libcln6:i386 libclone-perl libcloog-ppl0
  libcloog-ppl0:i386 libclucene0ldbl:i386 libclutter-1.0-0:i386
  libcogl-pango0:i386 libcogl9:i386 libcolamd2.7.1:i386 libcolord1:i386
  libcomerr2:i386 libconfig-inifiles-perl libcroco3:i386 libcrystalhd3:i386
  libcups2:i386 libcups2-dev:i386 libcupsimage2:i386 libcurl3:i386
  libcurl3-gnutls:i386 libcurl3-nss:i386 libdata-optlist-perl
  libdate-manip-perl libdatetime-format-builder-perl
  libdatetime-format-iso8601-perl libdatetime-format-strptime-perl
  libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl
  libdatrie1:i386 libdb4.8 libdb4.8:i386 libdb5.1:i386 libdbus-1-3:i386
  libdbus-1-dev:i386 libdbus-glib-1-2:i386 libdbus-glib1.0-cil libdbus1.0-cil
  libdbusmenu-glib4:i386 libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386
  libdbusmenu-qt2:i386 libdc1394-22:i386 libdconf0:i386 libdigest-hmac-perl
  libdiscid0:i386 libdlrestrictions1:i386 libdmtx0a:i386 libdpkg-perl
  libdrm-dev:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libdrm2:i386 libdv4:i386 libdvbpsi7:i386 libdvdnav-dev:i386 libdvdnav4:i386
  libdvdread-dbg:i386 libdvdread-dev:i386 libdvdread4:i386 libebml3
  libebml3:i386 libechonest1.2 libechonest1.2:i386 libelf1:i386 libelfg0:i386
  libemail-valid-perl libencode-locale-perl libept1.4.12 liberror-perl libesd0
  libesd0:i386 libevent-1.4-2:i386 libevent-2.0-5:i386 libexif12:i386
  libexpat1:i386 libexpat1-dev:i386 libfaac0:i386 libffi6:i386
  libfile-listing-perl libfile-slurp-perl libfl-dev libfl-dev:i386 libflac++6
  libflac++6:i386 libflac8:i386 libflickcurl0:i386 libflite1:i386 libfm-data
  libfont-afm-perl libfontconfig1:i386 libfontconfig1-dev:i386
  libfreetype6:i386 libfreetype6-dev:i386 libfreezethaw-perl libftgl2:i386
  libgadu3:i386 libgail-3-0:i386 libgail18:i386 libgamin0:i386 libgavl1
  libgavl1:i386 libgcc1:i386 libgconf-2-4:i386 libgconf2-4:i386
  libgconf2.0-cil libgcrypt11:i386 libgcrypt11-dev:i386 libgd2-xpm:i386
  libgdata1.9-cil libgdbm3:i386 libgdiplus libgdk-pixbuf2.0-0:i386
  libgee2:i386 libgettextpo0 libgettextpo0:i386 libgif-dev:i386 libgif4
  libgif4:i386 libgimp2.0:i386 libgkeyfile1.0-cil libgl1-mesa-dev:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglade2-0 libglade2-0:i386
  libglapi-mesa:i386 libglew1.5:i386 libglewmx1.5:i386 libglib2.0-0:i386
  libglib2.0-cil libglib2.0-dev:i386 libglibmm-2.4-1c2a:i386 libglu1-mesa:i386
  libglu1-mesa-dev:i386 libgmime2.6-cil libgmlib0 libgmlib0:i386 libgmp10:i386
  libgmp3c2:i386 libgmpxx4ldbl libgmpxx4ldbl:i386 libgmtk0 libgmtk0:i386
  libgmtk0-data libgnome-desktop-2-17:i386 libgnome-keyring0:i386
  libgnome-mag2:i386 libgnome-vfs2.0-cil libgnome2-0 libgnome2-0:i386
  libgnome2-bin libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-0:i386 libgnomecanvas2-common libgnomeui-0
  libgnomeui-0:i386 libgnomeui-common libgnomevfs2-0 libgnomevfs2-0:i386
  libgnomevfs2-common libgnomevfs2-extra libgnomevfs2-extra:i386
  libgnutls-dev:i386 libgnutls-openssl27 libgnutls-openssl27:i386
  libgnutls26:i386 libgnutlsxx27 libgnutlsxx27:i386 libgomp1:i386
  libgoocanvas-common libgpg-error-dev:i386 libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgps20 libgps20:i386
  libgraph4:i386 libgraphite3:i386 libgsl0ldbl:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgssglue1:i386 libgssrpc4 libgssrpc4:i386
  libgstreamer-plugins-bad0.10-0:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk-3-0:i386 libgtk-sharp-beans-cil
  libgtk-vnc-1.0-0:i386 libgtk-vnc-2.0-0:i386 libgtk2-gladexml-perl
  libgtk2.0-0:i386 libgtk2.0-cil libgtkhtml-4.0-common
  libgtkhtml-editor-common libgtkhtml3.14-19:i386 libgtksourceview2.0-common
  libgudev-1.0-0:i386 libgudev1.0-cil libgvc5:i386 libgvnc-1.0-0:i386
  libgvpr1:i386 libhal-storage1:i386 libhal1:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhttp-server-simple-perl
  libhunspell-1.3-0:i386 libhx509-5-heimdal:i386 libice-dev:i386 libice6:i386
  libid3tag0:i386 libidl0:i386 libidn11:i386 libido-0.1-0:i386
  libiec61883-0:i386 libieee1284-3:i386 libieee1284-3-dev:i386
  libilmbase6:i386 libimlib2:i386 libio-pty-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libio-string-perl libipc-run-perl
  libjack-jackd2-0:i386 libjasper1:i386 libjpeg-dev libjpeg-progs
  libjpeg-turbo-progs libjpeg-turbo8:i386 libjpeg-turbo8-dev
  libjpeg-turbo8-dev:i386 libjpeg62 libjpeg62:i386 libjpeg8:i386 libjpeg8-dev
  libjpeg8-dev:i386 libjson-glib-1.0-0:i386 libjson0:i386 libk5crypto3:i386
  libkadm5clnt-mit8 libkadm5clnt-mit8:i386 libkadm5srv-mit8
  libkadm5srv-mit8:i386 libkcmutils4:i386 libkdb5-6 libkdb5-6:i386
  libkdeclarative5:i386 libkdecorations4:i386 libkdecore5:i386 libkdeui5:i386
  libkdnssd4:i386 libkephal4abi1:i386 libkeyutils1:i386 libkholidays4:i386
  libkidletime4:i386 libkimap4:i386 libkipi-data libkjsapi4:i386
  libkjsembed4:i386 libkldap4:i386 libkmbox4:i386 libkmime4:i386 libkms1
  libkms1:i386 libkntlm4:i386 libkonq5-templates libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5-dev:i386 libkrb5support0:i386 libkresources4:i386
  libkrosscore4:i386 libkscreensaver5:i386 libksgrd4:i386
  libksignalplotter4:i386 libkunitconversion4:i386 libkwineffects1abi3:i386
  libkwinglutils1:i386 libkwinnvidiahack4:i386 liblastfm0:i386
  liblaunchpad-integration1 liblcms1:i386 liblcms1-dev liblcms1-dev:i386
  liblcms2-2:i386 libldap-2.4-2:i386 libldap2-dev libldap2-dev:i386
  liblensfun-data liblist-moreutils-perl libllvm3.0:i386 liblockfile1:i386
  liblqr-1-0:i386 libltdl-dev libltdl-dev:i386 libltdl7:i386 liblua5.1-0:i386
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblzma5:i386 liblzo2-2
  liblzo2-2:i386 libmad0:i386 libmail-sendmail-perl libmailtools-perl
  libmath-round-perl libmatroska5:i386 libmenu-cache1:i386 libmikmod2
  libmikmod2:i386 libmldbm-perl libmlt-data libmng1:i386
  libmodule-runtime-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-corlib2.0-cil
  libmono-corlib4.0-cil libmono-csharp4.0-cil libmono-i18n-west2.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-management2.0-cil
  libmono-management4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil
  libmono-security2.0-cil libmono-security4.0-cil libmono-sharpzip2.84-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system2.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libmp3lame0:i386 libmpc2:i386 libmpfr4:i386 libmpg123-0 libmpg123-0:i386
  libmpg123-dev libmpg123-dev:i386 libmysqlclient18 libmysqlclient18:i386
  libncurses5:i386 libncurses5-dev:i386 libncursesw5:i386
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-daemon-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl
  libnet-ssleay-perl libnetpbm10:i386 libnfsidmap2:i386 libnl1 libnl1:i386
  libnotify0.4-cil libnotify4:i386 libnspr4:i386 libnss3:i386 libnss3-1d:i386
  liboauth0:i386 libobt0 libodbc1 libodbc1:i386 libogg0:i386 liboil0.3:i386
  libopenal-dev:i386 libopenal1:i386 libopencv-core2.3:i386
  libopencv-flann2.3:i386 libopencv-imgproc2.3:i386 libopenexr6:i386
  libopenjpeg2:i386 libopenraw1:i386 libopenspc0:i386 liborbit2:i386
  liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libosmesa6-dev:i386
  libosp5:i386 libostyle1c2:i386 libp11-kit-dev:i386 libp11-kit0:i386
  libpackage-deprecationmanager-perl libpackage-stash-perl
  libpackage-stash-xs-perl libpam-modules:i386 libpam-smbpass
  libpam-smbpass:i386 libpam-winbind libpam-winbind:i386 libpam0g:i386
  libpango1.0-0:i386 libpangomm-1.4-1:i386 libparams-classify-perl
  libparams-util-perl libparams-validate-perl libparse-debianchangelog-perl
  libpathplan4:i386 libpcap0.8:i386 libpci3:i386 libpciaccess0:i386
  libpcre3:i386 libpcre3-dev:i386 libpcrecpp0 libpcrecpp0:i386
  libpcsclite1:i386 libphonon4 libphonon4:i386 libpipeline1:i386
  libpixman-1-0:i386 libplasma-geolocation-interface4:i386 libplrpc-perl
  libpng12-0:i386 libpng12-dev:i386 libpod-plainer-perl
  libpolkit-agent-1-0:i386 libpolkit-gobject-1-0:i386 libpolkit-qt-1-1:i386
  libpoppler19:i386 libpopt0:i386 libpostproc52:i386 libppl-c4 libppl-c4:i386
  libppl9 libppl9:i386 libprison0:i386 libprocesscore4abi1:i386
  libprocessui4a:i386 libproxy1:i386 libpst4 libpst4:i386 libpthread-stubs0
  libpthread-stubs0:i386 libpthread-stubs0-dev libpthread-stubs0-dev:i386
  libpulse-dev:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libpwl5
  libpwl5:i386 libqalculate5:i386 libqca2:i386 libqimageblitz4:i386 libqjson0
  libqjson0:i386 libqrencode3:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386
  libqt4-qt3support libqt4-qt3support:i386 libqt4-script:i386 libqt4-sql:i386
  libqt4-sql-mysql libqt4-sql-mysql:i386 libqt4-sql-sqlite:i386
  libqt4-svg:i386 libqt4-webkit:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 libquadmath0:i386
  libqxt-core0:i386 libqxt-gui0:i386 libraptor1:i386 librarian0
  libraw1394-11:i386 libreadline6:i386 libreoffice-help-en-gb
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libresid-builder0c2a:i386
  libroken18-heimdal:i386 librpc-xml-perl librpm2 librpmbuild2 librpmio2
  librpmsign0 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386
  libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl-image1.2 libsdl-image1.2:i386 libsdl-mixer1.2 libsdl-mixer1.2:i386
  libsdl1.2debian:i386 libselinux1:i386 libsensors4:i386 libsepol1
  libsepol1:i386 libsgmls-perl libshout3:i386 libsidplay2:i386
  libsieve2-1:i386 libsigc++-2.0-0c2a:i386 libslang2:i386 libsm-dev:i386
  libsm6:i386 libsmbclient:i386 libsndfile1:i386 libsocket6-perl
  libsolid4:i386 libsolidcontrol4abi2:i386 libsolidcontrolifaces4abi2:i386
  libsoundtouch0:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsp1c2
  libspeex1:i386 libspeexdsp1:i386 libspiro0:i386 libsqlite3-0:i386
  libssh-4:i386 libssl-dev:i386 libssl-doc libssl0.9.8 libssl0.9.8:i386
  libssl1.0.0:i386 libstartup-notification0:i386 libstdc++6:i386
  libstlport4.6ldbl:i386 libstreams0:i386 libsub-install-perl libsub-name-perl
  libswscale2:i386 libsys-hostname-long-perl libtag1-vanilla:i386
  libtag1c2a:i386 libtaglib2.0-cil libtalloc2:i386 libtar0:i386
  libtasn1-3:i386 libtasn1-3-dev:i386 libtdb1:i386 libtextcat-data
  libthai0:i386 libtheora0:i386 libthreadweaver4:i386 libtie-ixhash-perl
  libtiff-tools:i386 libtiff4:i386 libtiff4-dev:i386 libtiffxx0c2
  libtiffxx0c2:i386 libtimedate-perl libtinfo-dev libtinfo-dev:i386
  libtinfo5:i386 libtinyxml2.6.2:i386 libtirpc1:i386 libtool libtry-tiny-perl
  libts-0.0-0:i386 libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386 libudev0:i386
  libumfpack5.4.0:i386 libuninameslist0:i386 libunique-1.0-0:i386
  libunistring0:i386 libupnp3:i386 liburi-perl libusb-0.1-4:i386
  libusb-1.0-0:i386 libusb-dev:i386 libuser1:i386 libuuid1:i386 libv4l-0:i386
  libv4l-dev:i386 libv4lconvert0:i386 libva-x11-1 libva-x11-1:i386 libva1:i386
  libvdpau1 libvdpau1:i386 libvirtodbc0 libvisual-0.4-0:i386
  libvisual-0.4-plugins:i386 libvo-aacenc0:i386 libvo-amrwbenc0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libvte-common
  libvte9 libwacom2:i386 libwavpack1:i386 libwbclient0:i386
  libwebkitgtk-1.0-common libwildmidi1:i386 libwind0-heimdal:i386
  libwrap0:i386 libwww-curl-perl libwww-mechanize-perl libwww-perl
  libwww-robotrules-perl libwxbase2.8-0 libwxbase2.8-0:i386 libwxgtk2.8-0
  libwxgtk2.8-0:i386 libx11-6:i386 libx11-dev libx11-dev:i386 libx11-doc
  libx11-xcb-dev:i386 libx11-xcb1:i386 libx264-120:i386 libxau-dev
  libxau-dev:i386 libxau6:i386 libxaw7:i386 libxcb-composite0
  libxcb-composite0:i386 libxcb-glx0:i386 libxcb-glx0-dev libxcb-glx0-dev:i386
  libxcb-keysyms1:i386 libxcb-randr0 libxcb-randr0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb-util0:i386 libxcb-xv0 libxcb-xv0:i386 libxcb1:i386
  libxcb1-dev libxcb1-dev:i386 libxcomposite-dev:i386 libxcomposite1:i386
  libxcursor-dev:i386 libxcursor1:i386 libxdamage-dev:i386 libxdamage1:i386
  libxdmcp-dev libxdmcp-dev:i386 libxdmcp6:i386 libxdo2:i386 libxext-dev:i386
  libxext6:i386 libxfixes-dev:i386 libxfixes3:i386 libxft2:i386 libxi-dev:i386
  libxi6:i386 libxinerama-dev:i386 libxinerama1:i386 libxkbfile1:i386
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-base-perl
  libxml-sax-expat-perl libxml-sax-perl libxml-simple-perl libxml-twig-perl
  libxml-writer-perl libxml-xpath-perl libxml2:i386 libxml2-dev
  libxml2-dev:i386 libxml2-utils libxmmsclient-glib1:i386 libxmmsclient6:i386
  libxmu6:i386 libxmuu1:i386 libxpm4:i386 libxrandr-dev:i386 libxrandr2:i386
  libxrender-dev:i386 libxrender1:i386 libxslt1-dev:i386 libxslt1.1:i386
  libxss1:i386 libxt-dev:i386 libxt6:i386 libxtst6:i386 libxv1:i386
  libxvidcore4:i386 libxxf86vm-dev:i386 libxxf86vm1:i386 libyaml-syck-perl
  libzbar0:i386 lintian linux-generic-pae:i386 linux-headers-3.2.0-23
  linux-headers-3.2.0-24 linux-headers-3.2.0-25 linux-headers-3.2.0-26
  linux-headers-3.2.0-27 linux-headers-3.2.0-30 linux-headers-3.2.0-31
  linux-headers-3.2.0-32 linux-headers-3.2.0-33
  linux-image-3.2.0-23-generic-pae:i386 linux-image-3.2.0-24-generic-pae:i386
  linux-image-3.2.0-25-generic-pae:i386 linux-image-3.2.0-26-generic-pae:i386
  linux-image-3.2.0-27-generic-pae:i386 linux-image-3.2.0-29-generic-pae:i386
  linux-image-3.2.0-30-generic-pae:i386 linux-image-3.2.0-31-generic-pae:i386
  linux-image-3.2.0-32-generic-pae:i386 linux-image-3.2.0-33-generic-pae:i386
  linux-image-3.2.0-34-generic-pae:i386 linux-image-generic-pae:i386
  linux-libc-dev:i386 lmodern lp-solve:i386 lsb-invalid-mta luatex
  lxappearance lxde-icon-theme lxdm lxinput:i386 lxmenu-data lxmusic:i386
  lxrandr lxsession:i386 lxsession-edit lxshortcut lxterminal lynx lynx-cur m4
  menu menu-xdg mesa-common-dev:i386 min12xxw mono-2.0-gac mono-4.0-gac
  mono-csharp-shell mono-gac mono-gmcs mono-runtime movixmaker-2
  mysql-client-core-5.5 mysql-common mysql-server-core-5.5 ncurses-term
  netpbm:i386 nmap:i386 normalize-audio:i386 ntfsprogs odbcinst
  odbcinst1debian2 odbcinst1debian2:i386 opencl-headers openjdk-6-jre
  openjdk-6-jre:i386 openjdk-6-jre-headless openjdk-6-jre-headless:i386
  openjdk-6-jre-lib openjdk-7-jre openjdk-7-jre:i386 openjdk-7-jre-headless
  openjdk-7-jre-headless:i386 openjdk-7-jre-lib openshot-doc openssh-server
  openstreetmap-map-icons-classic openstreetmap-map-icons-square oss-compat
  oss4-dev oxygen-cursor-theme oxygen-icon-theme p7zip-full patchutils
  pavucontrol pax perl-tk pgf phonon phonon:i386 phonon-backend-gstreamer
  phonon-backend-gstreamer:i386 pnm2ppa po-debconf prelink:i386 projectm-data
  prosper ps2eps ptouch-driver pulseaudio-esound-compat:i386 pxljr
  python-aptdaemon-gtk python-aptdaemon.gtkwidgets python-central
  python-glade2 python-launchpad-integration python-paramiko python-support
  python-telepathy python-vte python-wsgi-intercept python3.2-minimal:i386
  rar:i386 rarian-compat rastertosag-gdi rdesktop:i386 recordmydesktop
  rpm-common rpm2cpio samba screen-resolution-extra screensaver-default-images
  scrot:i386 setcd:i386 sgml-data sgmlspl shared-desktop-ontologies sp splix
  ssh ssh-import-id synaptic tcl tcl8.4:i386 tcl8.5 tdb-tools:i386 tex-common
  texlive-base texlive-binaries texlive-common texlive-doc-base
  texlive-extra-utils texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base
  texlive-latex-base-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pstricks
  texlive-pstricks-doc tipa ttf-aenigma ttf-dejavu-extra ttf-droid
  ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation
  ttf-mscorefonts-installer ttf-opensymbol ttf-takao-pgothic ttf-thai-tlwg
  ttf-umefont ttf-unfonts-core tzdata-java ubuntuone-control-panel-gtk
  unity-2d-launcher unity-2d-places unity-place-applications unity-place-files
  unixodbc unixodbc-dev:i386 unrar:i386 valgrind:i386 viking:i386
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  vlc-data vorbis-tools:i386 winbind:i386 wine-gecko1.4 wine-gecko1.4:i386
  wireless-crda:i386 x-ttcidfont-conf x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xarchiver
  xbase-clients xdotool:i386 xmms2-core:i386 xmms2-plugin-alsa:i386
  xmms2-plugin-id3v2:i386 xmms2-plugin-mad:i386 xmms2-plugin-vorbis:i386
  xorg-sgml-doctools xsane-common xscreensaver-data xscreensaver-gl:i386
  xsltproc xtrans-dev zeitgeist-extension-fts zip:i386 zlib1g:i386 zlib1g-dev
  zlib1g-dev:i386
0 upgraded, 1172 newly installed, 24 to remove and 0 not upgraded.
Need to get 1,556 MB of archives.
After this operation, 3,981 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by sdowney717 on 2012-12-05
I think I wont do that. Some of them might be waste of time and perhaps 32 bit stuff, like I see a whole list of kernels.

So far so good. the 64 bit version feels faster.
I dont seem to have lost any files and learned some things.
That chrome os from the first post is dead, does not work.

Mostly though gets me mad to follow online copy advice without thinking it could be wrong. And then to see the comments on that site saying how well it works, I just dont know what is up with that.

---

