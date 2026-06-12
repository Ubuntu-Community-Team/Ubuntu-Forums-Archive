---
title: "some battery icons are wrong in xfce4-power-manager 1.0.11"
date: 2014-02-20
forum: General Help
---

### Post by Ertxiem on 2014-02-20
I'm using xfce4-power-manager 1.0.11 in lubuntu 12.04 to display the battery status.
As far as I could understand, the icons displayed in my laptop are from:
```
/usr/share/icons/elementary/panel/48
```
because I'm using the lubuntu icons theme that picks up the elementary theme when needed.
However, when the battery is low, 4 icons appear to be from a different theme.

I'm trying to solve this for a couple of days and it may be related to missing files, but I'm not sure.

The images missing correspond to file names that end with 
000.svg
020.svg
000-charging.svg
000-charging.svg

(or the "caution" and "low" that correspond to 000 and 020, respectively).

I thought it could be due to some non existent file, so I tried to create some symbolic links to the file names that I thought it would be likely to be existing, but without success.

In attachment I've included the Battery-060.png that is the "correct" image, according to the theme I selected and the Battery-020-wrong.png that is one of the "incorrect" images I get.

If I knew what files xfce4-power-manager is looking for I could do more symbolic links to solve this.

---

### Post by Toz on 2014-02-20
> **Ertxiem said:**
> 
If I knew what files xfce4-power-manager is looking for I could do more symbolic links to solve this.
It should be using the xfpm-battery-* files. If its an svg-based scalable icon theme, then the files will have .svg extensions. Otherwise, they are probably .png. I don't have the elementary icon theme on my system, but the elementary-xfce icon theme uses .png files (for these status icons).

---

### Post by Ertxiem on 2014-02-20
Thanks for the quick reply Toz.

I'm afraid I don't have xfpm-battery-* files in [I]/usr/share/icons/elementary/panel/48[I].

The only files starting with [I]xfpm[I] I have are:
```

28 Apr 11  2013 xfpm-primary-000-charging.svg -> gpm-primary-000-charging.svg
19 Apr 11  2013 xfpm-primary-000.svg -> gpm-battery-000.svg
28 Apr 11  2013 xfpm-primary-020-charging.svg -> gpm-primary-020-charging.svg
19 Apr 11  2013 xfpm-primary-020.svg -> gpm-primary-020.svg
28 Apr 11  2013 xfpm-primary-040-charging.svg -> gpm-primary-040-charging.svg
19 Apr 11  2013 xfpm-primary-040.svg -> gpm-primary-040.svg
28 Apr 11  2013 xfpm-primary-060-charging.svg -> gpm-primary-060-charging.svg
19 Apr 11  2013 xfpm-primary-060.svg -> gpm-primary-060.svg
28 Apr 11  2013 xfpm-primary-080-charging.svg -> gpm-primary-080-charging.svg
19 Apr 11  2013 xfpm-primary-080.svg -> gpm-primary-080.svg
28 Apr 11  2013 xfpm-primary-100-charging.svg -> gpm-primary-100-charging.svg
19 Apr 11  2013 xfpm-primary-100.svg -> gpm-primary-100.svg
23 Feb 20 03:44 xfpm-primary-caution.svg -> gpm-battery-caution.svg
23 Apr 11  2013 xfpm-primary-charged.svg -> gpm-battery-charged.svg
32 Feb 20 03:43 xfpm-primary-charging-caution.svg -> gpm-battery-charging-caution.svg
28 Feb 20 03:43 xfpm-primary-charging-low.svg -> gpm-battery-charging-low.svg
19 Feb 20 03:43 xfpm-primary-low.svg -> gpm-battery-low.svg
19 Apr 11  2013 xfpm-primary-missing.svg -> gpm-battery-000.svg
28 Apr 11  2013 xfpm-ups-000-charging.svg -> gpm-battery-000-charging.svg
19 Apr 11  2013 xfpm-ups-000.svg -> gpm-battery-000.svg
28 Apr 11  2013 xfpm-ups-020-charging.svg -> gpm-battery-020-charging.svg
19 Apr 11  2013 xfpm-ups-020.svg -> gpm-battery-020.svg
28 Apr 11  2013 xfpm-ups-040-charging.svg -> gpm-battery-040-charging.svg
19 Apr 11  2013 xfpm-ups-040.svg -> gpm-battery-040.svg
28 Apr 11  2013 xfpm-ups-060-charging.svg -> gpm-battery-060-charging.svg
19 Apr 11  2013 xfpm-ups-060.svg -> gpm-battery-060.svg
28 Apr 11  2013 xfpm-ups-080-charging.svg -> gpm-battery-080-charging.svg
19 Apr 11  2013 xfpm-ups-080.svg -> gpm-battery-080.svg
28 Apr 11  2013 xfpm-ups-100-charging.svg -> gpm-battery-100-charging.svg
19 Apr 11  2013 xfpm-ups-100.svg -> gpm-battery-100.svg
23 Apr 11  2013 xfpm-ups-charged.svg -> gpm-battery-charged.svg
23 Apr 11  2013 xfpm-ups-missing.svg -> gpm-battery-missing.svg

```
The links xfpm-primary-*words* were created by me to see if I could solve this issue.

