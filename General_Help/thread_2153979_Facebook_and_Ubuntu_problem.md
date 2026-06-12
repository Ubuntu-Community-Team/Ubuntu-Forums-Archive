---
title: "Facebook and Ubuntu problem"
date: 2013-06-13
forum: General Help
---

### Post by Ifaistos on 2013-06-13
Hello everyone :-)
Just yesterday I got a message from Ubuntu, asking me permission to post on my behalf on Facebook.
I have been asked before but I never allowed that.
For some reason I decided to allow it, to see what it will do.

Now every few minutes it opens this page on facebook on my Firefox.
[https://www.facebook.com/connect/blank.html#_=_](https://www.facebook.com/connect/blank.html#_=_)
and I get the message that is shown on my attached picture.

Can anyone explain why this is happening, and most importantly how do I get rid of this?

Thank you all :-)

---

### Post by BuddyThirteen on 2013-06-13
I've been having the same problem, and it's caused by gwibber-service, though I don't know any solutions. I've just disabled gwibber from startup, and the problem is (almost) gone. It still opens one of those tabs at startup, but after that it's quiet.

---

### Post by Ifaistos on 2013-06-13
Thanks for the answer.
How do I stop the gwibber service?
From the system monitor?

Does anyone know how to reset this setting.
It is quite annoying..

Thanks again.

---

### Post by BuddyThirteen on 2013-06-13
System monitor would work, but I personally find it's quicker to open up the terminal real quick (Ctrl+Alt+T) and just type "killall gwibber-service"

But you'll need to do that every time you restart. If you open up Gwibber (in your messaging menu up at the top) and then go into its preferences and uncheck the box for "Start service at login"

As I said, this isn't a true solution, but it does get rid of the annoyance...

---

### Post by byStanderone on 2013-06-13
...perhaps you may uninstall gwibberr  from your system using synaptic manager... and observe the effect...likewise you may re-install it later.

---

### Post by Ifaistos on 2013-06-13
Hm... most probably my problem was caused by smt else...

killall gwibber-service
gwibber-service: no process found

I don't seem to be running this service...

Any other ideas?

---

### Post by HermanAB on 2013-06-13
ps -e

---

