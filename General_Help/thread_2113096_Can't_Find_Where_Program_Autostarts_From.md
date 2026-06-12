---
title: "Can't Find Where Program Autostarts From"
date: 2013-02-06
forum: General Help
---

### Post by AntumDeluge on 2013-02-06
I have a program, [QJoyPad]("http://qjoypad.sourceforge.net/"), that is autostarting at login (I think) and I can't figure out where it is starting from. Here is a list of places I have checked:

- Looked in ~/.config/autostart:
```
:~$ ls -a ~/.config/autostart
.  ..
```- Looked in KDE autostart under system settings.

- Run the command initctl list:
```
:~$ initctl list
avahi-daemon start/running, process 720
mountall-net stop/waiting
nmbd start/running, process 1643
passwd stop/waiting
rc stop/waiting
rsyslog start/running, process 712
tty4 start/running, process 1207
udev start/running, process 494
upstart-udev-bridge start/running, process 487
ureadahead-other stop/waiting
apport start/running
console-setup stop/waiting
hwclock-save stop/waiting
irqbalance stop/waiting
plymouth-log stop/waiting
smbd start/running, process 1018
tty5 start/running, process 1213
failsafe stop/waiting
hybrid-gfx stop/waiting
modemmanager start/running, process 1050
rfkill-store stop/waiting
atd start/running, process 1258
dbus start/running, process 642
mounted-var stop/waiting
plymouth stop/waiting
resolvconf start/running
udev-fallback-graphics stop/waiting
control-alt-delete stop/waiting
hwclock stop/waiting
mounted-proc stop/waiting
network-manager start/running, process 1057
alsa-store stop/waiting
module-init-tools stop/waiting
setvtrgb stop/waiting
shutdown stop/waiting
alsa-restore stop/waiting
cron start/running, process 1257
lightdm stop/waiting
mountall stop/waiting
mounted-debugfs stop/waiting
binfmt-support stop/waiting
console stop/waiting
mounted-run stop/waiting
acpid start/running, process 1255
bluetooth start/running, process 670
plymouth-stop stop/waiting
rcS stop/waiting
ufw start/running
wait-for-state stop/waiting
flush-early-job-log stop/waiting
friendly-recovery stop/waiting
rc-sysinit stop/waiting
cups start/running, process 767
upstart-socket-bridge start/running, process 1072
anacron stop/waiting
tty2 start/running, process 1228
udevtrigger stop/waiting
container-detect stop/waiting
mounted-dev stop/waiting
tty3 start/running, process 1229
udev-finish stop/waiting
cryptdisks-udev stop/waiting
hostname stop/waiting
kdm start/running, process 1233
mountall-reboot stop/waiting
mountall-shell stop/waiting
mounted-tmp stop/waiting
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface (wlan0) start/running
plymouth-splash stop/waiting
plymouth-upstart-bridge stop/waiting
tty1 start/running, process 1514
udevmonitor stop/waiting
cryptdisks-enable stop/waiting
dmesg stop/waiting
network-interface-security (network-manager) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/wlan0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking stop/waiting
procps stop/waiting
rfkill-restore stop/waiting
tty6 start/running, process 1236
network-interface-container stop/waiting
ureadahead stop/waiting
```- Looked in /etc/xdg/autostart.
```
:~$ ls -a /etc/xdg/autostart
.
..
blueman.desktop
gdu-notification-daemon.desktop
gnome-fallback-mount-helper.desktop
gnome-keyring-gpg.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-settings-daemon.desktop
gnome-sound-applet.desktop
gsettings-data-convert.desktop
jockey-gtk.desktop
jockey-kde.desktop
nautilus-autostart.desktop
nm-applet.desktop
nvidia-autostart.desktop
polkit-gnome-authentication-agent-1.desktop
print-applet.desktop
pulseaudio.desktop
pulseaudio-kde.desktop
synaptiks_init_config.desktop
update-notifier.desktop
xfce4-power-manager.desktop
zeitgeist-datahub.desktop
```

---