---

### Post by Toz on 2014-02-20
A few questions:
1. Can you post the icon theme's index.theme file? (should be the /usr/share/icons/elementary/index.theme)
2. What size (height) is your panel?
3. Are you using xfce4-panel or another panel?

---

### Post by Toz on 2014-02-20
Sorry, my bad. Just double-checking and the files are xfpm-primary-* (not xfpm-battery).

EDIT: try this:
```
find /usr/share/icons/elementary -name xfpm-primary* -print
```
...and notice that the 24 panel size has only 000, 020, and 040 icons. I wonder whether depending on your panel size, since it can't find the correct icon in the 24 folder, its using the icon in the 48 folder, but when it comes to an icon that exists in thr 24 folder, it uses that.

---

### Post by Ertxiem on 2014-02-20
Edit: 
I missed that 24 folder. You seem to be right. My icons were set at size 24, so that is the folder to start with.
That explains it, although it's weird why the other files aren't there.
Anyway, I made some new symbolic links and problem solved.
Thanks a lot for your help.

-----


Starting with the 2nd and 3rd questions, I'm using LXPanel 0.5.8.
It's on the vertical, but the icon height is set at 24 pixels.

And now the 1st question, I'm using the lubuntu icon theme.
It's index.theme contains:
```

[Icon Theme]
Name=lubuntu
Comment=lubuntu icon theme, derivated from elementary
Inherits=elementary

Example=directory-x-normal

#Directory list
Directories=places/22,places/24,places/48,places/64,places/128,apps/16,apps/48,

[places/22]
Size=22
Context=Places
Type=Scalable

[places/24]
Size=24
Context=Places
Type=Scalable

[places/48]
Size=48
Context=Places
Type=Scalable

[places/64]
Size=64
Context=Places
Type=Scalable

[places/128]
Size=128
Context=Places
Type=Scalable

[apps/16]
Size=16
Context=Applications
Type=Scalable

[apps/48]
Size=48
Context=Applications
Type=Scalable

```


