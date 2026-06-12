---
title: "1-5-2023 Update Disaster... Help!!"
date: 2023-01-06
forum: General Help
---

### Post by BlueAZ on 2023-01-06
Hi,  I used Software Updater yesterday to check for updates for my Ubuntu 22.04 64-bit desktop.  A bunch showed up, so I clicked Install as I always do.  To my horror, I saw that Updater was actually removing stuff; lots of stuff...  Stuff I use daily!  I took a deep breath & thought:  Ubuntu won't let me down, Updater will replace the removed stuff with updated versions!  WRONG!!!  I lost a lot of applications and normal functions.  How could this happen?  Who put together this disastrous update??!!!
So far, I've been able to replace some applications through the Software Store, but it's time-consuming.  And it appears I've lost any type of Desktop at all: no dock on the left, no cursor just a gray box, no desktop icons.  I need help replacing my Desktop...  like, how?  And with what?  I was already frustrated that I couldn't open files from my desktop icons, so I'd like one that will do that.  And I REALLY need the dock back!!
Many Thanks!!  :rolleyes:

---

### Post by Impavidus on 2023-01-07
It sounds like one of the upgraded packages had a conflict with something important and the update manager decided to remove the important thing to allow the upgrade to proceed. This is most common when using software from unofficial sources. Always look at the list of packages marked for upgrade, installation or removal. That's why we don't recommend automatic upgrades, although Ubuntu offers them.

