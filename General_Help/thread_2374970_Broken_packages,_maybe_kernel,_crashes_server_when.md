---
title: "Broken packages, maybe kernel, crashes server when I try to repair"
date: 2017-10-20
forum: General Help
---

### Post by hiro24 on 2017-10-20
So this is a bit of an unusual problem. I have a PC running Ubuntu 16.04.2 LTS. Somewhere along the line I've picked up some tainted package or something.

Long story short, the server is stable. But I'm unable to install anything. If I try, I'm met w/ errors about needing to repair, etc, apt-get or dpkg, not sure on the wording exactly.

If I try a dpkg --configure -a; apt-get install -f it runs for about 5 or 6 minutes, then abruptly hard powers off the PC?! Here's the output from the last time I ran it.

```
root@Cerebrum:/# dpkg --configure -a; apt-get install -f
Setting up linux-firmware (1.157.11) ...
update-initramfs: Generating /boot/initrd.img-4.13.8-041308-generic
By using this application, you agree to our Privacy Policy, Terms of Use and End User License Agreement.
https://www.getsync.com/legal/privacy
https://www.getsync.com/legal/terms-of-use
https://www.getsync.com/legal/eula

Resilio Sync forked to background. pid = 9934
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
Can't lock pid file. It seems Resilio Sync is already running with pid 9934

dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  a11y-profile-manager-indicator acpi-support activity-log-manager adium-theme-ubuntu aisleriot
  app-install-data-partner apturl apturl-common baobab bluez-cups branding-ubuntu brltty checkbox-converged
  checkbox-gui cheese dc deja-dup dmz-cursor-theme espeak-data example-content fonts-guru fonts-guru-extra
  fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-lklug-sinhala fonts-lohit-guru fonts-noto-cjk
  fonts-sil-abyssinica fonts-sil-padauk fonts-symbola fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda
  fonts-tlwg-garuda-ttf fonts-tlwg-kinnari fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman fonts-tlwg-laksaman-ttf
  fonts-tlwg-loma fonts-tlwg-loma-ttf fonts-tlwg-mono fonts-tlwg-mono-ttf fonts-tlwg-norasi fonts-tlwg-norasi-ttf
  fonts-tlwg-purisa fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter
  fonts-tlwg-typewriter-ttf fonts-tlwg-typist fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf
  fonts-tlwg-umpush fonts-tlwg-umpush-ttf fonts-tlwg-waree fonts-tlwg-waree-ttf fwupd gedit gedit-common genisoimage
  gir1.2-atspi-2.0 gir1.2-gst-plugins-base-1.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-rb-3.0 gir1.2-secret-1
  gir1.2-udisks-2.0 gnome-accessibility-themes gnome-calendar gnome-font-viewer gnome-mahjongg gnome-mines gnome-orca
  gnome-screenshot gnome-session-canberra gnome-sudoku gnome-system-log gnome-video-effects
  gstreamer1.0-plugins-base-apps gucharmap gvfs-fuse ibus-table inputattach intel-gpu-tools kerneloops-daemon
  language-selector-gnome laptop-detect liba11y-profile-manager-0.1-0 liba11y-profile-manager-data libatk-adaptor
  libavahi-ui-gtk3-0 libcdr-0.1-1 libdfu1 libdmapsharing-3.0-2 libdotconf0 libedataserverui-1.2-1 libespeak1
  libevent-2.0-5 libexiv2-14 libfreehand-0.1-1 libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1
  libfreerdp-plugins-standard libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-common libgexiv2-2 libgpod-common
  libgpod4 libgsoap8 libminiupnpc10 libmspub-0.1-1 libnatpmp1 liborcus-0.10-0v5 libpagemaker-0.0-0
  libpeas-1.0-0-python3loader libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqqwing2v5 libqt4-opengl
  libraw15 libreoffice-calc libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-ogltrans libreoffice-pdfimport librhythmbox-core9 libsgutils2-2 libsonic0 libspeechd2 libssh-4
  libtcl8.6 libtk8.6 libunwind8 libvisio-0.1-1 libvncclient1 libvncserver1 libwhoopsie-preferences0 libwhoopsie0
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1
  libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1 libwinpr-pool0.1
  libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1
  libwinpr-utils0.1 light-themes linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-89 linux-image-4.4.0-62-generic
  linux-image-extra-4.4.0-62-generic media-player-info memtest86+ mscompress mtools nautilus-sendto nautilus-share
  onboard onboard-data plainbox-provider-checkbox plainbox-provider-resource-generic plainbox-secure-policy
  policykit-desktop-privileges pppconfig pppoeconf printer-driver-brlaser printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-foo2zjs-common printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio-module-bluetooth pyotherside
  python3-brlapi python3-checkbox-support python3-gi-cairo python3-guacamole python3-jinja2 python3-louis
  python3-mako python3-markupsafe python3-padme python3-plainbox python3-pyatspi python3-pyparsing python3-speechd
  python3-xlsxwriter qml-module-io-thp-pyotherside qmlscene qtdeclarative5-dev-tools remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc rfkill rhythmbox rhythmbox-data rhythmbox-plugin-zeitgeist rhythmbox-plugins
  seahorse shotwell shotwell-common simple-scan sni-qt speech-dispatcher speech-dispatcher-audio-plugins syslinux
  syslinux-common syslinux-legacy tcl tcl8.6 tk tk8.6 toshset transmission-common transmission-gtk
  ttf-ancient-fonts-symbola ubuntu-artwork ubuntu-settings ubuntu-software ubuntu-sounds ubuntu-wallpapers
  ubuntu-wallpapers-xenial unity-accessibility-profiles usb-creator-common usb-creator-gtk vino whoopsie
  whoopsie-preferences xbrlapi xcursor-themes xdg-user-dirs-gtk xdiagnose
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 322 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-firmware (1.157.11) ...
update-initramfs: Generating /boot/initrd.img-4.13.8-041308-generic

```

