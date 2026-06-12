---
title: "Long time to boot"
date: 2013-03-20
forum: General Help
---

### Post by ibrahim52 on 2013-03-20
I remember when I did my fresh installation on my new laptop Lenovo g580, the boot time was less than 14 seconds but now it has reach to 27 seconds and after splash screen I see fsck check as well. Is there any way to trace down the boot logs and speed up the boot process ?

---

### Post by c2tarun on 2013-03-20
> **ibrahim52 said:**
> I remember when I did my fresh installation on my new laptop Lenovo g580, the boot time was less than 14 seconds but now it has reach to 27 seconds and after splash screen I see fsck check as well. Is there any way to trace down the boot logs and speed up the boot process ?

Please check your startup applications. Also did you install any servers like openfire, apache or any other which automatically start as your system start.
Start up applications are mostly responsible for this. If you are on Ubuntu 12.04 or more then most of your startup applications are hidden from UI "Startup Applications". Please check for the files in /etc/xdg/X11/autostart. Don't remove any file unless you are very sure that you don't need it during startup. You can also share your list here, we'll try to help.

---

### Post by ibrahim52 on 2013-03-21
at-spi-dbus-bus.desktop
bluetooth-applet.desktop
bluetooth-applet-unity.desktop
deja-dup-monitor.desktop
gnome-fallback-mount-helper.desktop
gnome-keyring-gpg.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-screensaver.desktop
gnome-settings-daemon.desktop
gnome-sound-applet.desktop
gnome-user-share.desktop
gsettings-data-convert.desktop
gwibber.desktop
nautilus-autostart.desktop
nm-applet.desktop
onboard-autostart.desktop
orca-autostart.desktop
polkit-gnome-authentication-agent-1.desktop
print-applet.desktop
pulseaudio.desktop
pulseaudio-kde.desktop
telepathy-indicator.desktop
ubuntuone-launch.desktop
update-notifier.desktop
user-dirs-update-gtk.desktop
vino-server.desktop
zeitgeist-datahub.desktop



According to UI application it is just PIDGIN and REMMINA

---

### Post by ibrahim52 on 2013-03-21
One more thing , FSCK also keeps running after splash screen, which takes more time to boot. I don't want to disable it but I used to have quick boot and safe Ubuntu. That's what I am looking for again.

---

### Post by tubbygweilo on 2013-03-21
> **c2tarun said:**
> Please check your startup applications. Also did you install any servers like openfire, apache or any other which automatically start as your system start.
Start up applications are mostly responsible for this. If you are on Ubuntu 12.04 or more then most of your startup applications are hidden from UI "Startup Applications". Please check for the files in /etc/xdg/X11/autostart. Don't remove any file unless you are very sure that you don't need it during startup. You can also share your list here, we'll try to help.

Useful information as I've often wondered where they were hidden.

Thanks.

---

### Post by rnerwein on 2013-03-21
> **ibrahim52 said:**
> I remember when I did my fresh installation on my new laptop Lenovo g580, the boot time was less than 14 seconds but now it has reach to 27 seconds and after splash screen I see fsck check as well. Is there any way to trace down the boot logs and speed up the boot process ?
hi
sorry i can't be back off. 14 to 27 seconds - this must be a apocalypse. my opinion is: better for you to: :popcorn:
but have fun
cears

---

### Post by ibrahim52 on 2013-03-21
> **rnerwein said:**
> hi
sorry i can't be back off. 14 to 27 seconds - this must be a apocalypse. my opinion is: better for you to: :popcorn:
but have fun
cears

hahaha lol, trust me I literally start "yawning" sometimes. if its Windows then it seems valid I can even take a bath and come back to use the desktop :p but Ubuntu is "quick" and if its slow then somethings wrong.

---

### Post by tgalati4 on 2013-03-21
Bootchart will help visualize the booting process.  If the fsck happening because your disk is having a problem?  Linux requires a clean filesystem before booting.  If your filesystem is unclean (now a different problem to troubleshoot) then fsck will take some time to check the integrity of the inode tables and overall health of the filesystem before booting.

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache search bootchart
bootchart - boot sequence auditing
pybootchartgui - boot sequence visualisation

---

### Post by ibrahim52 on 2013-03-22
So should I install and run it after a boot ?

---

### Post by ibrahim52 on 2013-03-28
This is what comes up during the boot between splash screen and the login screen. It stays for 10 seconds atleast processing everything.

---

### Post by ibrahim52 on 2013-03-31
**these are the logs of boot.log**

> fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda4: clean, 396900/1875968 files, 1897514/7500032 blocks
/dev/sda7: clean, 59939/15630336 files, 48982415/62499840 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [170G
[164G[ OK ]
 * Setting sensors limits       [170G
[164G[ OK ]
 * Starting mDNS/DNS-SD daemon[164G[ OK ]
 * Starting bluetooth daemon[164G[ OK ]
 * Starting Name Service Cache Daemon nscd       [170G
[164G[ OK ]
 * Stopping System V initialisation compatibility[164G[ OK ]
 * Starting System V runlevel compatibility[164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting save kernel messages[164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting TeamViewer remote control daemon[164G[ OK ]
 * Starting anac(h)ronistic cron[164G[ OK ]
 * Starting ACPI daemon[164G[ OK ]
 * Starting regular background program processing daemon[164G[ OK ]
 * Starting deferred execution scheduler[164G[ OK ]
 * Starting automatic crash report generation[164G[ OK ]
 * Stopping [164G[ OK ]
 * Starting LightDM Display Manager[164G[ OK ]
 * Starting CPU interrupts balancing daemon[164G[ OK ]
 * Stopping anac(h)ronistic cron[164G[ OK ]
 * Stopping save kernel messages[164G[ OK ]
 * Starting network connection manager[164G[ OK ]

---

### Post by ibrahim52 on 2013-03-31
and the above log is matching with the snapshot I took.

Is it safe to upload dmesg  log over here ?

---

