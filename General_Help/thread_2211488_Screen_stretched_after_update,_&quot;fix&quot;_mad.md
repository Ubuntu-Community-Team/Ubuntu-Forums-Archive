---
title: "Screen stretched after update, &quot;fix&quot; made things worse"
date: 2014-03-16
forum: General Help
---

### Post by wstrong714 on 2014-03-16
I am running Ubunbtu 12.04 LTS, and ran an update this morning.  After a reboot, my screen resolution was stretched.  I searched for a fix, and found a now closed thread that seemed to match exactly.  Followed the instructions.  Not only is the stretching problem not fixed, but now Cinnamon crashed and reverts to "fallback mode."

Here is the code I followed for the fix:

[B]sudo apt-get remove --purge nvidia-current
sudo apt-get autoremove
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
[B]sudo apt-get install nvidia-current nvidia-settings


[/B][/B]I'm not real well versed in these things, so if there is more info you need, let me know what it is and the best way to get it and I'll do my best.

---

### Post by r.stiltskin on 2014-03-16
Please post the output of this command to show what kind of video card you have:
```

lspci | grep -i vga

```
and this one, to show what changes you made to your system today:
```

cat /var/log/dpkg.log | grep '2014-03-16'

```

---

### Post by wstrong714 on 2014-03-16
[COLOR=#000000]r.stiltskin,
[/COLOR]
Result of the first command:
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200]