The elementary index.theme contains:
```

[Icon Theme]
Name=elementary
Comment=Smooth modern theme designed to be intuitive.
Inherits=gnome,hicolor

Example=directory-x-normal

#Directory list
Directories=actions/16,actions/22,actions/24,actions/32,actions/48,actions/64,actions/128,animations/16,animations/22,animations/24,animations/32,animations/48,animations/64,animations/128,apps/16,apps/22,apps/24,apps/32,apps/48,apps/64,apps/128,categories/16,categories/24,categories/32,categories/48,categories/64,categories/128,places/16,places/22,places/24,places/32,places/48,places/64,places/128,mimes/16,mimes/24,mimes/32,mimes/48,mimes/128,devices/16,devices/22,devices/24,devices/32,devices/48,devices/64,devices/128,emblems/16,emblems/22,emblems/24,emblems/32,emblems/48,emblems/64,emblems/128,status/16,status/22,status/24,status/32,status/48,status/64,status/128,notifications/16,notifications/22,notifications/24,notifications/32,notifications/48,panel/16,panel/22,panel/24,panel/48,stock/16,stock/22,stock/24,stock/32,stock/48,tools/22,

[actions/16]
Size=16
Context=Actions
Type=Fixed

[actions/22]
Size=22
Context=Actions
Type=Fixed

[actions/24]
Size=24
Context=Actions
Type=Fixed

[actions/32]
Size=32
Context=Actions
Type=Fixed

[actions/48]
Size=48
Context=Actions
Type=Scalable

[actions/64]
Size=64
Context=Actions
Type=Scalable

[actions/128]
Size=128
Context=Actions
Type=Scalable

[animations/16]
Size=16
Context=Animations
Type=Fixed

[animations/22]
Size=22
Context=Animations
Type=Fixed

[animations/24]
Size=24
Context=Animations
Type=Fixed

[animations/32]
Size=32
Context=Animations
Type=Fixed

[animations/48]
Size=48
Context=Animations
Type=Scalable

[animations/64]
Size=64
Context=Animations
Type=Scalable

[animations/128]
Size=128
Context=Animations
Type=Scalable

[apps/16]
Size=16
Context=Applications
Type=Fixed

[apps/22]
Size=22
Context=Applications
Type=Fixed

[apps/24]
Size=24
Context=Applications
Type=Fixed

[apps/32]
Size=32
Context=Applications
Type=Fixed

[apps/48]
Size=48
Context=Applications
Type=Scalable

[apps/64]
Size=64
Context=Applications
Type=Scalable

[apps/128]
Size=128
Context=Applications
Type=Scalable

[categories/16]
Size=16
Context=Categories
Type=Fixed

[categories/22]
Size=22
Context=Categories
Type=Fixed

[categories/24]
Size=24
Context=Categories
Type=Fixed

[categories/32]
Size=32
Context=Categories
Type=Fixed

[categories/48]
Size=48
Context=Categories
Type=Scalable

[categories/64]
Size=64
Context=Categories
Type=Scalable

[categories/128]
Size=128
Context=Categories
Type=Scalable

[devices/16]
Size=16
Context=Devices
Type=Fixed

[devices/22]
Size=22
Context=Devices
Type=Fixed

[devices/24]
Size=24
Context=Devices
Type=Fixed

[devices/32]
Size=32
Context=Devices
Type=Fixed

[devices/48]
Size=48
Context=Devices
Type=Scalable

[devices/64]
Size=64
Context=Devices
Type=Scalable

[devices/128]
Size=128
Context=Devices
Type=Scalable

[emblems/16]
Size=16
Context=Emblems
Type=Fixed

[emblems/22]
Size=22
Context=Emblems
Type=Fixed

[emblems/24]
Size=24
Context=Emblems
Type=Fixed

[emblems/32]
Size=32
Context=Emblems
Type=Fixed

[emblems/48]
Size=48
Context=Emblems
Type=Scalable

[emblems/64]
Size=64
Context=Emblems
Type=Scalable

[emblems/128]
Size=128
Context=Emblems
Type=Scalable

[mimes/16]
Size=16
Context=MimeTypes
Type=Fixed

[mimes/22]
Size=22
Context=MimeTypes
Type=Fixed

[mimes/24]
Size=24
Context=MimeTypes
Type=Fixed

[mimes/32]
Size=32
Context=MimeTypes
Type=Fixed

[mimes/48]
Size=48
Context=MimeTypes
Type=Scalable

[mimes/128]
Size=128
Context=MimeTypes
Type=Scalable

[places/16]
Size=16
Context=Places
Type=Fixed

[places/22]
Size=22
Context=Places
Type=Fixed

[places/24]
Size=24
Context=Places
Type=Fixed

[places/32]
Size=32
Context=Places
Type=Fixed

[places/48]
Size=48
Context=Places
Type=Fixed

[places/64]
Size=64
Context=Places
Type=Fixed

[places/128]
Size=128
Context=Places
Type=Fixed

[status/16]
Size=16
Context=Status
Type=Fixed

[status/22]
Size=22
Context=Status
Type=Fixed

[status/24]
Size=24
Context=Status
Type=Fixed

[status/32]
Size=32
Context=Status
Type=Fixed

[status/48]
Size=48
Context=Status
Type=Scalable

[status/64]
Size=64
Context=Status
Type=Scalable

[status/128]
Size=128
Context=Status
Type=Scalable

[notifications/16]
Size=16
Context=Status
Type=Fixed

[notifications/22]
Size=22
Context=Status
Type=Fixed

[notifications/24]
Size=24
Context=Status
Type=Fixed

[notifications/32]
Size=32
Context=Status
Type=Fixed

[notifications/48]
Size=48
Context=Status
Type=Scalable

[panel/16]
Size=16
Context=Status
Type=Fixed

[panel/22]
Size=22
Context=Status
Type=Fixed

[panel/24]
Size=24
Context=Status
Type=Fixed

[panel/48]
Size=48
Context=Status
Type=Scalable

[stock/16]
Size=16
Context=Stock
Type=Fixed

[stock/22]
Size=22
Context=Stock
Type=Fixed

[stock/24]
Size=24
Context=Stock
Type=Fixed

[stock/32]
Size=32
Context=Stock
Type=Fixed

[stock/48]
Size=48
Context=Stock
Type=Scalable

[tools/22]
Size=22
Context=Actions
Type=Fixed

```