### Post by Ifaistos on 2013-06-14
```
evans@Kallisto:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:01:11 ksoftirqd/0
    5 ?        00:00:00 kworker/0:0H
    6 ?        00:00:00 kworker/u:0
    7 ?        00:00:00 kworker/u:0H
    8 ?        00:00:00 migration/0
    9 ?        00:00:00 rcu_bh
   10 ?        00:01:52 rcu_sched
   11 ?        00:00:01 watchdog/0
   12 ?        00:00:01 watchdog/1
   13 ?        00:01:10 ksoftirqd/1
   14 ?        00:00:00 migration/1
   16 ?        00:00:00 kworker/1:0H
   17 ?        00:00:00 cpuset
   18 ?        00:00:00 khelper
   19 ?        00:00:00 kdevtmpfs
   20 ?        00:00:00 netns
   21 ?        00:00:00 bdi-default
   22 ?        00:00:00 kintegrityd
   23 ?        00:00:00 kblockd
   24 ?        00:00:00 ata_sff
   25 ?        00:00:00 khubd
   26 ?        00:00:00 md
   27 ?        00:00:00 devfreq_wq
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:14 kswapd0
   32 ?        00:00:00 ksmd
   33 ?        00:00:00 khugepaged
   34 ?        00:00:00 fsnotify_mark
   35 ?        00:00:00 ecryptfs-kthrea
   36 ?        00:00:00 crypto
   47 ?        00:00:00 kthrotld
   50 ?        00:00:00 scsi_eh_0
   51 ?        00:00:00 scsi_eh_1
   53 ?        00:00:00 scsi_eh_2
   54 ?        00:00:00 scsi_eh_3
   57 ?        00:00:00 binder
   77 ?        00:00:00 deferwq
   78 ?        00:00:00 charger_manager
  187 ?        00:00:00 scsi_eh_4
  191 ?        00:00:00 scsi_eh_5
  221 ?        00:00:00 firewire
  253 ?        00:00:06 flush-8:0
  262 ?        00:00:05 kworker/0:1H
  263 ?        00:00:04 kworker/1:1H
  264 ?        00:00:03 jbd2/sda5-8
  265 ?        00:00:00 ext4-dio-unwrit
  304 ?        00:00:00 upstart-file-br
  362 ?        00:00:00 upstart-udev-br
  364 ?        00:00:00 udevd
  640 ?        00:00:00 kpsmoused
  675 ?        00:00:00 hd-audio0
  701 ?        00:00:00 upstart-socket-
  750 ?        00:00:13 jbd2/sda7-8
  751 ?        00:00:00 ext4-dio-unwrit
  778 ?        00:00:02 mount.ntfs
  817 ?        00:00:00 smbd
  864 ?        00:00:15 rsyslogd
  930 tty4     00:00:00 getty
  936 tty5     00:00:00 getty
  974 tty2     00:00:00 getty
  975 tty3     00:00:00 getty
  977 tty6     00:00:00 getty
  982 ?        00:00:00 acpid
  983 ?        00:00:00 cron
  984 ?        00:00:00 atd
  985 ?        00:00:02 dbus-daemon
 1034 ?        00:00:26 teamviewerd
 1054 ?        00:00:00 modem-manager
 1061 ?        00:00:00 lightdm
 1071 ?        00:00:00 bluetoothd
 1078 ?        00:00:00 whoopsie
 1083 ?        00:00:00 krfcommd
 1097 tty7     01:10:27 Xorg
 1107 ?        00:00:00 avahi-daemon
 1109 ?        00:00:00 avahi-daemon
 1112 ?        00:00:00 cups-browsed
 1136 ?        00:00:00 cupsd
 1146 ?        00:00:00 smbd
 1267 tty1     00:00:00 getty
 1269 ?        00:00:00 NetworkManager
 1273 ?        00:00:01 polkitd
 1276 ?        00:00:00 colord
 1295 ?        00:00:00 dhclient
 1304 ?        00:00:05 accounts-daemon
 1318 ?        00:00:00 kauditd
 1324 ?        00:00:00 console-kit-dae
 1402 ?        00:00:01 dnsmasq
 1545 ?        00:00:00 winbindd
 1549 ?        00:00:02 nmbd
 1550 ?        00:00:00 winbindd
 1587 ?        00:00:00 upowerd
 1745 ?        00:00:00 lightdm
 1798 ?        00:00:01 rtkit-daemon
 1882 ?        00:00:05 gnome-keyring-d
 1893 ?        00:00:02 gnome-session
 1940 ?        00:00:00 ssh-agent
 1943 ?        00:00:00 dbus-launch
 1944 ?        00:12:13 dbus-daemon
 1964 ?        00:00:00 at-spi-bus-laun
 1968 ?        00:00:00 dbus-daemon
 1971 ?        00:00:00 at-spi2-registr
 1984 ?        00:00:51 gnome-settings-
 1994 ?        00:08:48 pulseaudio
 1996 ?        00:00:01 gvfsd
 2000 ?        00:00:00 gvfsd-fuse
 2030 ?        00:00:00 gconf-helper
 2033 ?        00:00:00 gconfd-2
 2042 ?        02:42:41 compiz
 2043 ?        00:00:00 wineserver
 2048 ?        00:00:01 dconf-service
 2051 ?        00:00:00 nm-applet
 2052 ?        00:00:00 gnome-fallback-
 2061 ?        00:00:00 polkit-gnome-au
 2067 ?        00:00:01 gvfs-udisks2-vo
 2070 ?        00:03:07 nautilus
 2071 ?        01:03:38 indicator-multi
 2075 ?        00:02:00 wallch
 2078 ?        00:00:54 udisksd
 2094 ?        00:00:00 gvfs-gphoto2-vo
 2098 ?        00:00:00 gvfs-mtp-volume
 2103 ?        00:00:00 gvfs-afc-volume
 2117 ?        00:00:00 gvfsd-trash
 2121 ?        00:02:06 dropbox
 2123 ?        00:00:00 gvfsd-burn
 2139 ?        00:00:00 telepathy-indic
 2151 ?        00:01:04 notify-osd
 2156 ?        00:00:01 mission-control
 2161 ?        00:00:00 gvfsd-metadata
 2169 ?        00:00:01 gnome-screensav
 2184 ?        00:00:33 bamfdaemon
 2197 ?        00:00:05 zeitgeist-datah
 2206 ?        00:00:03 zeitgeist-daemo
 2212 ?        00:00:04 zeitgeist-fts
 2220 ?        00:00:00 cat
 2245 ?        00:00:00 sh
 2246 ?        00:00:32 gtk-window-deco
 2249 ?        01:18:28 unity-panel-ser
 2251 ?        00:34:14 hud-service
 2277 ?        00:00:00 indicator-bluet
 2279 ?        00:00:00 indicator-sound
 2284 ?        00:00:00 indicator-datet
 2287 ?        00:00:00 indicator-sessi
 2288 ?        00:00:00 indicator-print
 2289 ?        00:00:00 indicator-sync-
 2290 ?        00:00:00 indicator-messa
 2291 ?        00:11:43 indicator-appli
 2314 ?        00:00:00 evolution-sourc
 2346 ?        00:00:11 goa-daemon
 2389 ?        00:00:09 ubuntuone-syncd
 2408 ?        00:00:06 unity-applicati
 2411 ?        00:00:02 unity-lens-frie
 2413 ?        00:00:00 unity-music-dae
 2414 ?        00:00:01 unity-files-dae
 2422 ?        00:00:02 unity-lens-phot
 2424 ?        00:00:01 unity-shopping-
 2426 ?        00:00:01 unity-video-len
 2479 ?        00:00:00 sh
 2480 ?        00:00:00 pxgsettings
 2489 ?        00:44:04 chrome
 2497 ?        00:00:01 unity-scope-vid
 2499 ?        00:00:02 unity-scope-gdr
 2506 ?        00:00:00 sh
 2507 ?        00:00:00 pxgsettings
 2518 ?        00:00:00 unity-musicstor
 2536 ?        01:38:46 firefox
 2558 ?        00:00:00 sh
 2559 ?        00:00:00 pxgsettings
 2565 ?        00:00:00 oosplash
 2594 ?        00:00:32 chrome
 2603 ?        00:00:00 chrome-sandbox
 2604 ?        00:00:00 chrome
 2630 ?        00:00:00 nacl_helper_boo
 2632 ?        00:04:11 soffice.bin
 2643 ?        00:00:33 signon-ui
 2657 ?        00:02:22 friends-service
 2680 ?        00:00:04 update-notifier
 2693 ?        00:00:00 sh
 2694 ?        00:00:00 pxgsettings
 2709 ?        00:00:00 unity-webapps-s
 2762 ?        00:00:00 evolution-addre
 2791 ?        00:00:00 chrome
 2858 ?        00:02:43 chrome
 2862 ?        01:05:25 chrome
 2870 ?        00:00:05 chrome
 3049 ?        01:32:36 chrome
 3104 ?        00:03:04 chrome
 3117 ?        00:00:59 chrome
 3125 ?        00:03:44 chrome
 3140 ?        00:00:00 deja-dup-monito
 3157 ?        01:56:18 chrome
 3201 ?        00:02:01 chrome <defunct>
 3470 ?        00:03:49 chrome
 3474 ?        00:00:00 chrome
 3500 ?        00:00:00 gvfsd-http
 3504 ?        00:00:00 sh
 3505 ?        00:00:00 pxgsettings
 6701 ?        00:00:00 scsi_eh_9
 6702 ?        00:00:00 usb-storage
 6705 ?        00:00:00 kworker/u:2
 6706 ?        00:00:00 udevd
 6707 ?        00:00:00 udevd
 8270 ?        00:22:55 plugin-containe
 9089 ?        00:00:00 chrome <defunct>
 9146 ?        00:00:00 chrome <defunct>
 9291 ?        00:00:02 chrome <defunct>
 9314 ?        00:00:00 chrome
 9545 ?        00:00:01 kworker/0:2
 9549 ?        00:00:00 kworker/1:2
 9764 ?        00:00:14 update-manager
 9998 ?        00:00:00 dbus
10170 ?        00:00:00 kworker/0:0
10267 ?        00:00:00 kworker/1:1
10268 ?        00:00:00 kworker/0:1
10271 ?        00:00:00 kworker/1:0
10301 ?        00:00:00 sh
10302 ?        00:00:00 gnome-terminal
10306 ?        00:00:00 gnome-pty-helpe
10308 pts/1    00:00:00 bash
10313 pts/1    00:00:00 ps
14088 ?        00:03:29 wineserver
14094 ?        00:00:00 services.exe
14098 ?        00:00:18 CrossLoopServic
14100 ?        00:00:14 explorer.exe
14108 ?        00:00:00 winedevice.exe
14115 ?        00:00:00 plugplay.exe
14122 ?        00:05:19 Evernote.exe
14138 ?        00:00:00 EvernoteTray.ex
14140 ?        00:00:40 EvernoteClipper
23453 ?        02:14:33 chrome
28889 ?        00:00:03 gedit
29271 ?        00:01:32 chrome
31158 ?        00:00:00 chrome
31368 ?        00:00:07 chrome
31953 ?        00:17:42 thunderbird
32025 ?        00:00:04 chrome
evans@Kallisto:~$
```

---

### Post by Ifaistos on 2013-06-15
Bump

---

### Post by Ifaistos on 2013-06-17
Bump

---

### Post by Ifaistos on 2013-06-17
Bump

---

### Post by Baldrick_NZ on 2013-06-18
It's an on-going issue with the ubuntu online accounts. Users get the same message when they try to sign up using third-party clients like Empathy and Gwibber. 

The best bet is to open 'Online Accounts' under 'System Settings' and remove (delete) the offending Facebook entry. You may have inadvertantly attempted to create a Facebook online account in Ubuntu.

If you want to use a chat client for Facebook, then I suggest you install 'Pidgin' from the repos and use that until Canonical fix up the mess. Pidgin doesn't access the Online accounts, so you should be safe there.

Hope that helps.

---

### Post by Ifaistos on 2013-06-19
Thank you !!
I deleted the online account for Facebook I hope it works.

I was also getting messages all the time that Ubuntu could not access my Facebook online account.

---