After sitting on the last line for about 2 or 3 minutes the server abruptly dies. Any suggestions would be appreciated.

---

### Post by Bashing-om on 2017-10-20
hiro24; Hey;

Let's poke at it with a sharp stick !
we have:
> 
.......installed, 0 to remove and 322 not upgraded.

so what results:
```

sudo apt update
sudo apt full-upgrade

```
where I will not be surprised  if " no space left on device" occurs .

[INDENT][INDENT]tidy is better
[/INDENT][/INDENT]

---

### Post by hiro24 on 2017-10-20
Plenty of space.

```
hiro@Cerebrum:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.9G     0  7.9G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sdb1       443G  162G  259G  39% /
tmpfs           7.9G  8.0K  7.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G  4.0K  1.6G   1% /run/user/108
tmpfs           1.6G     0  1.6G   0% /run/user/0

```

Can't do what you suggested. Result:

```
root@Cerebrum:~# apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:4 http://linux-packages.resilio.com/resilio-sync/deb resilio-sync InRelease
Hit:5 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:7 http://dl.google.com/linux/chrome/deb stable Release
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Fetched 306 kB in 2s (128 kB/s)
Reading package lists... Done
You have new mail in /var/mail/root
root@Cerebrum:~# apt-get full-upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

Followed by

```
root@Cerebrum:~# dpkg --configure -a
Setting up linux-firmware (1.157.11) ...
update-initramfs: Generating /boot/initrd.img-4.13.8-041308-generic
By using this application, you agree to our Privacy Policy, Terms of Use and End User License Agreement.
https://www.getsync.com/legal/privacy
https://www.getsync.com/legal/terms-of-use
https://www.getsync.com/legal/eula

Resilio Sync forked to background. pid = 10185
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic

```

Followed by power off.

---

### Post by ian-weisser on 2017-10-20
> **hiro24 said:**
> 
Resilio Sync forked to background. pid = 9934
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
Can't lock pid file. It seems Resilio Sync is already running with pid 9934


Try stopping Resilio Sync before starting apt actions, and restart when the package action is complete.

Looks like time for some maintenance there...

---

