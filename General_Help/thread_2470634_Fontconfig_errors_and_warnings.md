---
title: "Fontconfig errors and warnings"
date: 2022-01-06
forum: General Help
---

### Post by julian-g71 on 2022-01-06
Hi - I'm hoping that someone can help me with the following issue that seems to have appeared on systems I have running Ubuntu 20.04.3 LTS.

System Details:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.3 LTS"

uname -rv
5.4.0-91-generic #102-Ubuntu SMP Fri Nov 5 16:31:28 UTC 2021

dpkg -l |grep -s -i fontconfig
ii  fontconfig                          2.13.1-2ubuntu3        amd64     generic font configuration library - support binaries
ii  fontconfig-config                 2.13.1-2ubuntu3        all          generic font configuration library - configuration
ii  libfontconfig1:amd64            2.13.1-2ubuntu3        amd64     generic font configuration library - runtime

snap list chromium
Name      Version        Rev   Tracking       Publisher   Notes
chromium  96.0.4664.110  1854  latest/stable  canonical&#10003;  -

This seems to be something to do with either fontconfig or snap chromium or a combination of the two and attempts to fix this have failed so far.

Upon launching chromium from the command line I get these errors & warnings although chromium does launch and seems fine. Up until about a month ago this didn't happen at all. So the only changes will have been O/S and snap updates applied.

Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/30-metric-aliases.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/30-metric-aliases.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/30-metric-aliases.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/30-metric-aliases.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/40-nonlatin.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/40-nonlatin.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/40-nonlatin.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/40-nonlatin.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/45-generic.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/45-generic.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/45-generic.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/45-generic.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/45-latin.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/45-latin.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/45-latin.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/45-latin.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/49-sansserif.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/49-sansserif.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/49-sansserif.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/49-sansserif.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/50-user.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/50-user.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/50-user.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/50-user.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/51-local.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/51-local.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/51-local.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/51-local.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/60-generic.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/60-generic.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/60-generic.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/60-generic.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/60-latin.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/60-latin.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/60-latin.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/60-latin.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/65-fonts-persian.conf", line 34: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/65-fonts-persian.conf", line 35: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/65-fonts-persian.conf", line 35: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/65-fonts-persian.conf", line 35: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/65-fonts-persian.conf", line 36: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/65-fonts-persian.conf", line 36: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/65-nonlatin.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/65-nonlatin.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/65-nonlatin.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/65-nonlatin.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/69-unifont.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/69-unifont.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/69-unifont.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/69-unifont.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/69-unifont.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/69-unifont.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/80-delicious.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/80-delicious.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/80-delicious.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/80-delicious.conf", line 6: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/conf.d/90-synthetic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/90-synthetic.conf", line 5: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/conf.d/90-synthetic.conf", line 5: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/conf.d/90-synthetic.conf", line 5: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/conf.d/90-synthetic.conf", line 6: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/conf.d/90-synthetic.conf", line 6: invalid attribute 'version'

Both fontconfig-config & fontconfig are Version: 2.13.1-2ubuntu3 which is the latest.
And snap chromium is 96.0.4664.110 latest/stable

I've not been able to find any information out about this particular scenario but have read many threads about fontconfig and possible fixes including re-installing fontconfig or moving the users fontconfig out of the way and running fc-cache to regenerate. But this hasn't worked at all.

I also note that the conf files all listed above are part of fontconfig-config, as running dpkg -S <filename.conf> shows me this.

I did want to try and downgrade chromium but this doesn't seem to be an option? You can either have the stable or beta/edge versions - which I have tried and the problem is still present.

Any help or advice would be greatly appreciated. Thanks.

---

### Post by schragge on 2022-01-06
Looks like either chromium cannot access **/usr/share/xml/fontconfig/fonts.dtd** or the file is corrupt.
In the former case, try
```
snap connect chromium:browser-sandbox :browser-support
```
This is a shot in the dark: I don't use snapped Chromium, and don't know what snap plugs it provides. Check it with [FONT=monospace]**snap interface**[/FONT] and [FONT=monospace]**snap connections chromium**[/FONT]

In the latter
```
sudo apt reinstall fontconfig-config
```

---

### Post by julian-g71 on 2022-01-06
Thank you, I have tried both suggested fixes and the problem remains unfortunately.

---

### Post by schragge on 2022-01-06
Please provide the output of
```
snap connections chromium
```

---

### Post by julian-g71 on 2022-01-06
Hi, here's the output as requested.

```
snap connections chromium
Interface                 Plug                                    Slot                             Notes
audio-playback            chromium:audio-playback                 :audio-playback                  -
audio-record              chromium:audio-record                   :audio-record                    -
bluez                     chromium:bluez                          :bluez                           -
browser-support           chromium:browser-sandbox                :browser-support                 -
camera                    chromium:camera                         :camera                          -
content[gnome-3-28-1804]  chromium:gnome-3-28-1804                gnome-3-28-1804:gnome-3-28-1804  -
content[gtk-3-themes]     chromium:gtk-3-themes                   gtk-common-themes:gtk-3-themes   -
content[icon-themes]      chromium:icon-themes                    gtk-common-themes:icon-themes    -
content[sound-themes]     chromium:sound-themes                   gtk-common-themes:sound-themes   -
cups-control              chromium:cups-control                   :cups-control                    -
desktop                   chromium:desktop                        :desktop                         -
desktop-legacy            chromium:desktop-legacy                 :desktop-legacy                  -
gsettings                 chromium:gsettings                      :gsettings                       -
home                      chromium:home                           :home                            -
joystick                  chromium:joystick                       :joystick                        -
mount-observe             chromium:mount-observe                  -                                -
mpris                     -                                       chromium:mpris                   -
network                   chromium:network                        :network                         -
network-bind              chromium:network-bind                   :network-bind                    -
network-manager           chromium:network-manager                -                                -
opengl                    chromium:opengl                         :opengl                          -
password-manager-service  chromium:password-manager-service       -                                -
personal-files            chromium:chromium-config                :personal-files                  -
pulseaudio                chromium:pulseaudio                     -                                -
raw-usb                   chromium:raw-usb                        -                                -
removable-media           chromium:removable-media                :removable-media                 -
screen-inhibit-control    chromium:screen-inhibit-control         :screen-inhibit-control          -
system-files              chromium:etc-chromium-browser-policies  :system-files                    -
system-packages-doc       chromium:system-packages-doc            :system-packages-doc             -
u2f-devices               chromium:u2f-devices                    :u2f-devices                     -
unity7                    chromium:unity7                         :unity7                          -
upower-observe            chromium:upower-observe                 :upower-observe                  -
wayland                   chromium:wayland                        :wayland                         -
x11                       chromium:x11                            :x11                             -
```

---