I took the chance to search for files with *xfpm* in the name
```
find /usr/share/icons/ -iname "*xfpm-*"
```
and I found that the "wrong" icons I see are in a different elementary directory 
/usr/share/icons/elementary/panel/22

those are named "gpm-battery-0x0.svg", and "gpm-battery-0x0-charging.svg" with x being 0, 2 or 4.

So, apparently the xfce4-power-manager is using the gpm icons...

That got me wondering if there are files in the .../22 directory that aren't in the .../48 directory.
I guess it wasn't fruitful... here are the ones I found, just in case I overlooked something:
```

account-logged-in.svg
applications-chat-panel.svg
applications-email-panel.svg
audio-input-microphone-high-panel.svg
audio-input-microphone-none-panel.svg
audio-output-none-panel.svg
audio-volume-high-panel.svg
audio-volume-low-panel.svg
audio-volume-low-zero-panel.svg
audio-volume-medium-panel.svg
audio-volume-muted-blocking-panel.svg
audio-volume-muted-panel.svg
banshee-panel.svg
battery_plugged.svg
blueman-tray.svg
bluetooth-active.svg
bluetooth-disabled.svg
bluetooth-paired.svg
dropboxstatus-busy.svg
dropboxstatus-busy2.svg
dropboxstatus-idle.svg
dropboxstatus-logo.svg
dropboxstatus-x.svg
gnome-do-symbolic.svg
gnome-main-menu.svg
gpm-keyboard-000.svg
gpm-keyboard-020.svg
gpm-keyboard-040.svg
gpm-keyboard-060.svg
gpm-keyboard-080.svg
gpm-keyboard-100.svg
gpm-phone-100_alt.svg
gsd-xrandr.svg
gsm-3g-full.svg
gsm-3g-high.svg
gsm-3g-low.svg
gsm-3g-medium.svg
gsm-3g-none.svg
gtg-panel.svg
gtk-dialog-authentication-panel.svg
haguichi-connected.svg
haguichi-connecting-1.svg
haguichi-connecting-2.svg
haguichi-connecting-3.svg
haguichi-disconnected.svg
indicator-messages-new.svg
indicator-messages.svg
krb-valid-ticket.svg
nm-adhoc.svg
nm-device-wired-autoip.svg
nm-signal-0.svg
nm-signal-00.svg
nm-signal-100.svg
nm-signal-25.svg
nm-signal-50.svg
nm-signal-75.svg
nm-tech-3g.svg
nm-tech-cdma-1x.svg
nm-tech-edge.svg
nm-tech-evdo.svg
nm-tech-gprs.svg
nm-tech-hspa.svg
nm-tech-umts.svg
nm-vpn-active-lock.svg
nm-vpn-connecting12.svg
nm-vpn-connecting13.svg
nm-vpn-connecting14.svg
nm-vpn-lock.svg
nm-vpn-standalone-lock.svg
nm-wwan-tower.svg
novell-button.svg
preferences-desktop-accessibility-panel.svg
rhythmbox-notplaying.svg
rhythmbox-panel.svg
start-here.svg
steadyflow-alert-panel.svg
steadyflow-panel.svg
system-file-manager-panel.svg
system-restart-panel.svg
system-shutdown-panel-restart.svg
system-shutdown-panel.svg
tomboy-panel.svg
transmission-tray-icon.svg
ubuntuone-client-error.svg
ubuntuone-client-idle.svg
ubuntuone-client-offline.svg
ubuntuone-client-updating.svg
user-available-panel.svg
user-away-panel.svg
user-busy-panel.svg
user-idle-panel.svg
user-invisible-panel.svg
user-offline-panel.svg
xchat-panel.svg
xfce4-mixer-muted.svg
xfce4-mixer-no-muted.svg
xfce4-mixer-no-record.svg
xfce4-mixer-record.svg
xfce4-mixer-volume-high.svg
xfce4-mixer-volume-low-medium.svg
xfce4-mixer-volume-low.svg
xfce4-mixer-volume-medium.svg
xfce4-mixer-volume-muted.svg
xfce4-mixer-volume-ultra-low.svg
xfce4-mixer-volume-very-high.svg
xfpm-ac-adapter.svg
xfpm-keyboard-000.svg
xfpm-keyboard-030.svg
xfpm-keyboard-060.svg
xfpm-keyboard-100.svg
xfpm-mouse-030.svg
xfpm-phone-030.svg

```

---

