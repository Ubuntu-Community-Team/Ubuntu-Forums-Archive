---
title: "The shell scripts in /etc/init.d dont's start"
date: 2006-11-06
forum: General Help
---

### Post by osa100 on 2006-11-06
Hello, I have Ubuntu 5.10 _Breezy Badger_ version.
The shell scripts of folder /etc/init.d don't start to startup for example: Apache2, privoxy, ssh ecc.  I have check with BUM, it seems all good, In the directories /etc/rc[0-6].d there are links to scripts in init.d.
What has happened? You can help me? Thanks.
P.S 
Excused my English, I'm italian

---

### Post by bsussman on 2006-11-06
How do you know they are not executing?

are the daemons not running?

---

### Post by taurus on 2006-11-06
See them from this command?

```
ps -A
```

---

### Post by osa100 on 2006-11-07
> **taurus said:**
> See them from this command?

```
ps -A
```

This is the output of ps -A:
```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
  126 ?        00:00:00 kblockd/0
  154 ?        00:00:00 pdflush
  155 ?        00:00:00 pdflush
  157 ?        00:00:00 aio/0
  156 ?        00:00:00 kswapd0
  742 ?        00:00:00 kseriod
  981 ?        00:00:00 ata/0
 2531 ?        00:00:00 khubd
 4186 ?        00:00:00 kjournald
 4332 ?        00:00:00 udevd
 6833 ?        00:00:00 shpchpd_event
 7527 ?        00:00:00 kgameportd
 7829 ?        00:00:00 dhclient3
 7860 ?        00:00:00 portmap
 7970 ?        00:00:00 rc
 8154 ?        00:00:00 acpid
 8169 ?        00:00:00 syslogd
 8186 ?        00:00:00 dd
 8188 ?        00:00:00 klogd
 8201 ?        00:00:00 dbus-daemon
 8214 ?        00:00:00 hald
 8219 ?        00:00:00 hald-addon-acpi
 8229 ?        00:00:00 hald-addon-stor
 8231 ?        00:00:00 hald-addon-stor
 8533 ?        00:00:00 gdm
 8534 ?        00:00:00 gdm
 8572 ?        00:00:22 Xorg
 8625 ?        00:00:00 cupsd
 8629 ?        00:00:00 S20cftp
 8669 ?        00:00:00 x-session-manag
 8708 ?        00:00:00 ssh-agent
 8711 ?        00:00:00 dbus-launch
 8712 ?        00:00:00 dbus-daemon
 8715 ?        00:00:00 gconfd-2
 8723 ?        00:00:00 gnome-keyring-d
 8725 ?        00:00:00 esd
 8729 ?        00:00:00 bonobo-activati
 8732 ?        00:00:00 gnome-settings-
 8739 ?        00:00:00 gam_server
 8759 ?        00:00:00 xscreensaver
 8766 ?        00:00:01 vino-server
 8771 ?        00:00:00 metacity
 8796 ?        00:00:00 gnome-panel
 8798 ?        00:00:01 nautilus
 8800 ?        00:00:00 gnome-volume-ma
 8808 ?        00:00:00 update-notifier
 8810 ?        00:00:00 wnck-applet
 8813 ?        00:00:00 gnome-cups-icon
 8815 ?        00:00:00 notification-da
 8822 ?        00:00:00 gnome-vfs-daemo
 8826 ?        00:00:00 trashapplet
 8839 ?        00:00:00 mapping-daemon
 8856 ?        00:00:00 notification-ar
 8858 ?        00:00:00 mixer_applet2
 8860 ?        00:00:00 clock-applet
 8866 ?        00:00:00 firefox
 8870 ?        00:00:00 run-mozilla.sh
 8875 ?        00:00:11 firefox-bin
 9214 ?        00:00:00 gnome-terminal
 9218 ?        00:00:00 gnome-pty-helpe
 9219 pts/0    00:00:00 bash
 9291 pts/0    00:00:00 su
 9316 pts/0    00:00:00 bash
 9357 ?        00:00:00 w3m
 9358 pts/0    00:00:00 ps

```

However for example apache 2 demon doesn't start to startup, I must start it with comand /etc/init.d/apache2 start.

---

### Post by bsussman on 2006-11-07
I have not had this problem in 6.06 or 6.10

It is unlikely to be a 5.10 bug, in my opinion, since by now I would expect it to be reported!  5.10 only has 6 more months of support as far as I know.

I assume you installed apache2 using the standard .deb package(s)

I assume your manual start is done either using the root account or sudo.

I assume youe manual start is successful and shows no errors either in the terminal window or log?

What do the apache2 logs say immediately after a boot?  Is there anything in the error log?

---

### Post by Iowan on 2006-11-07
Could you post a listing of the links in /etc/rc2.d?

---

### Post by osa100 on 2006-11-07
> **Iowan said:**
> Could you post a listing of the links in /etc/rc2.d?
This is the listing of directory rc2.d:


```
K19hplip         S12dbus               S20pcmcia      S89anacron
K20acpi-support  S13gdm                S20postfix     S89cron
K20apmd          S14ppp                S20powernowd   S91apache2
K20hotkey-setup  S18portmap            S20privoxy     S91apache-perl
K74bluez-utils   S19cupsys             S20rsync       S98usplash
K77ntp-server    S20cftp               S20ssh_start   S99fetchmail
K89atd           S20firestarter        S20tor         S99rmnologin
S05vbesave       S20lan                S20vsftpd      S99stop-bootlogd
S10acpid         S20makedev            S21kdm
S10sysklogd      S20mysql              S21nfs-common
S11klogd         S20nfs-kernel-server  S25mdadm

```
One important what is that only scripts shell don't start, in fact cftp is a  process written in C language.
The apache log in /var/log/apache2 doesn't does not say null regarding the boot. Thank you.

---