Let's see what packages were actually removed and upgraded:```
grep '2023-01-05' /var/log/dpkg.log | grep ' upgrade \| remove '
```
The configuration of the removed packages should still be there, so most can be restored simply by reinstalling them. This may trigger removal of the package whose upgrade caused this trouble.

---

### Post by BlueAZ on 2023-01-07
Here is that output from Terminal:
```
:~$ grep '2023-01-05' /var/log/dpkg.log | grep ' upgrade \| remove '
2023-01-05 14:22:01 upgrade gnome-remote-desktop:amd64 42.4-0ubuntu1 42.7-0ubuntu1
2023-01-05 14:22:07 upgrade libcurl3-gnutls:i386 7.81.0-1ubuntu1.6 7.81.0-1ubuntu1.7
2023-01-05 14:22:08 upgrade libcurl3-gnutls:amd64 7.81.0-1ubuntu1.6 7.81.0-1ubuntu1.7
2023-01-05 14:22:08 upgrade libcurl4:i386 7.81.0-1ubuntu1.6 7.81.0-1ubuntu1.7
2023-01-05 14:22:09 upgrade libcurl4:amd64 7.81.0-1ubuntu1.6 7.81.0-1ubuntu1.7
2023-01-05 14:22:10 upgrade libksba8:amd64 1.6.0-2ubuntu0.1 1.6.0-2ubuntu0.2
2023-01-05 14:22:11 upgrade nautilus:amd64 1:42.2-0ubuntu1 1:42.2-0ubuntu2.1
2023-01-05 14:22:15 upgrade nautilus-data:all 1:42.2-0ubuntu1 1:42.2-0ubuntu2.1
2023-01-05 14:22:16 upgrade libnautilus-extension1a:amd64 1:42.2-0ubuntu1 1:42.2-0ubuntu2.1
2023-01-05 14:23:08 remove acpi-support:amd64 0.144 <none>
2023-01-05 14:23:08 remove acpid:amd64 1:2.0.33-1ubuntu1 <none>
2023-01-05 14:23:12 remove aisleriot:amd64 1:3.22.22-1 <none>
2023-01-05 14:23:14 remove apt-config-icons-hidpi:all 0.15.2-2 <none>
2023-01-05 14:23:14 remove nautilus-share:amd64 0.7.3-2ubuntu6 <none>
2023-01-05 14:23:15 remove apturl:amd64 0.5.2ubuntu22 <none>
2023-01-05 14:23:16 remove apturl-common:amd64 0.5.2ubuntu22 <none>
2023-01-05 14:23:16 remove baobab:amd64 41.0-2 <none>
2023-01-05 14:23:17 remove bluez-cups:amd64 5.64-0ubuntu1 <none>
2023-01-05 14:23:18 remove branding-ubuntu:all 0.10 <none>
2023-01-05 14:23:19 remove cheese:amd64 41.1-1build1 <none>
2023-01-05 14:23:19 remove deja-dup:amd64 42.9-1ubuntu3 <none>
2023-01-05 14:23:20 remove dmz-cursor-theme:all 0.4.5ubuntu1 <none>
2023-01-05 14:23:21 remove duplicity:amd64 0.8.21-1build1 <none>
2023-01-05 14:23:21 remove eog:amd64 42.0-1 <none>
2023-01-05 14:23:23 remove gnome-shell-extension-desktop-icons-ng:all 43-2ubuntu1 <none>
2023-01-05 14:23:24 remove file-roller:amd64 3.42.0-1 <none>
2023-01-05 14:23:24 remove fonts-kacst:all 2.01+mry-15 <none>
2023-01-05 14:23:25 remove fonts-kacst-one:all 5.0+svn11846-10 <none>
2023-01-05 14:23:26 remove fonts-khmeros-core:all 5.0-9ubuntu1 <none>
2023-01-05 14:23:26 remove fonts-lao:all 0.0.20060226-10ubuntu2 <none>
2023-01-05 14:23:26 remove fonts-lklug-sinhala:all 0.6-4 <none>
2023-01-05 14:23:27 remove fonts-noto-cjk:all 1:20220127+repack1-1 <none>
2023-01-05 14:23:27 remove fonts-noto-color-emoji:all 2.034-1 <none>
2023-01-05 14:23:28 remove fonts-sil-abyssinica:all 2.100-3 <none>
2023-01-05 14:23:29 remove fonts-sil-padauk:all 5.000-3 <none>
2023-01-05 14:23:29 remove fonts-thai-tlwg:all 1:0.7.3-1 <none>
2023-01-05 14:23:30 remove fonts-tibetan-machine:all 1.901b-6 <none>
2023-01-05 14:23:30 remove fonts-tlwg-garuda:all 1:0.7.3-1 <none>
2023-01-05 14:23:31 remove fonts-tlwg-garuda-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:31 remove fonts-tlwg-kinnari:all 1:0.7.3-1 <none>
2023-01-05 14:23:31 remove fonts-tlwg-kinnari-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:32 remove fonts-tlwg-laksaman:all 1:0.7.3-1 <none>
2023-01-05 14:23:32 remove fonts-tlwg-laksaman-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:33 remove fonts-tlwg-loma:all 1:0.7.3-1 <none>
2023-01-05 14:23:33 remove fonts-tlwg-loma-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:34 remove fonts-tlwg-mono:all 1:0.7.3-1 <none>
2023-01-05 14:23:34 remove fonts-tlwg-mono-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:35 remove fonts-tlwg-norasi:all 1:0.7.3-1 <none>
2023-01-05 14:23:35 remove fonts-tlwg-norasi-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:36 remove fonts-tlwg-purisa:all 1:0.7.3-1 <none>
2023-01-05 14:23:36 remove fonts-tlwg-purisa-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:37 remove fonts-tlwg-sawasdee:all 1:0.7.3-1 <none>
2023-01-05 14:23:37 remove fonts-tlwg-sawasdee-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:38 remove fonts-tlwg-typewriter:all 1:0.7.3-1 <none>
2023-01-05 14:23:38 remove fonts-tlwg-typewriter-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:40 remove fonts-tlwg-typist:all 1:0.7.3-1 <none>
2023-01-05 14:23:41 remove fonts-tlwg-typist-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:41 remove fonts-tlwg-typo:all 1:0.7.3-1 <none>
2023-01-05 14:23:42 remove fonts-tlwg-typo-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:42 remove fonts-tlwg-umpush:all 1:0.7.3-1 <none>
2023-01-05 14:23:43 remove fonts-tlwg-umpush-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:43 remove fonts-tlwg-waree:all 1:0.7.3-1 <none>
2023-01-05 14:23:44 remove fonts-tlwg-waree-ttf:all 1:0.7.3-1 <none>
2023-01-05 14:23:44 remove fwupd:amd64 1.7.9-1~22.04.1 <none>
2023-01-05 14:23:47 remove fwupd-signed:amd64 1.44+1.2-3 <none>
2023-01-05 14:23:48 remove gamemode:amd64 1.6.1-1build2 <none>
2023-01-05 14:23:49 remove libgamemode0:amd64 1.6.1-1build2 <none>
2023-01-05 14:23:49 remove gamemode-daemon:amd64 1.6.1-1build2 <none>
2023-01-05 14:23:50 remove usb-creator-gtk:all 0.3.13 <none>
2023-01-05 14:23:50 remove usb-creator-common:all 0.3.13 <none>
2023-01-05 14:23:51 remove genisoimage:amd64 9:1.1.11-3.2ubuntu1 <none>
2023-01-05 14:23:51 remove totem-plugins:amd64 42.0-1ubuntu1 <none>
2023-01-05 14:23:52 remove gir1.2-totem-1.0:amd64 42.0-1ubuntu1 <none>
2023-01-05 14:23:52 remove gir1.2-totemplparser-1.0:amd64 3.26.6-1build1 <none>
2023-01-05 14:23:53 remove gnome-accessibility-themes:all 3.28-1ubuntu3 <none>
2023-01-05 14:23:54 remove gnome-bluetooth:amd64 3.34.5-8 <none>
2023-01-05 14:23:54 remove gnome-calculator:amd64 1:41.1-2ubuntu2 <none>
2023-01-05 14:23:55 remove gnome-calendar:amd64 41.2-3 <none>
2023-01-05 14:23:56 remove gnome-characters:amd64 41.0-4 <none>
2023-01-05 14:23:57 remove gnome-disk-utility:amd64 42.0-1ubuntu1 <none>
2023-01-05 14:23:57 remove gnome-font-viewer:amd64 41.0-2 <none>
2023-01-05 14:23:58 remove gnome-initial-setup:amd64 42.0.1-1ubuntu2 <none>
2023-01-05 14:23:59 remove gnome-logs:amd64 42.0-1 <none>
2023-01-05 14:24:00 remove gnome-mahjongg:amd64 1:3.38.3-2 <none>
2023-01-05 14:24:01 remove gnome-mines:amd64 1:40.1-1 <none>
2023-01-05 14:24:03 remove gnome-power-manager:amd64 3.32.0-2build2 <none>
2023-01-05 14:24:03 remove gnome-session-canberra:amd64 0.30-10ubuntu1 <none>
2023-01-05 14:24:04 remove gnome-shell-extension-ubuntu-dock:all 72~ubuntu5.22.04.1 <none>
2023-01-05 14:24:04 remove gnome-sudoku:amd64 1:42.0-1 <none>
2023-01-05 14:24:05 remove gnome-system-monitor:amd64 42.0-1 <none>
2023-01-05 14:24:06 remove yaru-theme-gtk:all 22.04.4 <none>
2023-01-05 14:24:07 remove gnome-themes-extra:amd64 3.28-1ubuntu3 <none>
2023-01-05 14:24:08 remove gnome-themes-extra-data:all 3.28-1ubuntu3 <none>
2023-01-05 14:24:08 remove gnome-todo:amd64 3.28.1-6ubuntu1 <none>
2023-01-05 14:24:09 remove gnome-todo-common:all 3.28.1-6ubuntu1 <none>
2023-01-05 14:24:09 remove gnome-video-effects:all 0.5.0-1ubuntu1 <none>
2023-01-05 14:24:10 remove totem:amd64 42.0-1ubuntu1 <none>
2023-01-05 14:24:11 remove grilo-plugins-0.3-base:amd64 0.3.14-1ubuntu2 <none>
2023-01-05 14:24:11 remove gsettings-ubuntu-schemas:all 0.0.7+21.10.20210712-0ubuntu2 <none>
2023-01-05 14:24:12 remove gstreamer1.0-gtk3:amd64 1.20.3-0ubuntu1 <none>
2023-01-05 14:24:13 remove gstreamer1.0-packagekit:amd64 1.2.5-2ubuntu2 <none>
2023-01-05 14:24:13 remove gstreamer1.0-plugins-base-apps:amd64 1.20.1-1 <none>
2023-01-05 14:24:14 remove gtk2-engines-murrine:amd64 0.98.2-3build2 <none>
2023-01-05 14:24:14 remove gtk2-engines-pixbuf:amd64 2.24.33-2ubuntu2 <none>
2023-01-05 14:24:15 remove guile-2.2-libs:amd64 2.2.7+1-6build2 <none>
2023-01-05 14:24:15 remove gvfs-fuse:amd64 1.48.2-0ubuntu1 <none>
2023-01-05 14:24:16 remove ibus-table:all 1.16.7-1 <none>
2023-01-05 14:24:17 remove inputattach:amd64 1:1.7.1-1build2 <none>
2023-01-05 14:24:17 remove kerneloops:amd64 0.12+git20140509-6ubuntu5 <none>
2023-01-05 14:24:18 remove laptop-detect:all 0.16 <none>
2023-01-05 14:24:18 remove remmina-plugin-vnc:amd64 1.4.25+dfsg-1 <none>
2023-01-05 14:24:19 remove remmina-plugin-secret:amd64 1.4.25+dfsg-1 <none>
2023-01-05 14:24:20 remove libreoffice-ogltrans:all 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:20 remove libreoffice-impress:amd64 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:21 remove libreoffice-draw:amd64 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:22 remove libcdr-0.1-1:amd64 0.1.6-2build2 <none>
2023-01-05 14:24:22 remove nautilus:amd64 1:42.2-0ubuntu2.1 <none>
2023-01-05 14:24:23 remove tracker-miner-fs:amd64 3.3.0-1 <none>
2023-01-05 14:24:24 remove tracker-extract:amd64 3.3.0-1 <none>
2023-01-05 14:24:24 remove libcue2:amd64 2.2.1-3build3 <none>
2023-01-05 14:24:25 remove libdazzle-1.0-0:amd64 3.44.0-1 <none>
2023-01-05 14:24:25 remove libdazzle-common:all 3.44.0-1 <none>
2023-01-05 14:24:26 remove transmission-gtk:amd64 3.00-2ubuntu2 <none>
2023-01-05 14:24:26 remove libevent-2.1-7:amd64 2.1.12-stable-1build3 <none>
2023-01-05 14:24:27 remove libexempi8:amd64 2.5.2-1ubuntu0.22.04.1 <none>
2023-01-05 14:24:27 remove libfreehand-0.1-1:amd64 0.1.2-3build2 <none>
2023-01-05 14:24:28 remove libfwupdplugin5:amd64 1.7.9-1~22.04.1 <none>
2023-01-05 14:24:28 remove libfwupd2:amd64 1.7.9-1~22.04.1 <none>
2023-01-05 14:24:29 remove libgamemodeauto0:amd64 1.6.1-1build2 <none>
2023-01-05 14:24:29 remove libgc1:amd64 1:8.0.6-1.1build1 <none>
2023-01-05 14:24:30 remove libgcab-1.0-0:amd64 1.4-3build2 <none>
2023-01-05 14:24:30 remove libgif7:amd64 5.1.9-2build2 <none>
2023-01-05 14:24:31 remove libgnome-games-support-1-3:amd64 1.8.2-1build1 <none>
2023-01-05 14:24:31 remove libgnome-games-support-common:all 1.8.2-1build1 <none>
2023-01-05 14:24:32 remove libgnome-todo:amd64 3.28.1-6ubuntu1 <none>
2023-01-05 14:24:32 remove libgom-1.0-0:amd64 0.4-1build2 <none>
2023-01-05 14:24:33 remove libtotem0:amd64 42.0-1ubuntu1 <none>
2023-01-05 14:24:33 remove libgrilo-0.3-0:amd64 0.3.14-1build1 <none>
2023-01-05 14:24:34 remove libgsf-1-114:amd64 1.14.47-1build2 <none>
2023-01-05 14:24:34 remove libgsf-1-common:all 1.14.47-1build2 <none>
2023-01-05 14:24:35 remove libinih1:amd64 53-1ubuntu3 <none>
2023-01-05 14:24:35 remove libjcat1:amd64 0.1.9-1 <none>
2023-01-05 14:24:36 remove liblua5.3-0:amd64 5.3.6-1build1 <none>
2023-01-05 14:24:37 remove libminiupnpc17:amd64 2.2.3-1build1 <none>
2023-01-05 14:24:37 remove libmspub-0.1-1:amd64 0.1.4-3build3 <none>
2023-01-05 14:24:38 remove libnatpmp1:amd64 20150609-7.1build2 <none>
2023-01-05 14:24:38 remove libpagemaker-0.0-0:amd64 0.0.4-1build3 <none>
2023-01-05 14:24:39 remove libproxy1-plugin-gsettings:amd64 0.4.17-2 <none>
2023-01-05 14:24:39 remove libproxy1-plugin-networkmanager:amd64 0.4.17-2 <none>
2023-01-05 14:24:40 remove libqqwing2v5:amd64 1.3.4-1.1ubuntu3 <none>
2023-01-05 14:24:40 remove libreoffice-calc:amd64 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:41 remove libreoffice-gnome:amd64 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:41 remove libreoffice-gtk3:amd64 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:42 remove libreoffice-pdfimport:all 1:7.3.7-0ubuntu0.22.04.1 <none>
2023-01-05 14:24:42 remove librsync2:amd64 2.3.2-1ubuntu1 <none>
2023-01-05 14:24:44 remove libsmbios-c2:amd64 2.4.3-1build1 <none>
2023-01-05 14:24:45 remove libsysmetrics1:amd64 1.7.1 <none>
2023-01-05 14:24:45 remove libtotem-plparser18:amd64 3.26.6-1build1 <none>
2023-01-05 14:24:46 remove libtotem-plparser-common:all 3.26.6-1build1 <none>
2023-01-05 14:24:46 remove tracker:amd64 3.3.0-1 <none>
2023-01-05 14:24:47 remove libtracker-sparql-3.0-0:amd64 3.3.0-1 <none>
2023-01-05 14:24:47 remove libu2f-udev:all 1.1.10-3build2 <none>
2023-01-05 14:24:48 remove libvisio-0.1-1:amd64 0.1.7-1build5 <none>
2023-01-05 14:24:48 remove libvncclient1:amd64 0.9.13+dfsg-3build2 <none>
2023-01-05 14:24:49 remove libwmf0.2-7-gtk:amd64 0.2.12-5ubuntu1 <none>
2023-01-05 14:24:49 remove libwmf-0.2-7-gtk:amd64 0.2.12-5ubuntu1 <none>
2023-01-05 14:24:50 remove libwmf-0.2-7:amd64 0.2.12-5ubuntu1 <none>
2023-01-05 14:24:50 remove lp-solve:amd64 5.5.2.5-2build2 <none>
2023-01-05 14:24:51 remove memtest86+:amd64 5.31b+dfsg-4 <none>
2023-01-05 14:25:04 remove mousetweaks:amd64 3.32.0-3build2 <none>
2023-01-05 14:25:05 remove nautilus-data:all 1:42.2-0ubuntu2.1 <none>
2023-01-05 14:25:05 remove network-manager-config-connectivity-ubuntu:all 1.36.6-0ubuntu2 <none>
2023-01-05 14:25:06 remove pcmciautils:amd64 018-13build1 <none>
2023-01-05 14:25:07 remove policykit-desktop-privileges:all 0.21 <none>
2023-01-05 14:25:07 remove python3-paramiko:all 2.9.3-0ubuntu1 <none>
2023-01-05 14:25:08 remove python3-bcrypt:amd64 3.2.0-1build1 <none>
2023-01-05 14:25:09 remove python3-future:all 0.18.2-5 <none>
2023-01-05 14:25:09 remove python3-lockfile:all 1:0.12.2-2.2 <none>
2023-01-05 14:25:10 remove remmina-plugin-rdp:amd64 1.4.25+dfsg-1 <none>
2023-01-05 14:25:11 remove rfkill:amd64 2.37.2-4ubuntu3 <none>
2023-01-05 14:25:11 remove seahorse:amd64 41.0-2 <none>
2023-01-05 14:25:13 remove simple-scan:amd64 42.0-1 <none>
2023-01-05 14:25:14 remove spice-vdagent:amd64 0.22.1-1 <none>
2023-01-05 14:25:16 remove systemd-oomd:amd64 249.11-0ubuntu3.6 <none>
2023-01-05 14:25:17 remove totem-common:all 42.0-1ubuntu1 <none>
2023-01-05 14:25:18 remove transmission-common:all 3.00-2ubuntu2 <none>
2023-01-05 14:25:19 remove ubuntu-report:amd64 1.7.1 <none>
2023-01-05 14:25:20 remove ubuntu-settings:all 22.04.6 <none>
2023-01-05 14:25:20 remove xorg:amd64 1:7.7+23ubuntu2 <none>
2023-01-05 14:25:21 remove x11-apps:amd64 7.7+8build2 <none>
2023-01-05 14:25:21 remove x11-session-utils:amd64 7.7+4build2 <none>
2023-01-05 14:25:22 remove xbitmaps:all 1.1.1-2.1ubuntu1 <none>
2023-01-05 14:25:23 remove xcursor-themes:all 1.0.6-0ubuntu1 <none>
2023-01-05 14:25:23 remove xdg-user-dirs-gtk:amd64 0.10-3build2 <none>
2023-01-05 14:25:23 remove xinit:amd64 1.4.1-0ubuntu4 <none>
2023-01-05 14:25:24 remove yaru-theme-icon:all 22.04.4 <none>
2023-01-05 14:25:25 remove yaru-theme-sound:all 22.04.4 <none>
2023-01-05 14:25:26 remove remmina:amd64 1.4.25+dfsg-1 <none>
2023-01-05 14:25:27 remove libavahi-ui-gtk3-0:amd64 0.8-5ubuntu5 <none>
2023-01-05 14:25:28 remove remmina-common:all 1.4.25+dfsg-1 <none>
2023-01-05 14:27:06 upgrade libsasl2-modules-db:amd64 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:07 upgrade libsasl2-modules-db:i386 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:08 upgrade libsasl2-2:i386 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:08 upgrade libsasl2-2:amd64 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:09 upgrade libsasl2-modules-gssapi-mit:amd64 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:10 upgrade libsasl2-modules:i386 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
2023-01-05 14:27:10 upgrade libsasl2-modules:amd64 2.1.27+dfsg2-3ubuntu1 2.1.27+dfsg2-3ubuntu1.1
```

As you can see, it's a lot.  I just don't know what many of these things are, what they do, etc.

---

### Post by BlueAZ on 2023-01-07
Trying more things to get back to normal...  Tried to install the gnome DE in Terminal, but it wouldn't install.  Went into Symantec and found the following:
Three grub-2 packages are 'broken'.  It won't 'upgrade' them, and I don't want to remove them in case they are the only grub on here.  12 packages won't upgrade.

---

### Post by #&amp;thj^% on 2023-01-07
Show us this:
```
dpkg -l | grep grub | grep ii

