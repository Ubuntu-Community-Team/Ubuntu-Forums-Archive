---
title: "sudo apt update &amp;&amp; sudo apt upgrade"
date: 2023-04-01
forum: General Help
---

### Post by Quarkrad on 2023-04-01
As an experiment I have put the relevant command in */etc/sudoers.d/config* such that no sudo password is asked and running a script with *sudo apt update && sudo apt upgrade* in it works in that no password is asked.  However, this is potentially dangerous (having said that this is a stand-alone Desktop only used daily by one user) and a 'little' belt-and-braces'.  What I would like to do is rather have a global *no sudo password* command in */etc/sudoers.d/config* is to have a specific NOPASSWD command just for *sudo apt update && sudo apt upgrade*.  So far I have not been able to find such a *user ALL+(ALL) NOPASSWD ???????* command that will do this.

---

### Post by TheFu on 2023-04-01
There is a warning about using **apt** in scripts. Best to heed that warning, lest something terrible happen.  
Also, whenever putting commands into sudo config files that won't require a password to run, please, please, please, specify the exact path of the program involved.  /usr/bin/apt-get - to prevent someone from screwing with their environment to gain root access by naming a different program with the same name.  Doing sudo in a secure way isn't easy.

I wouldn't allow all users the capability you are asking for.  But it you want to provide it to 1-2 users, that is easy. Add them to separate files.
```
thefu   ALL = NOPASSWD: (root) /usr/bin/apt-get upgrade,  (root) /usr/bin/apt-get update
```
I didn't test this.  There are examples in the sudoers manpage. Reviewing the caveats would be smart.

---

### Post by Quarkrad on 2023-04-03
No luck so far - I've been reading the man page and looking at examples but unfortunately I'm still stuck.

---

### Post by TheFu on 2023-04-03
> **Quarkrad said:**
> No luck so far - I've been reading the man page and looking at examples but unfortunately I'm still stuck.
Might it be helpful to post what you've tried and what did/didn't work?  Perhaps?  Maybe?

---

### Post by Quarkrad on 2023-04-03
This is what I am testing in a vm.

I have a simple bash script in /usr/bin/ called *backup.sh*

```
#!bin/bash
sudo apt update
sudo apt upgrade -y
```

I call that script via a customer launcher on my Desktop that has the following properties:

Type:            Application in Terminal
Command:   sh /usr/bin/backup.sh

note: I have Application in Terminal so that I can see what is happening.

When I run the backup.sh script I get a terminal, as expected, asking me for the sudo password.  When I enter the password the script runs and I get the equivalent of *sudo apt update* and *sudo apt upgrade*.