And the second:
2014-03-16 08:06:44 startup archives unpack
2014-03-16 08:06:49 upgrade google-chrome-stable 33.0.1750.146-1 33.0.1750.152-1
2014-03-16 08:06:49 status half-configured google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:49 status unpacked google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:49 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:49 status triggers-pending man-db 2.6.1-2ubuntu1
2014-03-16 08:06:49 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:49 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2014-03-16 08:06:49 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:49 status triggers-pending bamfdaemon 0.2.126-0ubuntu1
2014-03-16 08:06:49 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:06:50 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2014-03-16 08:06:50 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:07:01 status half-installed google-chrome-stable 33.0.1750.146-1
2014-03-16 08:07:01 status unpacked google-chrome-stable 33.0.1750.152-1
2014-03-16 08:07:01 status unpacked google-chrome-stable 33.0.1750.152-1
2014-03-16 08:07:02 upgrade libcupsfilters1 1.0.18-0ubuntu0.1 1.0.18-0ubuntu0.2
2014-03-16 08:07:02 status half-configured libcupsfilters1 1.0.18-0ubuntu0.1
2014-03-16 08:07:02 status unpacked libcupsfilters1 1.0.18-0ubuntu0.1
2014-03-16 08:07:02 status half-installed libcupsfilters1 1.0.18-0ubuntu0.1
2014-03-16 08:07:02 status half-installed libcupsfilters1 1.0.18-0ubuntu0.1
2014-03-16 08:07:02 status unpacked libcupsfilters1 1.0.18-0ubuntu0.2
2014-03-16 08:07:02 status unpacked libcupsfilters1 1.0.18-0ubuntu0.2
2014-03-16 08:07:03 upgrade libssh-4 0.5.2-1ubuntu0.12.04.2 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:07:03 status half-configured libssh-4 0.5.2-1ubuntu0.12.04.2
2014-03-16 08:07:03 status unpacked libssh-4 0.5.2-1ubuntu0.12.04.2
2014-03-16 08:07:03 status half-installed libssh-4 0.5.2-1ubuntu0.12.04.2
2014-03-16 08:07:03 status half-installed libssh-4 0.5.2-1ubuntu0.12.04.2
2014-03-16 08:07:03 status unpacked libssh-4 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:07:04 status unpacked libssh-4 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:07:04 upgrade tzdata-java 2013g-0ubuntu0.12.04 2014a-0ubuntu0.12.04
2014-03-16 08:07:04 status half-configured tzdata-java 2013g-0ubuntu0.12.04
2014-03-16 08:07:04 status unpacked tzdata-java 2013g-0ubuntu0.12.04
2014-03-16 08:07:04 status half-installed tzdata-java 2013g-0ubuntu0.12.04
2014-03-16 08:07:04 status half-installed tzdata-java 2013g-0ubuntu0.12.04
2014-03-16 08:07:05 status unpacked tzdata-java 2014a-0ubuntu0.12.04
2014-03-16 08:07:05 status unpacked tzdata-java 2014a-0ubuntu0.12.04
2014-03-16 08:07:05 upgrade tzdata 2013g-0ubuntu0.12.04 2014a-0ubuntu0.12.04
2014-03-16 08:07:05 status half-configured tzdata 2013g-0ubuntu0.12.04
2014-03-16 08:07:05 status unpacked tzdata 2013g-0ubuntu0.12.04
2014-03-16 08:07:05 status half-installed tzdata 2013g-0ubuntu0.12.04
2014-03-16 08:07:06 status half-installed tzdata 2013g-0ubuntu0.12.04
2014-03-16 08:07:07 status unpacked tzdata 2014a-0ubuntu0.12.04
2014-03-16 08:07:07 status unpacked tzdata 2014a-0ubuntu0.12.04
2014-03-16 08:07:07 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2014-03-16 08:07:07 status half-configured man-db 2.6.1-2ubuntu1
2014-03-16 08:07:10 status installed man-db 2.6.1-2ubuntu1
2014-03-16 08:07:10 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2014-03-16 08:07:10 status half-configured desktop-file-utils 0.20-0ubuntu3
2014-03-16 08:07:10 status installed desktop-file-utils 0.20-0ubuntu3
2014-03-16 08:07:10 trigproc bamfdaemon 0.2.126-0ubuntu1 0.2.126-0ubuntu1
2014-03-16 08:07:10 status half-configured bamfdaemon 0.2.126-0ubuntu1
2014-03-16 08:07:10 status installed bamfdaemon 0.2.126-0ubuntu1
2014-03-16 08:07:10 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2014-03-16 08:07:10 status half-configured gnome-menus 3.4.0-0ubuntu1
2014-03-16 08:07:10 status installed gnome-menus 3.4.0-0ubuntu1
2014-03-16 08:07:11 startup packages configure
2014-03-16 08:07:11 configure tzdata 2014a-0ubuntu0.12.04 <none>
2014-03-16 08:07:11 status unpacked tzdata 2014a-0ubuntu0.12.04
2014-03-16 08:07:11 status half-configured tzdata 2014a-0ubuntu0.12.04
2014-03-16 08:07:13 status installed tzdata 2014a-0ubuntu0.12.04
2014-03-16 08:07:14 startup archives unpack
2014-03-16 08:07:15 upgrade sudo 1.8.3p1-1ubuntu3.4 1.8.3p1-1ubuntu3.6
2014-03-16 08:07:15 status half-configured sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:15 status unpacked sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:15 status half-installed sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:15 status triggers-pending man-db 2.6.1-2ubuntu1
2014-03-16 08:07:15 status half-installed sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:16 status triggers-pending ureadahead 0.100.0-12
2014-03-16 08:07:16 status half-installed sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:16 status half-installed sudo 1.8.3p1-1ubuntu3.4
2014-03-16 08:07:16 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:07:16 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:07:16 upgrade cups-filters 1.0.18-0ubuntu0.1 1.0.18-0ubuntu0.2
2014-03-16 08:07:16 status half-configured cups-filters 1.0.18-0ubuntu0.1
2014-03-16 08:07:16 status unpacked cups-filters 1.0.18-0ubuntu0.1
2014-03-16 08:07:17 status half-installed cups-filters 1.0.18-0ubuntu0.1
2014-03-16 08:07:17 status triggers-pending cups 1.5.3-0ubuntu8
2014-03-16 08:07:17 status half-installed cups-filters 1.0.18-0ubuntu0.1
2014-03-16 08:07:17 status half-installed cups-filters 1.0.18-0ubuntu0.1
2014-03-16 08:07:17 status unpacked cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:07:17 status unpacked cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:07:18 upgrade flashplugin-installer 11.2.202.341ubuntu0.12.04.1 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:07:18 status half-configured flashplugin-installer 11.2.202.341ubuntu0.12.04.1
2014-03-16 08:07:18 status unpacked flashplugin-installer 11.2.202.341ubuntu0.12.04.1
2014-03-16 08:07:18 status half-installed flashplugin-installer 11.2.202.341ubuntu0.12.04.1
2014-03-16 08:07:18 status triggers-pending update-notifier-common 0.119ubuntu8.6
2014-03-16 08:07:18 status half-installed flashplugin-installer 11.2.202.341ubuntu0.12.04.1
2014-03-16 08:07:18 status half-installed flashplugin-installer 11.2.202.341ubuntu0.12.04.1
2014-03-16 08:07:18 status unpacked flashplugin-installer 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:07:19 status unpacked flashplugin-installer 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:07:19 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2014-03-16 08:07:19 status half-configured man-db 2.6.1-2ubuntu1
2014-03-16 08:07:22 status installed man-db 2.6.1-2ubuntu1
2014-03-16 08:07:22 trigproc ureadahead 0.100.0-12 0.100.0-12
2014-03-16 08:07:22 status half-configured ureadahead 0.100.0-12
2014-03-16 08:07:22 status installed ureadahead 0.100.0-12
2014-03-16 08:07:22 trigproc cups 1.5.3-0ubuntu8 1.5.3-0ubuntu8
2014-03-16 08:07:22 status half-configured cups 1.5.3-0ubuntu8
2014-03-16 08:07:31 status installed cups 1.5.3-0ubuntu8
2014-03-16 08:07:31 trigproc update-notifier-common 0.119ubuntu8.6 0.119ubuntu8.6
2014-03-16 08:07:31 status half-configured update-notifier-common 0.119ubuntu8.6
2014-03-16 08:08:25 status installed update-notifier-common 0.119ubuntu8.6
2014-03-16 08:08:26 startup packages configure
2014-03-16 08:08:26 configure google-chrome-stable 33.0.1750.152-1 <none>
2014-03-16 08:08:26 status unpacked google-chrome-stable 33.0.1750.152-1
2014-03-16 08:08:26 status half-configured google-chrome-stable 33.0.1750.152-1
2014-03-16 08:08:37 status installed google-chrome-stable 33.0.1750.152-1
2014-03-16 08:08:37 configure libcupsfilters1 1.0.18-0ubuntu0.2 <none>
2014-03-16 08:08:37 status unpacked libcupsfilters1 1.0.18-0ubuntu0.2
2014-03-16 08:08:37 status half-configured libcupsfilters1 1.0.18-0ubuntu0.2
2014-03-16 08:08:38 status installed libcupsfilters1 1.0.18-0ubuntu0.2
2014-03-16 08:08:38 status triggers-pending libc-bin 2.15-0ubuntu10.5
2014-03-16 08:08:38 configure libssh-4 0.5.2-1ubuntu0.12.04.3 <none>
2014-03-16 08:08:38 status unpacked libssh-4 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:08:38 status half-configured libssh-4 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:08:38 status installed libssh-4 0.5.2-1ubuntu0.12.04.3
2014-03-16 08:08:38 configure tzdata-java 2014a-0ubuntu0.12.04 <none>
2014-03-16 08:08:38 status unpacked tzdata-java 2014a-0ubuntu0.12.04
2014-03-16 08:08:38 status half-configured tzdata-java 2014a-0ubuntu0.12.04
2014-03-16 08:08:38 status installed tzdata-java 2014a-0ubuntu0.12.04
2014-03-16 08:08:38 configure sudo 1.8.3p1-1ubuntu3.6 <none>
2014-03-16 08:08:38 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:38 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:38 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:38 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:38 status unpacked sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:38 status half-configured sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:39 status installed sudo 1.8.3p1-1ubuntu3.6
2014-03-16 08:08:39 configure cups-filters 1.0.18-0ubuntu0.2 <none>
2014-03-16 08:08:39 status unpacked cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:08:39 status unpacked cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:08:39 status half-configured cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:08:40 status installed cups-filters 1.0.18-0ubuntu0.2
2014-03-16 08:08:40 configure flashplugin-installer 11.2.202.346ubuntu0.12.04.1 <none>
2014-03-16 08:08:40 status unpacked flashplugin-installer 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:08:40 status half-configured flashplugin-installer 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:08:41 status installed flashplugin-installer 11.2.202.346ubuntu0.12.04.1
2014-03-16 08:08:41 trigproc libc-bin 2.15-0ubuntu10.5 <none>
2014-03-16 08:08:41 status half-configured libc-bin 2.15-0ubuntu10.5
2014-03-16 08:08:42 status installed libc-bin 2.15-0ubuntu10.5
2014-03-16 09:25:58 startup archives unpack
2014-03-16 09:26:02 install libconfuse-common <none> 2.7-4
2014-03-16 09:26:02 status half-installed libconfuse-common 2.7-4
2014-03-16 09:26:02 status unpacked libconfuse-common 2.7-4
2014-03-16 09:26:02 status unpacked libconfuse-common 2.7-4
2014-03-16 09:26:03 install libconfuse0 <none> 2.7-4
2014-03-16 09:26:03 status half-installed libconfuse0 2.7-4
2014-03-16 09:26:03 status unpacked libconfuse0 2.7-4
2014-03-16 09:26:03 status unpacked libconfuse0 2.7-4
2014-03-16 09:26:04 install libxcb-dpms0 <none> 1.8.1-1ubuntu0.2
2014-03-16 09:26:04 status half-installed libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:04 status unpacked libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:04 status unpacked libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 install libxcb-randr0 <none> 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 status half-installed libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 status unpacked libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 status unpacked libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 install libxcb-xinerama0 <none> 1.8.1-1ubuntu0.2
2014-03-16 09:26:05 status half-installed libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:06 status unpacked libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:06 status unpacked libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:06 install dzen2 <none> 0.8.5-4
2014-03-16 09:26:06 status half-installed dzen2 0.8.5-4
2014-03-16 09:26:06 status triggers-pending man-db 2.6.1-2ubuntu1
2014-03-16 09:26:06 status half-installed dzen2 0.8.5-4
2014-03-16 09:26:06 status unpacked dzen2 0.8.5-4
2014-03-16 09:26:07 status unpacked dzen2 0.8.5-4
2014-03-16 09:26:07 install libev4 <none> 1:4.11-1
2014-03-16 09:26:07 status half-installed libev4 1:4.11-1
2014-03-16 09:26:07 status unpacked libev4 1:4.11-1
2014-03-16 09:26:07 status unpacked libev4 1:4.11-1
2014-03-16 09:26:08 install libxcb-icccm4 <none> 0.3.8-1build1
2014-03-16 09:26:08 status half-installed libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:08 status unpacked libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:08 status unpacked libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:08 install libxcb-keysyms1 <none> 0.3.8-1build1
2014-03-16 09:26:08 status half-installed libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:09 status unpacked libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:09 status unpacked libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:09 install i3-wm <none> 4.1.2-2
2014-03-16 09:26:09 status half-installed i3-wm 4.1.2-2
2014-03-16 09:26:09 status triggers-pending doc-base 0.10.3
2014-03-16 09:26:09 status half-installed i3-wm 4.1.2-2
2014-03-16 09:26:10 status half-installed i3-wm 4.1.2-2
2014-03-16 09:26:10 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:10 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:10 install i3 <none> 4.1.2-2
2014-03-16 09:26:10 status half-installed i3 4.1.2-2
2014-03-16 09:26:10 status unpacked i3 4.1.2-2
2014-03-16 09:26:10 status unpacked i3 4.1.2-2
2014-03-16 09:26:11 install libxcb-image0 <none> 0.3.8-1build1
2014-03-16 09:26:11 status half-installed libxcb-image0 0.3.8-1build1
2014-03-16 09:26:11 status unpacked libxcb-image0 0.3.8-1build1
2014-03-16 09:26:11 status unpacked libxcb-image0 0.3.8-1build1
2014-03-16 09:26:12 install i3lock <none> 2.2-1
2014-03-16 09:26:12 status half-installed i3lock 2.2-1
2014-03-16 09:26:12 status half-installed i3lock 2.2-1
2014-03-16 09:26:12 status unpacked i3lock 2.2-1
2014-03-16 09:26:12 status unpacked i3lock 2.2-1
2014-03-16 09:26:12 install i3status <none> 2.4-1
2014-03-16 09:26:12 status half-installed i3status 2.4-1
2014-03-16 09:26:12 status half-installed i3status 2.4-1
2014-03-16 09:26:13 status unpacked i3status 2.4-1
2014-03-16 09:26:13 status unpacked i3status 2.4-1
2014-03-16 09:26:13 install suckless-tools <none> 38-1
2014-03-16 09:26:13 status half-installed suckless-tools 38-1
2014-03-16 09:26:13 status half-installed suckless-tools 38-1
2014-03-16 09:26:13 status unpacked suckless-tools 38-1
2014-03-16 09:26:13 status unpacked suckless-tools 38-1
2014-03-16 09:26:13 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2014-03-16 09:26:13 status half-configured man-db 2.6.1-2ubuntu1
2014-03-16 09:26:18 status installed man-db 2.6.1-2ubuntu1
2014-03-16 09:26:18 trigproc doc-base 0.10.3 0.10.3
2014-03-16 09:26:18 status half-configured doc-base 0.10.3
2014-03-16 09:26:19 status installed doc-base 0.10.3
2014-03-16 09:26:20 startup packages configure
2014-03-16 09:26:20 configure libconfuse-common 2.7-4 <none>
2014-03-16 09:26:20 status unpacked libconfuse-common 2.7-4
2014-03-16 09:26:20 status half-configured libconfuse-common 2.7-4
2014-03-16 09:26:20 status installed libconfuse-common 2.7-4
2014-03-16 09:26:20 configure libconfuse0 2.7-4 <none>
2014-03-16 09:26:20 status unpacked libconfuse0 2.7-4
2014-03-16 09:26:20 status half-configured libconfuse0 2.7-4
2014-03-16 09:26:20 status installed libconfuse0 2.7-4
2014-03-16 09:26:20 status triggers-pending libc-bin 2.15-0ubuntu10.5
2014-03-16 09:26:20 configure libxcb-dpms0 1.8.1-1ubuntu0.2 <none>
2014-03-16 09:26:20 status unpacked libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:20 status half-configured libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:20 status installed libxcb-dpms0 1.8.1-1ubuntu0.2
2014-03-16 09:26:20 configure libxcb-randr0 1.8.1-1ubuntu0.2 <none>
2014-03-16 09:26:20 status unpacked libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:20 status half-configured libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:21 status installed libxcb-randr0 1.8.1-1ubuntu0.2
2014-03-16 09:26:21 configure libxcb-xinerama0 1.8.1-1ubuntu0.2 <none>
2014-03-16 09:26:21 status unpacked libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:21 status half-configured libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:21 status installed libxcb-xinerama0 1.8.1-1ubuntu0.2
2014-03-16 09:26:21 configure dzen2 0.8.5-4 <none>
2014-03-16 09:26:21 status unpacked dzen2 0.8.5-4
2014-03-16 09:26:21 status half-configured dzen2 0.8.5-4
2014-03-16 09:26:21 status installed dzen2 0.8.5-4
2014-03-16 09:26:21 configure libev4 1:4.11-1 <none>
2014-03-16 09:26:21 status unpacked libev4 1:4.11-1
2014-03-16 09:26:21 status half-configured libev4 1:4.11-1
2014-03-16 09:26:21 status installed libev4 1:4.11-1
2014-03-16 09:26:21 configure libxcb-icccm4 0.3.8-1build1 <none>
2014-03-16 09:26:21 status unpacked libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:21 status half-configured libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:22 status installed libxcb-icccm4 0.3.8-1build1
2014-03-16 09:26:22 configure libxcb-keysyms1 0.3.8-1build1 <none>
2014-03-16 09:26:22 status unpacked libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:22 status half-configured libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:22 status installed libxcb-keysyms1 0.3.8-1build1
2014-03-16 09:26:22 configure i3-wm 4.1.2-2 <none>
2014-03-16 09:26:22 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:22 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:22 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:22 status unpacked i3-wm 4.1.2-2
2014-03-16 09:26:22 status half-configured i3-wm 4.1.2-2
2014-03-16 09:26:23 status installed i3-wm 4.1.2-2
2014-03-16 09:26:23 configure i3 4.1.2-2 <none>
2014-03-16 09:26:23 status unpacked i3 4.1.2-2
2014-03-16 09:26:23 status half-configured i3 4.1.2-2
2014-03-16 09:26:23 status installed i3 4.1.2-2
2014-03-16 09:26:23 configure libxcb-image0 0.3.8-1build1 <none>
2014-03-16 09:26:23 status unpacked libxcb-image0 0.3.8-1build1
2014-03-16 09:26:23 status half-configured libxcb-image0 0.3.8-1build1
2014-03-16 09:26:23 status installed libxcb-image0 0.3.8-1build1
2014-03-16 09:26:23 configure i3lock 2.2-1 <none>
2014-03-16 09:26:23 status unpacked i3lock 2.2-1
2014-03-16 09:26:23 status unpacked i3lock 2.2-1
2014-03-16 09:26:24 status half-configured i3lock 2.2-1
2014-03-16 09:26:24 status installed i3lock 2.2-1
2014-03-16 09:26:24 configure i3status 2.4-1 <none>
2014-03-16 09:26:24 status unpacked i3status 2.4-1
2014-03-16 09:26:24 status unpacked i3status 2.4-1
2014-03-16 09:26:24 status half-configured i3status 2.4-1
2014-03-16 09:26:24 status installed i3status 2.4-1
2014-03-16 09:26:24 configure suckless-tools 38-1 <none>
2014-03-16 09:26:24 status unpacked suckless-tools 38-1
2014-03-16 09:26:24 status half-configured suckless-tools 38-1
2014-03-16 09:26:24 status installed suckless-tools 38-1
2014-03-16 09:26:24 trigproc libc-bin 2.15-0ubuntu10.5 <none>
2014-03-16 09:26:24 status half-configured libc-bin 2.15-0ubuntu10.5
2014-03-16 09:26:24 status installed libc-bin 2.15-0ubuntu10.5
2014-03-16 09:32:25 startup packages remove
2014-03-16 09:32:25 status installed gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 remove gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1 <none>
2014-03-16 09:32:30 status half-configured gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 status half-installed gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 status config-files gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 status config-files gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 status config-files gir1.2-ubuntuoneui-3.0 3.0.1-0ubuntu1
2014-03-16 09:32:30 status not-installed gir1.2-ubuntuoneui-3.0 <none>
2014-03-16 09:32:30 status installed libubuntuoneui-3.0-1 3.0.1-0ubuntu1
2014-03-16 09:32:30 remove libubuntuoneui-3.0-1 3.0.1-0ubuntu1 <none>
2014-03-16 09:32:30 status half-configured libubuntuoneui-3.0-1 3.0.1-0ubuntu1
2014-03-16 09:32:30 status half-installed libubuntuoneui-3.0-1 3.0.1-0ubuntu1
2014-03-16 09:32:31 status triggers-pending libc-bin 2.15-0ubuntu10.5
2014-03-16 09:32:31 status config-files libubuntuoneui-3.0-1 3.0.1-0ubuntu1
2014-03-16 09:32:31 status config-files libubuntuoneui-3.0-1 3.0.1-0ubuntu1
2014-03-16 09:32:31 status installed thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:31 remove thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-03-16 09:32:31 status half-configured thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:31 status half-installed thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:31 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:31 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:32 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-03-16 09:32:32 status not-installed thunderbird-globalmenu <none>
2014-03-16 09:32:32 trigproc libc-bin 2.15-0ubuntu10.5 <none>
2014-03-16 09:32:32 status half-configured libc-bin 2.15-0ubuntu10.5
2014-03-16 09:32:32 status installed libc-bin 2.15-0ubuntu10.5
2014-03-16 09:39:16 startup archives unpack
2014-03-16 09:39:17 install libvdpau1 <none> 0.4.1-3ubuntu1.1
2014-03-16 09:39:17 status half-installed libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:18 status unpacked libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:18 status unpacked libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:18 install dkms <none> 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:18 status half-installed dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:18 status triggers-pending man-db 2.6.1-2ubuntu1
2014-03-16 09:39:18 status half-installed dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:19 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:19 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:19 install fakeroot <none> 1.18.2-1
2014-03-16 09:39:19 status half-installed fakeroot 1.18.2-1
2014-03-16 09:39:19 status half-installed fakeroot 1.18.2-1
2014-03-16 09:39:20 status unpacked fakeroot 1.18.2-1
2014-03-16 09:39:20 status unpacked fakeroot 1.18.2-1
2014-03-16 09:39:20 install nvidia-304 <none> 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:20 status half-installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:34 status half-installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:34 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2014-03-16 09:39:34 status half-installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:34 status triggers-pending bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:39:34 status half-installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:34 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2014-03-16 09:39:34 status half-installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 status unpacked nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 status unpacked nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 install nvidia-current <none> 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 status half-installed nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 status unpacked nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:37 status unpacked nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:38 install screen-resolution-extra <none> 0.14ubuntu2.1
2014-03-16 09:39:38 status half-installed screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:39:38 status unpacked screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:39:38 status unpacked screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:39:39 install nvidia-settings <none> 331.20-0ubuntu0.0.1
2014-03-16 09:39:39 status half-installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:39 status half-installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:39 status half-installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:39 status half-installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:39 status half-installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:40 status unpacked nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:40 status unpacked nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:39:40 install nvidia-settings-304 <none> 331.20-0ubuntu0.0.1
2014-03-16 09:39:40 status half-installed nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:39:41 status unpacked nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:39:41 status unpacked nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:39:41 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2014-03-16 09:39:41 status half-configured man-db 2.6.1-2ubuntu1
2014-03-16 09:39:45 status installed man-db 2.6.1-2ubuntu1
2014-03-16 09:39:45 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2014-03-16 09:39:45 status half-configured desktop-file-utils 0.20-0ubuntu3
2014-03-16 09:39:45 status installed desktop-file-utils 0.20-0ubuntu3
2014-03-16 09:39:45 trigproc bamfdaemon 0.2.126-0ubuntu1 0.2.126-0ubuntu1
2014-03-16 09:39:45 status half-configured bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:39:46 status installed bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:39:46 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2014-03-16 09:39:46 status half-configured gnome-menus 3.4.0-0ubuntu1
2014-03-16 09:39:46 status installed gnome-menus 3.4.0-0ubuntu1
2014-03-16 09:39:47 startup packages configure
2014-03-16 09:39:47 configure libvdpau1 0.4.1-3ubuntu1.1 <none>
2014-03-16 09:39:47 status unpacked libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:47 status unpacked libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:47 status half-configured libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:47 status installed libvdpau1 0.4.1-3ubuntu1.1
2014-03-16 09:39:47 status triggers-pending libc-bin 2.15-0ubuntu10.5
2014-03-16 09:39:47 configure dkms 2.2.0.3-1ubuntu3.2 <none>
2014-03-16 09:39:47 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:47 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:47 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:47 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:47 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status unpacked dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status half-configured dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 status installed dkms 2.2.0.3-1ubuntu3.2
2014-03-16 09:39:48 configure fakeroot 1.18.2-1 <none>
2014-03-16 09:39:48 status unpacked fakeroot 1.18.2-1
2014-03-16 09:39:48 status half-configured fakeroot 1.18.2-1
2014-03-16 09:39:49 status installed fakeroot 1.18.2-1
2014-03-16 09:39:49 configure nvidia-304 304.116-0ubuntu1~xedgers~precise1 <none>
2014-03-16 09:39:49 status unpacked nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:49 status unpacked nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:39:49 status half-configured nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:10 status installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:10 status triggers-pending bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:41:10 status triggers-awaited nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:10 status triggers-pending initramfs-tools 0.99ubuntu13.4
2014-03-16 09:41:10 configure screen-resolution-extra 0.14ubuntu2.1 <none>
2014-03-16 09:41:10 status unpacked screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:41:10 status unpacked screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:41:10 status half-configured screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:41:11 status installed screen-resolution-extra 0.14ubuntu2.1
2014-03-16 09:41:11 configure nvidia-settings 331.20-0ubuntu0.0.1 <none>
2014-03-16 09:41:11 status unpacked nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 status unpacked nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 status half-configured nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 status installed nvidia-settings 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 configure nvidia-settings-304 331.20-0ubuntu0.0.1 <none>
2014-03-16 09:41:11 status unpacked nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 status half-configured nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:41:11 status installed nvidia-settings-304 331.20-0ubuntu0.0.1
2014-03-16 09:41:12 trigproc bamfdaemon 0.2.126-0ubuntu1 <none>
2014-03-16 09:41:12 status half-configured bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:41:12 status installed nvidia-304 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:12 status installed bamfdaemon 0.2.126-0ubuntu1
2014-03-16 09:41:12 configure nvidia-current 304.116-0ubuntu1~xedgers~precise1 <none>
2014-03-16 09:41:12 status unpacked nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:12 status half-configured nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:12 status installed nvidia-current 304.116-0ubuntu1~xedgers~precise1
2014-03-16 09:41:12 trigproc libc-bin 2.15-0ubuntu10.5 <none>
2014-03-16 09:41:12 status half-configured libc-bin 2.15-0ubuntu10.5
2014-03-16 09:41:12 status installed libc-bin 2.15-0ubuntu10.5
2014-03-16 09:41:12 trigproc initramfs-tools 0.99ubuntu13.4 <none>
2014-03-16 09:41:12 status half-configured initramfs-tools 0.99ubuntu13.4
2014-03-16 09:41:40 status installed initramfs-tools 0.99ubuntu13.4