```

---

### Post by BlueAZ on 2023-01-07
Here is that:
:~$ dpkg -l | grep grub | grep ii
ii  grub-common                           2.06-2ubuntu7                           amd64        GRand Unified Bootloader (common files)
ii  grub-efi-amd64-bin                    2.06-2ubuntu10                          amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 modules)
ii  grub-efi-amd64-signed                 1.182~22.04.1+2.06-2ubuntu10            amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
ii  grub-gfxpayload-lists                 0.7                                     amd64        GRUB gfxpayload blacklist
ii  grub-pc                               2.06-2ubuntu7                           amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                           2.06-2ubuntu7                           amd64        GRand Unified Bootloader, version 2 (PC/BIOS modules)
ii  grub2-common                          2.06-2ubuntu7                           amd64        GRand Unified Bootloader (common files for version 2)

The 'ii's are in red.

---

### Post by Impavidus on 2023-01-08
No obvious problems yet...

Let's see what packages aren't properly installed:```
dpkg --list | grep -v '^ii \|^rc '
```

---

### Post by deadflowr on 2023-01-08
Not sure if related, but gnome-remote-desktop is in phased updates and was phased to 70% of users but has been pulled back because of errors.
This page is dynamic so it will change every few hours: [https://people.canonical.com/~ubuntu-archive/phased-updates.html]("https://people.canonical.com/~ubuntu-archive/phased-updates.html")

---

### Post by #&amp;thj^% on 2023-01-08
deadflowr could be on to something here:
```
gnome-remote-desktop 	42.7-0ubuntu1 (jbicha) 	0% of users (was 70%) 		448eb0 11f28b 	4
grub2 	2.06-2ubuntu7.1 (juliank) 	24% of users 			4
```
Sure hope they get this phased stuff a little smoother, and soon.

---

### Post by BlueAZ on 2023-01-08
> **Impavidus said:**
> No obvious problems yet...

Let's see what packages aren't properly installed:```
dpkg --list | grep -v '^ii \|^rc '
```

Here is that output:
:~$ dpkg --list | grep -v '^ii \|^rc '
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                                 Architecture Description
+++-=====================================-=======================================-============-================================================================================

I have no idea what this means...

---

### Post by Impavidus on 2023-01-09
It means that no packages are broken.

Maybe a faulty upgrade to gnome-remote-desktop is the problem. Can you reinstall the removed packages? Some of the higher-level ones may pull in the lower-level ones, so you don't have to do all of them manually. It may be necessary to remove gnome-remote-desktop, if that's the cause of your trouble. You can then reinstall it later.

Don't do anything about the grub packages now. They aren't broken. There's an update to grub on the way, but it still in phased updates, so it may take some days before you get it.

---

### Post by BlueAZ on 2023-01-09
> **deadflowr said:**
> Not sure if related, but gnome-remote-desktop is in phased updates and was phased to 70% of users but has been pulled back because of errors.
This page is dynamic so it will change every few hours: [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)

Thanks Deadflowr.  Just so I understand, does this mean that my gnome-desktop isn't working because the update for gnome-remote-desktop isn't working?  If that's true, it's really too bed that the two are connected.  I've never used remote desktop, but I absolutely rely on my basic desktop!!  Any way to just get that back?  I've tried & it just won't download or install.  Any ideas on that?
Thanks again!

---

### Post by BlueAZ on 2023-01-09
> **Impavidus said:**
> It means that no packages are broken.

Maybe a faulty upgrade to gnome-remote-desktop is the problem. Can you reinstall the removed packages? Some of the higher-level ones may pull in the lower-level ones, so you don't have to do all of them manually. It may be necessary to remove gnome-remote-desktop, if that's the cause of your trouble. You can then reinstall it later.

Don't do anything about the grub packages now. They aren't broken. There's an update to grub on the way, but it still in phased updates, so it may take some days before you get it.

Thanks Impavidus!  It's good to know that no packages are broken.  But it doesn't explain why Synaptic tells me there are broken packages.  
Can I remove gnome-remote-desktop through Ubuntu Software?  I don't think I've ever used it, so won't miss it.  If that allows me to reinstall gnome-desktop, I'll be happy!
And yes, I have been able to reinstall other packages that were removed by the update.  I'm not sure, but it appears they are now snap packages instead of applications.  That confuses me, as a basic but committed Ubuntu user!

---

### Post by #&amp;thj^% on 2023-01-09
What's the upgrade command show:
```
sudo apt upgrade
```
and:
```
sudo apt --fix-broken install
```

---

### Post by BlueAZ on 2023-01-09
Hi 1Fallen,   Here is output from terminal:

:~$ sudo apt update
[sudo] password for blue: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [114 kB]     
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]      
Hit:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease                 
Get:5 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-security InRelease [7,453 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [99.8 kB]  
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [799 kB]
Hit:8 [https://ppa.launchpadcontent.net/rvm/smplayer/ubuntu](https://ppa.launchpadcontent.net/rvm/smplayer/ubuntu) jammy InRelease
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 DEP-11 Metadata [41.6 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 DEP-11 Metadata [13.3 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main i386 Packages [401 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main Translation-en [177 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 DEP-11 Metadata [97.1 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 Packages [527 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted Translation-en [80.6 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 DEP-11 Metadata [257 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports/universe amd64 DEP-11 Metadata [11.4 kB]
Fetched 2,738 kB in 1s (1,950 kB/s)                                  
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.

And:  :~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

The 4 not upgraded are grub 2 packages, which I see are problematic for everyone.  But this is looking better.  I still can't reinstall gnome-desktop though:

:~$ sudo apt install gnome-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package gnome-desktop

---

### Post by #&amp;thj^% on 2023-01-09
one more:
```
apt list --upgradeable
```

---

### Post by BlueAZ on 2023-01-09
All that shows is:

:~$ apt list upgradeable
Listing... Done

and nothing more...

---

### Post by #&amp;thj^% on 2023-01-09
Just had to check u know.;)
follow this for now please:
```
sudo apt install tasksel
```
now run;
```
sudo tasksel install ubuntu-desktop
```
stop on any error and paste it back here.

---

### Post by oldfred on 2023-01-09
I do not see a gnome-desktop in synaptic.

I see gnome which says it is the gnome desktop as a meta-packed which then will install a variety of gnome related packages.

---

### Post by #&amp;thj^% on 2023-01-09
> **oldfred said:**
> I do not see a gnome-desktop in synaptic.

I see gnome which says it is the gnome desktop as a meta-packed which then will install a variety of gnome related packages.

+1 it just installs a vanilla gnome-desktop and not gnome-shell. Thanks for that oldfred, great point.
EDIT:
```
apt search gnome-remote
Sorting... Done
Full Text Search... Done
gnome-remote-desktop/unstable,now 43.2-1 amd64 [installed,automatic]
  Remote desktop daemon for GNOME using PipeWire