So, to try and not have to enter the password, I have created the config file in */etc/sudoers.d/* and tried a number of statements.

1.  **dad ALL = NOPASSWD: (root) /usr/bin/apt-get upgrade,  (root) /usr/bin/apt-get update**    I get this output:

```
/etc/sudoers.d/config:1:21: syntax error
dad ALL = NOPASSWD: (root) /usr/bin/apt-get upgrade,  (root) /usr/bin/apt-get update
                    ^
[sudo] password for dad: 

```

If I enter the password the script runs

2. **dad ALL = NOPASSWD: /usr/bin/apt-get upgrade, /usr/bin/apt-get update**    I get this output:

```
[sudo] password for dad: 
```

If I enter the password the script runs

3.  [B]dad ALL = NOPASSWD: /usr/bin/apt-get upgrade  ,  /usr/bin/apt-get update
[/B]
```
[sudo] password for dad: 
```

If I enter the password the script runs

---

### Post by TheFu on 2023-04-03
apt != apt-get.
Use apt-get in scripts.  Your scripts should always use the /full/path/to/all/commands inside them.  I'd strongly recommend against using the '-y' option.  Just 2 weeks ago, I was burned with normal patching that removed a bunch of tools from a system. Due to bad dependency solutions.  It removed ffmpeg, a bunch of ffmpeg-related libraries and some caption libraries.  AND I don't have -y enabled.  I just wasn't paying attention to the list of packages to be removed.  Further, I didn't notice it for a few days. While I could selectively restore from backups from before the updates, it was better that I used aptitude and rejected the first 8 (or so) offered dependency solutions, before one that included ffmpeg and some of the other libraries was provided.  apt and apt-get aren't smart enough to do that.  

If it is complaining about the (root), then remove that. There are plenty of examples in the manpage. EXAMPLES section.

---

### Post by Quarkrad on 2023-04-04
> If it is complaining about the (root), then remove that

I tried that in 2 and 3 above but nothing works, and I was using apt-get.

---

### Post by TheFu on 2023-04-04
In post #5 above, this is the script claimed to be used.  

> **Quarkrad said:**
> I have a simple bash script in /usr/bin/ called *backup.sh*

```
#!bin/bash
sudo apt update
sudo apt upgrade -y
```


So, I assumed you were using apt, not apt-get.
BTW, it is smarter to keep packaged programs and our custom programs/scripts separate.  That's the use for /usr/local/ ... for our local, system-wide, scripts.  I'm a little confused why a backup.sh would do APT maintenance and not backups, but you do you.

I just tested this.
```
thefu   ALL = NOPASSWD: /usr/bin/apt-get upgrade, /usr/bin/apt-get update
```
It works here. I really should reboot to ensure it is really working, but cannot, probably for a few days.

---

### Post by Quarkrad on 2023-04-05
That has certainly helped but unfortunately there is still a problem; the **-y** option after [I]sudo apt-get upgrade
[/I]
_With the -y option in backup.sh_

/usr/bin/backup.sh

```
#!bin/bash
sudo apt-get update
sudo apt-get upgrade -y
sleep 20s
```

/etc/sudoers.d/config

```
dad ALL = NOPASSWD: /usr/bin/apt-get upgrade, /usr/bin/apt-get update
```

terminal output

```
Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Reading package lists... Done                    
[sudo] password for dad: 

```

_Without the -y option in backup.sh_

```
#!bin/bash
sudo apt-get update
sudo apt-get upgrade
sleep 20s
```

/etc/sudoers.d/config

```
dad ALL = NOPASSWD: /usr/bin/apt-get upgrade, /usr/bin/apt-get update
```

terminal output

```
 Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  alsa-ucm-conf distro-info-data libegl-mesa0 libgbm1 libgl1-mesa-dri
  libglapi-mesa libglx-mesa0 libpulse-mainloop-glib0 libpulse0 libpulsedsp
  libxatracker2 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers
  pulseaudio pulseaudio-module-bluetooth pulseaudio-utils
The following packages will be upgraded:
  apparmor apport apport-gtk apt apt-utils base-files bind9-dnsutils
  bind9-host bind9-libs caja-extensions-common caja-open-terminal caja-sendto
  caja-wallpaper cryptsetup cryptsetup-bin cryptsetup-initramfs dmidecode
  dnsmasq-base evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugin-bogofilter
  evolution-plugin-pstimport evolution-plugins firmware-sof-signed
  fonts-noto-color-emoji fonts-opensymbol fwupd gdb gir1.2-gdkpixbuf-2.0
  gir1.2-gnomedesktop-3.0 gir1.2-pango-1.0 gjs gnome-control-center-faces
  gnome-desktop3-data gnome-maps google-chrome-stable gzip imagemagick
  imagemagick-6-common imagemagick-6.q16 initramfs-tools initramfs-tools-bin
  initramfs-tools-core isc-dhcp-client isc-dhcp-common kbd
  language-selector-common language-selector-gnome libapparmor1 libapt-pkg6.0
  libcamel-1.2-63 libcryptsetup12 libdrm-amdgpu1 libdrm-common libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libebackend-1.2-10 libebook-1.2-20
  libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-26 libedataserverui-1.2-3 libevolution
  libfwupd2 libfwupdplugin5 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin
  libgdk-pixbuf2.0-common libgjs0g libglib2.0-0 libglib2.0-bin libglib2.0-data
  libgnome-desktop-3-19 libinput-bin libinput10 libldap-2.5-0 libldap-common
  libldb2 liblouis-data liblouis20 libmagickcore-6.q16-6
  libmagickcore-6.q16-6-extra libmagickwand-6.q16-6 libmbim-glib4
  libmbim-proxy libmm-glib0 libnetplan0 libnftables1 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpipewire-0.3-0
  libpipewire-0.3-common libpipewire-0.3-modules libpython3-stdlib
  libqmi-glib5 libqmi-proxy libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5widgets5 libreoffice-base-core libreoffice-calc libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk3 libreoffice-help-common
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-impress
  libreoffice-l10n-en-gb libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-colibre libreoffice-style-elementary
  libreoffice-style-yaru libreoffice-writer libsasl2-2 libsasl2-modules
  libsasl2-modules-db libsasl2-modules-gssapi-mit libsmbclient libsnmp-base
  libsnmp40 libspa-0.2-modules libspeechd2 libuno-cppu3
  libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3
  libuno-salhelpergcc3-3 libwbclient0 lintian linux-firmware modemmanager
  netplan.io nftables openssh-client openvpn pipewire pipewire-bin
  python-apt-common python3 python3-apport python3-apt python3-distupgrade
  python3-gdbm python3-ldb python3-lib2to3 python3-louis python3-minimal
  python3-problem-report python3-samba python3-software-properties
  python3-speechd python3-uno python3-update-manager qt5-gtk-platformtheme
  qt5-xdgdesktopportal-platformtheme samba-common samba-common-bin
  samba-dsdb-modules samba-libs smbclient snapd software-properties-common
  software-properties-gtk speech-dispatcher speech-dispatcher-audio-plugins
  speech-dispatcher-espeak-ng tcpdump thermald ubuntu-advantage-desktop-daemon
  ubuntu-advantage-tools ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk uno-libs-private update-manager
  update-manager-core update-notifier update-notifier-common ure vim-common
  vim-tiny xdg-utils xserver-xorg-video-amdgpu xxd
197 to upgrade, 0 to newly install, 0 to remove and 17 not to upgrade.
22 standard security updates
Need to get 0 B/534 MB of archives.
After this operation, 20.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```

---