Thank you for your quick reply!

---

### Post by r.stiltskin on 2014-03-16
Well that's a bit of a mess.  One thing's for sure -- you have a radeon video card, not nvidia, so to begin with you need to get rid of the nvidia driver:

```

sudo apt-get purge nvidia*

```

Next, to install radeon or to find out if the radeon driver is still installed run
```

sudo apt-get install xserver-xorg-video-radeon

```
If that tells you that xserver-xorg-video-radeon is already the newest version, then run
```

sudo dpkg-reconfigure xserver-xorg-video-radeon

```

That should get your screen back at least to the way it was immediately after the updates but I don't think it will solve the original problem.  One thing I see in the output from your dpkg log that might have caused your problem is i3-wm -- a window manager.  But I don't know why you have i3 in the first place.  I'm not familiar with Cinnamon.  Is i3 the standard window manager for Cinnamon?  If nobody else chimes in with some ideas I'll see what I can find later.  In the meantime get rid of nvidia and get your radeon driver reinstalled or reconfigured.

---

### Post by wstrong714 on 2014-03-16
Okay.... I got rid of the nvidia driver...So now cinnamon doesn't crash....THANK YOU!  Not sure why I thought I had an nvidia card, must be my older laptop.  As for the i3, I installed it to experiment with the tiling wondows manager.  I normally use Cinnamon because I can't stand Unity.  I am going to try to uninstall i3 to see if that is messing with the screen, though I am not sure why it would.  When I start up, I have a choice between Unity and Cinnamon, and now i3..It doesn't run if I don't choose it.  I'll give it a go, though.  I let you know if it fixws anything.

---

### Post by wstrong714 on 2014-03-16
And now i3 is finally removed.  But my screen is still stretched,  Ugh.  Any more thoughts?

---

### Post by r.stiltskin on 2014-03-16
Have you looked at the available display resolutions in your Settings Manager/Display dialog?  It might be as simple as clicking on a different resolution.

---

### Post by jim87 on 2015-01-30
What is the significance of the vertical line in the command :
lspci | grep -i vga

---

### Post by r.stiltskin on 2015-02-01
It's called a pipe.  You're actually looking at two commands, **lspci** and **grep -i vga**.   The pipe takes the output from lspci and sends it as input to grep.  **lspci** lists all pci devices.  **grep -i vga [*inputfile*]** outputs all lines in [*inputfile*] containing "vga" or "VGA", etc,  (ignoring case because of the -i option).  So in this case grep's "inputfile" is the output from lspci because of the pipe, and the result of the combined command is just to print to the screen the pci devices containing "vga" in their descriptions.

---