```
I'm running "debian sid" so yours will look different

---

### Post by BlueAZ on 2023-01-09
1fallen,  I had already tried that.  Tasksel is installed, is latest version.  When I run sudo tasksel install ubuntu-desktop, there is a pause, then nothing, Terminal returns to my lead-in script + :~$

---

### Post by #&amp;thj^% on 2023-01-09
Hard for me to know what you have done to date, pardon any repetition, this could lead to a corrupt desktop.
For now if you want to be absolutely sure of a good desktop install, then use instead:
```
sudo tasksel install --new-install ubuntu-desktop
```
no harm in that, unless you've done that as well previously. 
Or just wait it out until your phased out....LOL(pun)

---

### Post by BlueAZ on 2023-01-09
Wow!  That worked, I think.  Thanks 1fallen!
Over 150 packages were installed & configured.  Most look like the items removed by the 1-5-23 update.
I'll have to reboot, but am in the middle of some things, so I'll do that later & report back.

---

### Post by #&amp;thj^% on 2023-01-09
Cool, I'll check back as well.

---

### Post by BlueAZ on 2023-01-09
Well, that did add back a lot of stuff...   After rebooting there are loads of games I'm not interested in, etc.  But my desktop is still not as it was.  
First question:  what was it about that command that finally made something happen?  I'm pretty baffled by command syntax, other than the basics.
Q2:  Now I don't trust Software Updater, so is it safer to use sudo apt update in Terminal?
Q3:  Has Canonical changed the gnome desktop?  What I see now is just the image from my wallpaper changer and the top panel.  If I click Activities, the background image shrinks to a rectangle above another rectangle which contains my Favorites.  I'd like to have them in a dock on the left side of the screen, like before.  I'd also like to be able to see and open icons I've placed on the Desktop.  Now Desktop is just another folder in Home, so it's a multi-step process to get to them.  I keep certain things on the Desktop to remind me of events & things I need to do.  I seriously want all that functionality back!
Thanks

---

### Post by Impavidus on 2023-01-10
Don't worry about those grub packages. Synaptic puts an exclamation mark on them because an upgrade is available. It's still in phased updates and most users haven't got it yet. You can force it, if you like.

I'm not familiar with tasksel. It's not installed on my Xubuntu system. I don't know what that was supposed to do. Neither is gnome-remote-desktop installed, but I know it's optional.

As far as deb packages are concerned, software updater, the apt command line tools and synaptic behave exactly the same. You do have reason not to trust unattened updates. I disabled them. Look at the list of proposed changes before applying them.

---

### Post by maglin2 on 2023-01-10
> **BlueAZ said:**
> 
Q3:  Has Canonical changed the gnome desktop?  What I see now is just the image from my wallpaper changer and the top panel.  If I click Activities, the background image shrinks to a rectangle above another rectangle which contains my Favorites.  I'd like to have them in a dock on the left side of the screen, like before.  I'd also like to be able to see and open icons I've placed on the Desktop.  Now Desktop is just another folder in Home, so it's a multi-step process to get to them.  I keep certain things on the Desktop to remind me of events & things I need to do.  I seriously want all that functionality back!
Thanks

That doesn't sound like you've got the full ubuntu desktop with default extensions yet.
You could try installing gnome-shell-extensions
Then launch it and make sure the Built-In extensions are all shown as enabled.
I'm on Kinetic, not Jammy, so it won't be exactly the same, but it should look a bit like the screenshot.

---

### Post by #&amp;thj^% on 2023-01-10
> **BlueAZ said:**
> Well, that did add back a lot of stuff...   After rebooting there are loads of games I'm not interested in, etc.  But my desktop is still not as it was.  
First question:  what was it about that command that finally made something happen?  I'm pretty baffled by command syntax, other than the basics.

[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)
Your quoted as already had taskel installed, also using the command:
> 1fallen, I had already tried that. Tasksel is installed, is latest version. When I run sudo tasksel install ubuntu-desktop, there is a pause, then nothing,
I suggested possible corruption on the desktop. With that new taskel command used see this:
```
--new-install
    a**utomatically select some tasks without even displaying them to the user; default other tasks to on; used during new Debian installs**
```
more found in the man:
```
TASKSEL(8)                  Debian specific manpage                 TASKSEL(8)

NAME
       tasksel - a user interface for installing tasks

SYNOPSIS
       tasksel install <task>

       tasksel remove <task>

       tasksel [options]

DESCRIPTION
       tasksel shows all available tasks and allows selecting ones to install

OPTIONS
       -t, --test
           test mode; don't actually install or remove packages

       --new-install
           automatically select some tasks without even displaying them to the
           user; default other tasks to on; used during new Debian installs.

       --list-tasks
           list on stdout the tasks that would be displayed in the tasksel
           interface

       --task-packages task
           lists on stdout the packages that are available and part of the
           given task

           Note that this option may be given more than once.

       --task-desc task
           outputs the extended description of the given task

       --debconf-apt-progress options
           Pass the specified options to the debconf-apt-progress command that
           tasksel runs.

SEE ALSO
       dpkg(8), apt-get(8)

