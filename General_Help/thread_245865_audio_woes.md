---
title: "audio woes"
date: 2006-08-28
forum: General Help
---

### Post by Namtellum on 2006-08-28
I am getting a clicking noise on mp3 playback. It almost sounds like static, I've ruled out the possibility of it being the speakers as they do not do it under windows. Also, possibly a related issue, I get no sound in flash, I have tried some of the fixes I found doing a search to no avail. Any help would be appreciated. Edit: Also when i turn the master volume all the way down I still get sound in totem.

---

### Post by orb9220 on 2006-08-28
did you try other audio apps besides totem for playback?

---

### Post by Namtellum on 2006-08-28
Yep, every media player I have creates the static on mp3's. But a game such as warcraft 3 or a video podcast there is no static.

---

### Post by skymt on 2006-08-28
I've found the fluendo mp3 codec for gstreamer tends to have static. My solution is to use ogg. ;) 

Or, just install gstreamer0.10-plugins-ugly.

For the Flash issue, you should make sure no other programs that use audio are running. This means music players, video players, games, etc. Also, open a terminal and run "sudo killall esd", just in case.

---

### Post by Namtellum on 2006-08-29
It says I have that plugin already installed. And the killall command still gets me no sound in flash.

---

### Post by skymt on 2006-08-29
> **Namtellum said:**
> It says I have that plugin already installed. And the killall command still gets me no sound in flash.

Post the output of 'ps -e', please. Let's get to the bottom of this.

---

### Post by Namtellum on 2006-08-29
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:10 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  102 ?        00:00:00 pdflush
  103 ?        00:00:00 pdflush
  105 ?        00:00:00 aio/0
  104 ?        00:00:05 kswapd0
  692 ?        00:00:00 kseriod
 1808 ?        00:00:00 ata/0
 1809 ?        00:00:00 ata_hotplug/0
 1812 ?        00:00:00 scsi_eh_0
 1813 ?        00:00:00 scsi_eh_1
 1833 ?        00:00:00 khubd
 1940 ?        00:00:03 kjournald
 2170 ?        00:00:00 udevd
 3000 ?        00:00:00 shpchpd_event
 3134 ?        00:00:00 kgameportd
 3411 ?        00:00:00 dhclient3
 3997 ?        00:00:00 dd
 3999 ?        00:00:00 klogd
 4318 ?        00:00:00 gdm
 4347 ?        00:00:00 gdm
 4352 tty7     03:05:59 Xorg
 4361 ?        00:00:00 hpiod
 4368 ?        00:00:00 python
 4440 ?        00:00:00 dbus-daemon
 4455 ?        00:00:01 hald
 4456 ?        00:00:00 hald-runner
 4461 ?        00:00:00 hald-addon-acpi
 4467 ?        00:00:24 hald-addon-keyb
 4471 ?        00:00:00 hald-addon-keyb
 4529 ?        00:01:08 hald-addon-stor
 4530 ?        00:01:09 hald-addon-stor
 4532 ?        00:00:17 hald-addon-stor
 4533 ?        00:00:17 hald-addon-stor
 4616 ?        00:00:00 hcid
 4620 ?        00:00:00 sdpd
 4633 ?        00:00:00 krfcommd
 4646 ?        00:00:00 mdadm
 4680 ?        00:00:00 atd
 4693 ?        00:00:00 cron
 4765 tty1     00:00:00 getty
 4766 tty2     00:00:00 getty
 4767 tty3     00:00:00 getty
 4768 tty4     00:00:00 getty
 4769 tty5     00:00:00 getty
 4770 tty6     00:00:00 getty
 4785 ?        00:00:08 x-session-manag
 4827 ?        00:00:00 ssh-agent
 4830 ?        00:00:00 dbus-launch
 4831 ?        00:00:06 dbus-daemon
 4833 ?        00:00:03 gconfd-2
 4836 ?        00:00:00 gnome-keyring-d
 4838 ?        00:00:00 bonobo-activati
 4840 ?        00:00:38 gnome-settings-
 4849 ?        00:05:41 metacity
 4855 ?        00:05:28 gnome-panel
 4857 ?        00:01:32 nautilus
 4860 ?        00:00:05 gnome-volume-ma
 4868 ?        00:00:19 update-notifier
 4872 ?        00:00:08 gnome-vfs-daemo
 4878 ?        00:00:09 gnome-cups-icon
 4904 ?        00:00:12 gnome-power-man
 4906 ?        00:00:13 trashapplet
 4915 ?        00:00:00 mapping-daemon
 4918 ?        00:00:05 clock-applet
 4920 ?        00:00:15 mixer_applet2
 4934 ?        00:00:36 gnome-screensav
 4938 ?        03:02:47 gaim
 7532 ?        00:00:21 notification-da
 1391 ?        00:00:00 acpid
14806 ?        00:00:00 cupsd
14884 ?        00:00:00 syslogd
17134 ?        00:00:00 swiftfox
17137 ?        00:00:00 run-mozilla.sh
17142 ?        00:03:17 swiftfox-bin
20703 ?        00:00:11 rhythmbox
20730 ?        00:00:00 rhythmbox
  461 ?        00:00:00 gnome-terminal
  464 ?        00:00:00 esd
  465 ?        00:00:00 gnome-pty-helpe
  466 pts/0    00:00:00 bash
  484 pts/0    00:00:00 ps

---

### Post by skymt on 2006-08-29
So, when you try to play a Flash video, you quit Rhythmbox and sudo killall esd, right? You generally have to do the latter for each Youtube session; esd has a bad habit of appearing when you don't want it.

Under System > Preferences > Sound, you have "Enable software sound mixing (ESD)" disabled, right?

EDIT: note that by "Youtube session," I don't mean per video. Also, always close and re-open your browser after closing audio players and esd.

EDIT 2: I just remembered about your MP3 static. Do you have the fluendo codecs installed? If you do, remove them. They take priority over -plugins-ugly, and as I said, they can cause static.

---

### Post by smartalecks on 2006-08-29
I am also having this problem. Recently, i installed Timidity++ (midi playback) via EasyUbuntu. I did not have this problem before I did.

i'll try uninstalling.

edit: I think it worked. uninstall freepats and all timidity if you have it.

---

### Post by Namtellum on 2006-08-29
I dont have freepats or timidity installed. and i tried to remove fluendo but it said it could not find package. I also did have esd enabled but i disabled it and it hasnt seem to of done anything.

---