FILES
       /usr/share/tasksel/descs/*.desc and
       /usr/local/share/tasksel/descs/*.desc are used to define tasks.

AUTHOR
       tasksel was written by Randolph Chung <tausq@debian.org> and Joey Hess
       <joeyh@debian.org>

HISTORY
       This document first appeared with tasksel-1.0

3.71                              2023-01-03                        TASKSEL(8)

```
As far as using soft-ware updater, it should not have any bad results.
I have no answer for your desktop differences, mine are still intact as before.
I always have used or will use any command I suggest* for users, I'm the guppy first.
My removal was very clean as well (Not a Suggestion just saying it's safe when used proper)
**And just to be absolutely clear it will destroy your install, in the wrong hands.**
REMOVAL:
```
sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  bogofilter bogofilter-bdb bogofilter-common evince-common evolution-common
  gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0
  gir1.2-gnomebluetooth-3.0 gir1.2-graphene-1.0 gir1.2-gtk-4.0
  gir1.2-gweather-4.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-4.1
  gir1.2-nma-1.0 gir1.2-polkit-1.0 gir1.2-rsvg-2.0 gir1.2-soup-3.0
  gir1.2-upowerglib-1.0 gir1.2-webkit2-4.1 gjs gnome-control-center-data
  gnome-session-common gnome-settings-daemon-common gnome-shell-common
  gstreamer1.0-pipewire ibus ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 im-config
  libcmark0.30.2 libcolord-gtk4-1 libdee-1.0-4 libevdocument3-4 libevview3-3
  libfreerdp-server2-2 libgail-3-0 libgdm1 libgeoclue-2-0 libgjs0g
  libgnome-autoar-0-0 libgnome-autoar-gtk-0-0 libgnome-bluetooth-ui-3.0-13
  libgsl27 libgslcblas0 libgsound0 libibus-1.0-5 libmozjs-102-0
  libnss-myhostname libsnapd-glib-2-1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libxkbregistry0 libytnef0
  mutter-common power-profiles-daemon python3-ibus-1.0 realmd
  switcheroo-control xwayland
0 upgraded, 0 newly installed, 67 to remove and 0 not upgraded.
After this operation, 278 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 662026 files and directories currently installed.)
Removing bogofilter (1.2.5-1+b2) ...
Removing bogofilter-bdb (1.2.5-1+b2) ...
Removing bogofilter-common (1.2.5-1+b2) ...
Removing evince-common (43.1-2) ...
Removing evolution-common (3.46.3-1) ...
Removing gir1.2-accountsservice-1.0:amd64 (22.08.8-1+b1) ...
Removing gir1.2-adw-1:amd64 (1.2.1-1) ...
Removing gir1.2-gcr-3:amd64 (3.41.1-1+b1) ...
Removing gir1.2-gck-1:amd64 (3.41.1-1+b1) ...
Removing gir1.2-gdesktopenums-3.0:amd64 (43.0-1) ...
Removing gir1.2-gdm-1.0:amd64 (43.0-1) ...
Removing gir1.2-geoclue-2.0:amd64 (2.6.0-2) ...
Removing gir1.2-gnomebluetooth-3.0:amd64 (42.5-1) ...
Removing gir1.2-gtk-4.0:amd64 (4.8.3+ds-1) ...
Removing gir1.2-graphene-1.0:amd64 (1.10.8-1) ...
Removing gir1.2-gweather-4.0:amd64 (4.2.0-1) ...
Removing ibus (1.5.27-4) ...
Removing python3-ibus-1.0 (1.5.27-4) ...
Removing gir1.2-ibus-1.0:amd64 (1.5.27-4) ...
Removing gir1.2-webkit2-4.1:amd64 (2.38.3-1) ...
Removing gir1.2-javascriptcoregtk-4.1:amd64 (2.38.3-1) ...
Removing gir1.2-nma-1.0:amd64 (1.10.6-1) ...
Removing gir1.2-polkit-1.0 (122-1) ...
Removing gir1.2-rsvg-2.0:amd64 (2.54.5+dfsg-1) ...
Removing gir1.2-soup-3.0:amd64 (3.2.2-1) ...
Removing gir1.2-upowerglib-1.0:amd64 (0.99.20-2) ...
Removing gjs (1.74.1-1) ...
Removing gnome-control-center-data (1:43.2-1) ...
Removing gnome-session-common (43.0-1) ...
Removing gnome-settings-daemon-common (43.0-3) ...
Removing gnome-shell-common (43.1-2) ...
Removing gstreamer1.0-pipewire:amd64 (0.3.63-2) ...
Removing ibus-data (1.5.27-4) ...
Removing ibus-gtk:amd64 (1.5.27-4) ...
Removing ibus-gtk3:amd64 (1.5.27-4) ...
Removing ibus-gtk4:amd64 (1.5.27-4) ...
Removing im-config (0.54-1) ...
Removing libcmark0.30.2:amd64 (0.30.2-6) ...
Removing libcolord-gtk4-1:amd64 (0.3.0-3) ...
Removing libunity9:amd64 (7.1.4+19.04.20190319-6+b1) ...
Removing libunity-protocol-private0:amd64 (7.1.4+19.04.20190319-6+b1) ...
Removing libdee-1.0-4:amd64 (1.2.7+17.10.20170616-7+b2) ...
Removing libevview3-3:amd64 (43.1-2) ...
Removing libevdocument3-4:amd64 (43.1-2) ...
Removing libfreerdp-server2-2:amd64 (2.9.0+dfsg1-1) ...
Removing libgail-3-0:amd64 (3.24.36-1) ...
Removing libgdm1 (43.0-1) ...
Removing libgeoclue-2-0:amd64 (2.6.0-2) ...
Removing libgjs0g:amd64 (1.74.1-1) ...
Removing libgnome-autoar-gtk-0-0:amd64 (0.4.3-1) ...
Removing libgnome-autoar-0-0:amd64 (0.4.3-1) ...
Removing libgnome-bluetooth-ui-3.0-13:amd64 (42.5-1) ...
Removing libgsl27:amd64 (2.7.1+dfsg-3+b1) ...
Removing libgslcblas0:amd64 (2.7.1+dfsg-3+b1) ...
Removing libgsound0:amd64 (1.0.3-2) ...
Removing libibus-1.0-5:amd64 (1.5.27-4) ...
Removing libmozjs-102-0:amd64 (102.6.0-1) ...
Removing libnss-myhostname:amd64 (252.4-1) ...
Removing libsnapd-glib-2-1:amd64 (1.63-4) ...
Removing libunity-scopes-json-def-desktop (7.1.4+19.04.20190319-6) ...
Removing libxkbregistry0:amd64 (1.4.1-1) ...
Removing libytnef0:amd64 (2.0-1+b1) ...
Removing mutter-common (43.2-4) ...
Removing power-profiles-daemon (0.12-1+b1) ...
Removing realmd (0.17.1-1) ...
Removing switcheroo-control (2.6-1+b1) ...
Removing xwayland (2:22.1.6-1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1.1) ...
Processing triggers for libglib2.0-0:amd64 (2.74.4-1) ...
Processing triggers for libgtk-3-0:amd64 (3.24.36-1) ...
Processing triggers for libgtk2.0-0:amd64 (2.24.33-2) ...
Processing triggers for libc-bin (2.36-8) ...
Processing triggers for kaisen-menu (2.2+kaisen3) ...
Processing triggers for man-db (2.11.2-1) ...
Processing triggers for dbus (1.14.4-1) ...
Processing triggers for udev (252.4-1) ...
Processing triggers for libgtk-4-1:amd64 (4.8.3+ds-1) ...
Processing triggers for mailcap (3.70+nmu1) ...
Processing triggers for desktop-file-utils (0.26-1) ...


```
This is using a Debian Sid install so I got to think your desktop should surely be more stable than mine.

---

### Post by BlueAZ on 2023-01-10
Thanks 1fallen!  When I ran sudo apt autoremove just now, I got this:

The following packages will be REMOVED:
  gnome gnome-control-center gnome-core gnome-remote-desktop
  task-gnome-desktop
0 upgraded, 0 newly installed, 5 to remove and 17 not upgraded.
After this operation, 5,591 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 267882 files and directories currently installed.)
Removing gnome (1:42+3) ...
Removing task-gnome-desktop (3.68ubuntu2) ...
Removing gnome-core (1:42+3) ...
Removing gnome-control-center (1:41.7-0ubuntu0.22.04.5) ...
Removing gnome-remote-desktop (42.7-0ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.72.4-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.72.4-0ubuntu1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...

Then ran sudo apt install gnome-desktop and got this:

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package gnome-desktop

---

### Post by #&amp;thj^% on 2023-01-10
That's not what I wanted to see, it's almost a repeat from your original post#1
This is ok to just ignore "E: Could not find package gnome-desktop"
Mine:
```
sudo apt install gnome-desktop
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package gnome-desktop
```
I think oldfred pointed to it as well, it's just a meta-holder, and a mute issue.
can you show me this then:
```
sudo apt dist-upgrade -s

```
the "-s" flag is a dry run no changes will be made.

---

### Post by tea for one on 2023-01-10
> **BlueAZ said:**
> E: Unable to locate package gnome-desktop
The package is ubuntu-desktop rather than gnome-desktop.

Before you go any further, can you open a terminal and enter:-
```
apt policy ubuntu-desktop
```

Finally, have you installed alternative Desktop Environments i.e.Kubuntu, Xubuntu etc?
I ask because [COLOR="#0000FF"]apt autoremove[/COLOR] always seems to want to remove gnome packages and it leads me to think that you have more than one DE?

---

### Post by BlueAZ on 2023-01-10
This is what I got:

```
:~$ sudo apt dist-upgrade -s
[sudo] password for blue: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apache2-bin apg baobab bluez caribou five-or-more folks-common
  fonts-cantarell fonts-symbola four-in-a-row gedit gedit-common
  gir1.2-caribou-1.0 gir1.2-champlain-0.12 gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-dazzle-1.0 gir1.2-geocodeglib-1.0
  gir1.2-gfbgraph-0.2 gir1.2-grilo-0.3 gir1.2-gst-plugins-bad-1.0
  gir1.2-gtkchamplain-0.12 gir1.2-gtkclutter-1.0 gir1.2-mediaart-2.0
  gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-tracker-3.0 gnome-2048
  gnome-accessibility-themes gnome-bluetooth gnome-bluetooth-common
  gnome-calendar gnome-chess gnome-clocks gnome-color-manager gnome-contacts
  gnome-control-center-data gnome-control-center-faces gnome-disk-utility
  gnome-font-viewer gnome-games gnome-klotski gnome-logs gnome-maps
  gnome-music gnome-nibbles gnome-online-accounts gnome-online-miners
  gnome-robots gnome-sound-recorder gnome-sudoku gnome-system-monitor
  gnome-taquin gnome-tetravex gnome-themes-extra gnome-themes-extra-data
  gnome-todo gnome-todo-common gnome-user-share gnome-weather
  gstreamer1.0-packagekit gtk2-engines-pixbuf gvfs-fuse hitori hoichess iagno
  language-selector-common language-selector-gnome libapache2-mod-dnssd
  libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
  libcaribou-common libcaribou0 libcdr-0.1-1 libcolord-gtk1 libdazzle-1.0-0
  libdazzle-common libevent-2.1-7 libfolks-eds26 libfolks26 libfreehand-0.1-1
  libfreerdp-client2-2 libfreerdp-server2-2 libfreerdp2-2 libgfbgraph-0.2-0
  libgnome-bluetooth13 libgnome-todo libgoa-backend-1.0-1 libgpod-common
  libgpod4 libgsf-bin libgsound0 libminiupnpc17 libmspub-0.1-1 libnatpmp1
  libpagemaker-0.0-0 libpkcs11-helper1 libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libproxy1-plugin-webkit libqqwing2v5
  libreoffice-calc libreoffice-draw libreoffice-gnome libreoffice-gtk3
  libreoffice-impress librest-0.7-0 librhythmbox-core10 librygel-core-2.6-2
  librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-renderer-gst-2.6-2
  librygel-server-2.6-2 libsbc1 libsgutils2-2 libvisio-0.1-1 libvncserver1
  libwinpr2-2 libzapojit-0.0-0 lightsoff lp-solve media-player-info
  mobile-broadband-provider-info network-manager-gnome network-manager-openvpn
  network-manager-openvpn-gnome network-manager-pptp-gnome openvpn
  pulseaudio-module-bluetooth python3-macaroonbakery python3-mako python3-nacl
  python3-protobuf python3-pymacaroons python3-rfc3339 quadrapassel rhythmbox
  rhythmbox-data rhythmbox-plugin-alternative-toolbar
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rygel rygel-playbin
  rygel-tracker seahorse shotwell shotwell-common simple-scan swell-foop tali
  task-desktop transmission-common transmission-gtk x11-apps x11-session-utils
  xbitmaps xdg-user-dirs-gtk xinit xorg
Use 'sudo apt autoremove' to remove them.
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common libegl-mesa0 libgbm1
  libgbm1:i386 libgl1-mesa-dri libglapi-mesa libglapi-mesa:i386 libglx-mesa0
  libosmesa6 libosmesa6:i386 libxatracker2 mesa-va-drivers mesa-vdpau-drivers
  mesa-vulkan-drivers
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
```

---

### Post by #&amp;thj^% on 2023-01-10
I'll wait till you see tea for one's post above with results,
This is looking a bit nasty now...

---

### Post by BlueAZ on 2023-01-10
And this is what I got about desktop:

:~$ apt policy ubuntu-desktop
ubuntu-desktop:
  Installed: (none)
  Candidate: 1.481
  Version table:
     1.481 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages

Does that mean I can install it from there?  I don't understand how/why this was removed by Software Updater.  I haven't installed any other desktop.  I do have gnome extensions installed, but some elements of it seem to be missing now, like Desktop Icons NG or DING.  Those were shown before.  I tried to go to gnome extensions online and add back these things, but it just gives me error messages about some connectivity thing.  Sent me to Documentation, but I don't understand it.

---

### Post by BlueAZ on 2023-01-10
Ack!  Just went to [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)    I can see packages there, but I don't know what they are or what is safe to install now.

---

### Post by tea for one on 2023-01-10
The package ubuntu-desktop has this description in synaptic
```
This package depends on all of the packages in the Ubuntu desktop system
It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
```
If you are using Jammy 22.04 with gnome-shell, then it should be present in your system.
You can try and install it but there is no telling what will happen bearing in mind the current situation.

Priority number one is to back up your personal data. then a re-install is a good option.

---

### Post by #&amp;thj^% on 2023-01-10
Ok this makes no sense at all, this is just me making notes here to help others that may stumble on this thread...
You ran "tasksel install ubuntu-desktop" nothing from your prompt.
Next you ran "tasksel --new-install ubuntu-desktop" lot's of packages were installed, some not wanted.(That can be dealt with later)
And now it all wants to come un-done or nuked.
This is what I would like to follow, after I've tested my theory first...I'll be right back. So Hold Tight Please!

---

### Post by BlueAZ on 2023-01-10
That's what I was afraid of.  Makes me want to scream!  Right now I'm dealing with a new breast cancer diagnosis and just need my computer to work.  How can an update from Canonical cause this much havoc?
On the bright side, this is the only issue I've had with Ubuntu that hasn't been solved in this illustrious Forum.  I'm eternally grateful to you guys -- THANK YOU!!!!!
I will find time to back up.  I have the ISO on a flashdrive.

---

### Post by #&amp;thj^% on 2023-01-10
OK my friend here it is from APT only:
```
me@me-ThinkPad-X1-Carbon-7th:~$ sudo apt install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  aisleriot apg apport-gtk apt-config-icons-hidpi aptdaemon aptdaemon-data
  avahi-utils baobab branding-ubuntu brltty cheese cheese-common
  cracklib-runtime cups-pk-helper dconf-cli deja-dup duplicity eog
  espeak-ng-data evince evince-common evolution-data-server
  evolution-data-server-common file-roller firefox fonts-noto-color-emoji
  fprintd gamemode gamemode-daemon gcc-12-base:i386 gdb gdm3 geoclue-2.0
  gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomeautoar-0.1 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0
  gir1.2-gnomedesktop-4.0 gir1.2-graphene-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-4.0 gir1.2-gudev-1.0 gir1.2-gweather-4.0
  gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-4.0 gir1.2-javascriptcoregtk-4.1
  gir1.2-json-1.0 gir1.2-mutter-11 gir1.2-nma-1.0 gir1.2-peas-1.0
  gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rsvg-2.0 gir1.2-snapd-2
  gir1.2-soup-2.4 gir1.2-soup-3.0 gir1.2-totem-1.0 gir1.2-totemplparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-7.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.91
  gir1.2-webkit2-4.0 gir1.2-webkit2-4.1 gir1.2-wnck-3.0 gjs gkbd-capplet
  gnome-accessibility-themes gnome-bluetooth-3-common gnome-bluetooth-sendto
  gnome-calculator gnome-calendar gnome-characters gnome-control-center
  gnome-control-center-data gnome-control-center-faces gnome-desktop3-data
  gnome-disk-utility gnome-font-viewer gnome-initial-setup gnome-logs
  gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts
  gnome-power-manager gnome-remote-desktop gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-settings-daemon
  gnome-settings-daemon-common gnome-shell gnome-shell-common
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng
  gnome-shell-extension-ubuntu-dock gnome-startup-applications gnome-sudoku
  gnome-system-monitor gnome-terminal gnome-terminal-data gnome-text-editor
  gnome-user-docs gnome-video-effects grilo-plugins-0.3-base
  gsettings-ubuntu-schemas gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-gtk3 gstreamer1.0-packagekit gstreamer1.0-pipewire
  gstreamer1.0-plugins-base-apps guile-3.0-libs gvfs-backends gvfs-fuse ibus
  ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 ibus-table iio-sensor-proxy im-config
  krb5-locales language-selector-gnome ldap-utils libabw-0.1-1 libadwaita-1-0
  libao-common libao4 libatk-adaptor libavahi-ui-gtk3-0 libbabeltrace1
  libbasicobjects0 libboost-regex1.74.0 libbrlapi0.8 libburn4 libc-ares2
  libc6:i386 libc6-dbg libcamel-1.2-64 libcanberra-pulse libcap2:i386
  libcdr-0.1-1 libcheese-gtk25 libcheese8 libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango20 libcogl-path20 libcogl20 libcolamd2
  libcollection4 libcolord-gtk4-1 libcom-err2:i386 libcrack2 libcrypt1:i386
  libcue2 libdbus-1-3:i386 libdebuginfod-common libdebuginfod1 libdee-1.0-4
  libdhash1 libdmapsharing-3.0-2 libdotconf0 libe-book-0.1-1
  libebackend-1.2-11 libebook-1.2-21 libebook-contacts-1.2-4 libecal-2.0-2
  libedata-book-1.2-27 libedata-cal-2.0-2 libedataserver-1.2-27
  libedataserverui-1.2-4 libedataserverui4-1.0-0 libepubgen-0.1-1
  libespeak-ng1 libetonyek-0.1-1 libevdocument3-4 libevent-2.1-7a libevview3-3
  libexempi8 libexiv2-27 libfprint-2-2 libfprint-2-tod1 libfreehand-0.1-1
  libfreerdp-client2-2 libfreerdp-server2-2 libfreerdp2-2 libgamemode0
  libgamemode0:i386 libgamemodeauto0 libgamemodeauto0:i386 libgcc-s1:i386
  libgcrypt20:i386 libgdata-common libgdata22 libgdm1 libgeoclue-2-0
  libgeocode-glib-2-0 libgexiv2-2 libgjs0g libgnome-autoar-0-0 libgnome-bg-4-2
  libgnome-bluetooth-3.0-13 libgnome-bluetooth-ui-3.0-13 libgnome-desktop-3-20
  libgnome-desktop-4-2 libgnome-games-support-1-3
  libgnome-games-support-common libgnome-menu-3-0 libgnome-rr-4-2
  libgoa-backend-1.0-1 libgom-1.0-0 libgpg-error-l10n libgpg-error0:i386
  libgpod-common libgpod4 libgrilo-0.3-0 libgsf-1-114 libgsf-1-common
  libgsound0 libgssapi-krb5-2:i386 libgssdp-1.6-0 libgtksourceview-5-0
  libgtksourceview-5-common libgtop-2.0-11 libgtop2-common libgupnp-1.6-0
  libgupnp-av-1.0-3 libgupnp-dlna-2.0-4 libgweather-4-0 libgweather-4-common
  libgxps2 libibus-1.0-5 libidn2-0:i386 libimobiledevice6 libini-config5
  libinih1 libipa-hbac0 libipt2 libisoburn1 libisofs6
  libjavascriptcoregtk-4.0-18 libjavascriptcoregtk-5.0-0 libk5crypto3:i386
  libkeyutils1:i386 libkpathsea6 libkrb5-3:i386 libkrb5support0:i386
  liblz4-1:i386 liblzma5:i386 libmediaart-2.0-0 libmessaging-menu0
  libminiupnpc17 libmozjs-102-0 libmspub-0.1-1 libmutter-11-0 libmwaw-0.3-3
  libnatpmp1 libnautilus-extension4 libnfs13 libnfsidmap1 libnsl2:i386
  libnss-nis:i386 libnss-nisplus:i386 libnss-sss libodfgen-0.1-1
  libpagemaker-0.0-0 libpam-fprintd libpam-pwquality libpam-sss libpath-utils1
  libpcaudio0 libpcre2-32-0 libpeas-1.0-0 libpeas-common libphonenumber8
  libplist3 libportal-gtk3-1 libportal-gtk4-1 libportal1 libprotobuf23
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqqwing2v5 libraw20 libref-array1
  libreoffice-base-core libreoffice-calc libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-pdfimport
  libreoffice-style-breeze libreoffice-style-elementary libreoffice-style-yaru
  libreoffice-writer librest-1.0-0 librhythmbox-core10 librsync2
  librygel-core-2.8-0 librygel-db-2.8-0 librygel-renderer-2.8-0
  librygel-server-2.8-0 libsasl2-modules-gssapi-mit libsgutils2-2 libsonic0
  libsoup-gnome2.4-1 libsource-highlight-common libsource-highlight4v5
  libspectre1 libspeechd2 libssl3:i386 libsss-certmap0 libsss-idmap0
  libsss-nss-idmap0 libsuitesparseconfig5 libsynctex2 libsysmetrics1
  libsystemd0:i386 libtirpc3:i386 libtotem-plparser-common libtotem-plparser18
  libtotem0 libtracker-sparql-3.0-0 libtss2-rc0 libtss2-tctildr0
  libunistring2:i386 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libusbmuxd6 libvisio-0.1-1
  libvncclient1 libwebkit2gtk-4.0-37 libwebkit2gtk-5.0-0
  libwhoopsie-preferences0 libwhoopsie0 libwinpr2-2 libwmf-0.2-7
  libwmf-0.2-7-gtk libwmf0.2-7-gtk libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4
  libxcb-res0 libxcb-xv0 libxkbregistry0 libzstd1:i386 lp-solve
  media-player-info mousetweaks mutter-common nautilus nautilus-data
  nautilus-extension-gnome-terminal network-manager-config-connectivity-ubuntu
  network-manager-openvpn network-manager-openvpn-gnome orca
  plymouth-theme-spinner power-profiles-daemon python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-brlapi python3-cups
  python3-cupshelpers python3-debconf python3-defer python3-fasteners
  python3-future python3-ibus-1.0 python3-lockfile python3-louis python3-mako
  python3-markupsafe python3-monotonic python3-pyatspi python3-speechd
  python3-sss remmina remmina-common remmina-plugin-rdp remmina-plugin-secret
  remmina-plugin-vnc rhythmbox rhythmbox-data
  rhythmbox-plugin-alternative-toolbar rhythmbox-plugins rygel seahorse
  shotwell shotwell-common simple-scan snapd sound-icons speech-dispatcher
  speech-dispatcher-audio-plugins speech-dispatcher-espeak-ng squashfs-tools
  sssd sssd-ad sssd-ad-common sssd-common sssd-ipa sssd-krb5 sssd-krb5-common
  sssd-ldap sssd-proxy switcheroo-control system-config-printer
  system-config-printer-common system-config-printer-udev systemd-oomd
  thunderbird-gnome-support totem totem-common totem-plugins tracker
  tracker-extract tracker-miner-fs transmission-common transmission-gtk
  ubuntu-desktop-minimal ubuntu-docs ubuntu-release-upgrader-gtk ubuntu-report
  ubuntu-session ubuntu-settings ubuntu-wallpapers ubuntu-wallpapers-kinetic
  update-manager update-notifier update-notifier-common usb-creator-common
  usb-creator-gtk usbmuxd webp-pixbuf-loader whoopsie whoopsie-preferences
  xbrlapi xcursor-themes xdg-desktop-portal-gnome xorriso xserver-xephyr
  xwayland yaru-theme-gnome-shell yaru-theme-gtk yaru-theme-icon
  yaru-theme-sound zenity zenity-common
Suggested packages:
  gnome-cards-data brltty-speechd brltty-x11 console-braille unicode-cldr-core
  gnome-video-effects-frei0r python3-pydrive python3-boto ncftp lftp
  tahoe-lafs python3-swiftclient python3-pip par2 eog-plugins nautilus-sendto
  evolution arj lha ncompress rpm2cpio rzip sharutils unace unalz unar zoo
  gnome-shell-extension-gamemode gdb-doc gdbserver libpam-pkcs11
  gnome-software | gnome-packagekit gnome-user-share gstreamer1.0-pulseaudio
  realmd usbguard gir1.2-malcontent-0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gnome-backgrounds gnome-shell-extension-prefs
  chrome-gnome-shell gnome-video-effects-extra grilo-plugins-0.3-extra
  samba-common ibus-clutter ibus-doc ibus-table-array30 ibus-table-cangjie
  ibus-table-cangjie-big ibus-table-cangjie3 ibus-table-cangjie5
  ibus-table-cantonese ibus-table-cantonhk ibus-table-cns11643
  ibus-table-compose ibus-table-easy ibus-table-easy-big ibus-table-emoji
  ibus-table-erbi ibus-table-erbi-qs ibus-table-ipa-x-sampa
  ibus-table-jyutping ibus-table-latex ibus-table-quick
  ibus-table-quick-classic ibus-table-quick3 ibus-table-quick5
  ibus-table-rustrad ibus-table-scj6 ibus-table-stroke5 ibus-table-thai
  ibus-table-translit ibus-table-translit-ua ibus-table-viqr ibus-table-wu
  ibus-table-wubi ibus-table-yawerty ibus-table-yong libsndio6.1
  glibc-doc:i386 locales:i386 exiv2 freerdp2-x11 rng-tools:i386
  grilo-plugins-0.3 krb5-doc:i386 krb5-user:i386 libusbmuxd-tools minissdpd
  natpmpc libreoffice-base libreoffice-evolution libreofficekit-data
  breeze-icon-theme fonts-crosextra-caladea fonts-crosextra-carlito
  libreoffice-java-common default-jre | java-runtime | java8-runtime | jre
  sg3-utils unity-common gstreamer1.0-plugins-bad gnome-sushi
  nautilus-extension-brasero python-future-doc python-lockfile-doc
  python-mako-doc python3-beaker remmina-plugin-exec remmina-plugin-kwallet
  remmina-plugin-python remmina-plugin-www remmina-plugin-x2go
  gnome-codec-install rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist
  rygel-playbin rygel-preferences rygel-ruih rygel-tracker tumbler
  libttspico-utils espeak mbrola speech-dispatcher-doc-cs
  speech-dispatcher-festival speech-dispatcher-cicero speech-dispatcher-flite
  speech-dispatcher-espeak adcli libsss-sudo sssd-tools libsasl2-modules-ldap
  gnome-software python3-smbc ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid
  ubuntu-wallpapers-maverick ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric
  ubuntu-wallpapers-precise ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
  ubuntu-wallpapers-saucy ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic
  ubuntu-wallpapers-vivid ubuntu-wallpapers-wily ubuntu-wallpapers-xenial
  ubuntu-wallpapers-yakkety ubuntu-wallpapers-zesty ubuntu-wallpapers-artful
  ubuntu-wallpapers-bionic ubuntu-wallpapers-cosmic ubuntu-wallpapers-disco
  ubuntu-wallpapers-eoan ubuntu-wallpapers-focal ubuntu-wallpapers-groovy
  ubuntu-wallpapers-hirsute ubuntu-wallpapers-impish ubuntu-wallpapers-jammy
  xorriso-tcltk cdck
The following NEW packages will be installed:
  aisleriot apg apport-gtk apt-config-icons-hidpi aptdaemon aptdaemon-data
  avahi-utils baobab branding-ubuntu brltty cheese cheese-common
  cracklib-runtime cups-pk-helper dconf-cli deja-dup duplicity eog
  espeak-ng-data evince evince-common evolution-data-server
  evolution-data-server-common file-roller firefox fonts-noto-color-emoji
  fprintd gamemode gamemode-daemon gcc-12-base:i386 gdb gdm3 geoclue-2.0
  gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomeautoar-0.1 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0
  gir1.2-gnomedesktop-4.0 gir1.2-graphene-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-4.0 gir1.2-gudev-1.0 gir1.2-gweather-4.0
  gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-4.0 gir1.2-javascriptcoregtk-4.1
  gir1.2-json-1.0 gir1.2-mutter-11 gir1.2-nma-1.0 gir1.2-peas-1.0
  gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rsvg-2.0 gir1.2-snapd-2
  gir1.2-soup-2.4 gir1.2-soup-3.0 gir1.2-totem-1.0 gir1.2-totemplparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-7.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.91
  gir1.2-webkit2-4.0 gir1.2-webkit2-4.1 gir1.2-wnck-3.0 gjs gkbd-capplet
  gnome-accessibility-themes gnome-bluetooth-3-common gnome-bluetooth-sendto
  gnome-calculator gnome-calendar gnome-characters gnome-control-center
  gnome-control-center-data gnome-control-center-faces gnome-desktop3-data
  gnome-disk-utility gnome-font-viewer gnome-initial-setup gnome-logs
  gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts
  gnome-power-manager gnome-remote-desktop gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-settings-daemon
  gnome-settings-daemon-common gnome-shell gnome-shell-common
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng
  gnome-shell-extension-ubuntu-dock gnome-startup-applications gnome-sudoku
  gnome-system-monitor gnome-terminal gnome-terminal-data gnome-text-editor
  gnome-user-docs gnome-video-effects grilo-plugins-0.3-base
  gsettings-ubuntu-schemas gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-gtk3 gstreamer1.0-packagekit gstreamer1.0-pipewire
  gstreamer1.0-plugins-base-apps guile-3.0-libs gvfs-backends gvfs-fuse ibus
  ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 ibus-table iio-sensor-proxy im-config
  krb5-locales language-selector-gnome ldap-utils libabw-0.1-1 libadwaita-1-0
  libao-common libao4 libatk-adaptor libavahi-ui-gtk3-0 libbabeltrace1
  libbasicobjects0 libboost-regex1.74.0 libbrlapi0.8 libburn4 libc-ares2
  libc6:i386 libc6-dbg libcamel-1.2-64 libcanberra-pulse libcap2:i386
  libcdr-0.1-1 libcheese-gtk25 libcheese8 libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango20 libcogl-path20 libcogl20 libcolamd2
  libcollection4 libcolord-gtk4-1 libcom-err2:i386 libcrack2 libcrypt1:i386
  libcue2 libdbus-1-3:i386 libdebuginfod-common libdebuginfod1 libdee-1.0-4
  libdhash1 libdmapsharing-3.0-2 libdotconf0 libe-book-0.1-1
  libebackend-1.2-11 libebook-1.2-21 libebook-contacts-1.2-4 libecal-2.0-2
  libedata-book-1.2-27 libedata-cal-2.0-2 libedataserver-1.2-27
  libedataserverui-1.2-4 libedataserverui4-1.0-0 libepubgen-0.1-1
  libespeak-ng1 libetonyek-0.1-1 libevdocument3-4 libevent-2.1-7a libevview3-3
  libexempi8 libexiv2-27 libfprint-2-2 libfprint-2-tod1 libfreehand-0.1-1
  libfreerdp-client2-2 libfreerdp-server2-2 libfreerdp2-2 libgamemode0
  libgamemode0:i386 libgamemodeauto0 libgamemodeauto0:i386 libgcc-s1:i386
  libgcrypt20:i386 libgdata-common libgdata22 libgdm1 libgeoclue-2-0
  libgeocode-glib-2-0 libgexiv2-2 libgjs0g libgnome-autoar-0-0 libgnome-bg-4-2
  libgnome-bluetooth-3.0-13 libgnome-bluetooth-ui-3.0-13 libgnome-desktop-3-20
  libgnome-desktop-4-2 libgnome-games-support-1-3
  libgnome-games-support-common libgnome-menu-3-0 libgnome-rr-4-2
  libgoa-backend-1.0-1 libgom-1.0-0 libgpg-error-l10n libgpg-error0:i386
  libgpod-common libgpod4 libgrilo-0.3-0 libgsf-1-114 libgsf-1-common
  libgsound0 libgssapi-krb5-2:i386 libgssdp-1.6-0 libgtksourceview-5-0
  libgtksourceview-5-common libgtop-2.0-11 libgtop2-common libgupnp-1.6-0
  libgupnp-av-1.0-3 libgupnp-dlna-2.0-4 libgweather-4-0 libgweather-4-common
  libgxps2 libibus-1.0-5 libidn2-0:i386 libimobiledevice6 libini-config5
  libinih1 libipa-hbac0 libipt2 libisoburn1 libisofs6
  libjavascriptcoregtk-4.0-18 libjavascriptcoregtk-5.0-0 libk5crypto3:i386
  libkeyutils1:i386 libkpathsea6 libkrb5-3:i386 libkrb5support0:i386
  liblz4-1:i386 liblzma5:i386 libmediaart-2.0-0 libmessaging-menu0
  libminiupnpc17 libmozjs-102-0 libmspub-0.1-1 libmutter-11-0 libmwaw-0.3-3
  libnatpmp1 libnautilus-extension4 libnfs13 libnfsidmap1 libnsl2:i386
  libnss-nis:i386 libnss-nisplus:i386 libnss-sss libodfgen-0.1-1
  libpagemaker-0.0-0 libpam-fprintd libpam-pwquality libpam-sss libpath-utils1
  libpcaudio0 libpcre2-32-0 libpeas-1.0-0 libpeas-common libphonenumber8
  libplist3 libportal-gtk3-1 libportal-gtk4-1 libportal1 libprotobuf23
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqqwing2v5 libraw20 libref-array1
  libreoffice-base-core libreoffice-calc libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-pdfimport
  libreoffice-style-breeze libreoffice-style-elementary libreoffice-style-yaru
  libreoffice-writer librest-1.0-0 librhythmbox-core10 librsync2
  librygel-core-2.8-0 librygel-db-2.8-0 librygel-renderer-2.8-0
  librygel-server-2.8-0 libsasl2-modules-gssapi-mit libsgutils2-2 libsonic0
  libsoup-gnome2.4-1 libsource-highlight-common libsource-highlight4v5
  libspectre1 libspeechd2 libssl3:i386 libsss-certmap0 libsss-idmap0
  libsss-nss-idmap0 libsuitesparseconfig5 libsynctex2 libsysmetrics1
  libsystemd0:i386 libtirpc3:i386 libtotem-plparser-common libtotem-plparser18
  libtotem0 libtracker-sparql-3.0-0 libtss2-rc0 libtss2-tctildr0
  libunistring2:i386 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libusbmuxd6 libvisio-0.1-1
  libvncclient1 libwebkit2gtk-4.0-37 libwebkit2gtk-5.0-0
  libwhoopsie-preferences0 libwhoopsie0 libwinpr2-2 libwmf-0.2-7
  libwmf-0.2-7-gtk libwmf0.2-7-gtk libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4
  libxcb-res0 libxcb-xv0 libxkbregistry0 libzstd1:i386 lp-solve
  media-player-info mousetweaks mutter-common nautilus nautilus-data
  nautilus-extension-gnome-terminal network-manager-config-connectivity-ubuntu
  network-manager-openvpn network-manager-openvpn-gnome orca
  plymouth-theme-spinner power-profiles-daemon python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-brlapi python3-cups
  python3-cupshelpers python3-debconf python3-defer python3-fasteners
  python3-future python3-ibus-1.0 python3-lockfile python3-louis python3-mako
  python3-markupsafe python3-monotonic python3-pyatspi python3-speechd
  python3-sss remmina remmina-common remmina-plugin-rdp remmina-plugin-secret
  remmina-plugin-vnc rhythmbox rhythmbox-data
  rhythmbox-plugin-alternative-toolbar rhythmbox-plugins rygel seahorse
  shotwell shotwell-common simple-scan snapd sound-icons speech-dispatcher
  speech-dispatcher-audio-plugins speech-dispatcher-espeak-ng squashfs-tools
  sssd sssd-ad sssd-ad-common sssd-common sssd-ipa sssd-krb5 sssd-krb5-common
  sssd-ldap sssd-proxy switcheroo-control system-config-printer
  system-config-printer-common system-config-printer-udev systemd-oomd
  thunderbird-gnome-support totem totem-common totem-plugins tracker
  tracker-extract tracker-miner-fs transmission-common transmission-gtk
  ubuntu-desktop ubuntu-desktop-minimal ubuntu-docs
  ubuntu-release-upgrader-gtk ubuntu-report ubuntu-session ubuntu-settings
  ubuntu-wallpapers ubuntu-wallpapers-kinetic update-manager update-notifier
  update-notifier-common usb-creator-common usb-creator-gtk usbmuxd
  webp-pixbuf-loader whoopsie whoopsie-preferences xbrlapi xcursor-themes
  xdg-desktop-portal-gnome xorriso xserver-xephyr xwayland
  yaru-theme-gnome-shell yaru-theme-gtk yaru-theme-icon yaru-theme-sound
  zenity zenity-common
0 upgraded, 473 newly installed, 0 to remove and 0 not upgraded.
Need to get 307 MB of archives.
After this operation, 1,179 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
This a virgin Ubuntu Desktop with all packages, Results in just a minute.
I have XFCE4 and now Gnome.

---

### Post by deadflowr on 2023-01-10
Try
```
sudo apt install --no-install-recommends ubuntu-desktop^
```

---

### Post by BlueAZ on 2023-01-10
1fallen, WOW!  I just tried 
sudo apt install ubuntu-desktop

and got a huge list of things downloaded, installed and set up.  However, my desktop still looks the same.  Oh, I probably need to reboot.  I'll do that.

---

### Post by #&amp;thj^% on 2023-01-10
Hoping for the best,  all good here:
```
me@me-ThinkPad-X1-Carbon-7th:~$ apt policy ubuntu-desktop
ubuntu-desktop:
  Installed: 1.497
  Candidate: 1.497
  Version table:
 *** 1.497 1001
       1001 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```
Once again I'm using Lunar sources here:
```
sudo apt dist-upgrade -s
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by BlueAZ on 2023-01-10
YES!!  After reboot, my desktop is BACK!!!  And I got this:

:~$ apt policy ubuntu-desktop
ubuntu-desktop:
  Installed: 1.481
  Candidate: 1.481
  Version table:
 *** 1.481 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status

I'm tempted to mark this thread 'SOLVED', but I'm not sure what thing(s) actually worked.  It may be relevant that I had gnome extensions installed and just removed it all before trying sudo apt install ubuntu-desktop again.  Now that I have my desktop back, I'm not sure if gnome-extensions was causing the problem all along...  I miss some of its features, but am afraid to install it again.

---

### Post by #&amp;thj^% on 2023-01-10
Well from my view tasksel did not  serve you well at one point.
APT seemed to jump in and handle things nicely for you.
Yep wait a day or two and see if we get any more bad results.
Just update and upgrade the way your accustom to.

---

### Post by tea for one on 2023-01-10
Good progress so far, methinks..........
> **BlueAZ said:**
>  It may be relevant that I had gnome extensions installed and just removed it all before trying sudo apt install ubuntu-desktop again.  Now that I have my desktop back, I'm not sure if gnome-extensions was causing the problem all along...  I miss some of its features, but am afraid to install it again.
Can you open a terminal again and enter:-
```
apt policy gnome-shell-extension-manager
```
Is it installed?
This package should help with the settings of the extension Desktop Icons NG (Ding).

---

### Post by BlueAZ on 2023-01-10
Hi tea for one,    This is what I got:

:~$ apt policy gnome-shell-extension-manager
gnome-shell-extension-manager:
  Installed: 0.3.0-0ubuntu2.1
  Candidate: 0.3.0-0ubuntu2.1
  Version table:
 *** 0.3.0-0ubuntu2.1 500

So that is installed, but I'm still leery of reinstalling gnome extensions...

---

### Post by tea for one on 2023-01-10
> **BlueAZ said:**
> So that is installed, but I'm still leery of reinstalling gnome extensions...
I understand your apprehension after all that has happened.
As the package is in your system, have a look at the settings for Desktop Icons NG (Ding).
Maybe, a pleasant surprise awaits..............;)

---

### Post by #&amp;thj^% on 2023-01-10
EDIT: ninja'd by tea for one ;)
You can't second guess your install or else where's the fun?
```
>> apt policy gnome-shell-extensions
gnome-shell-extensions:
  Installed: (none)
  Candidate: 43.1-1
  Version table:
     43.1-1 100
        100 http://ftp.us.debian.org/debian sid/main amd64 Packages


me on Tue Jan 10 at 03:27 PM in ~ branch: (HEAD) 
>> apt policy gnome-shell-extension-manager
gnome-shell-extension-manager:
  Installed: (none)
  Candidate: 0.2.3-2
  Version table:
     0.2.3-2 100
        100 http://ftp.us.debian.org/debian sid/main amd64 Packages

```
Might be a test early on the integrity of your install.

---

### Post by BlueAZ on 2023-01-10
OK, I did it!  Enabled gnome extensions again, and the sky did not fall!  Everything seems to be working as it did before the evil update!
Thank you so much for your caring and dedicated help!

---

### Post by #&amp;thj^% on 2023-01-10
> **BlueAZ said:**
> 
Thank you so much for your caring and dedicated help!
That makes it all worth while. :)

---

