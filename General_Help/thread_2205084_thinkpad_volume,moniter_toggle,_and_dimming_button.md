---
title: "thinkpad volume,moniter toggle, and dimming buttons not working anymore"
date: 2014-02-11
forum: General Help
---

### Post by nez2 on 2014-02-11
Had Mint and then one day last week my volume buttons, dimming buttons, monitor toggle, no camera, wlan on/off stopped working but the pause/play and next/back keys work. Not sure what update caused this and reverted back to a fresh install of 12 LTS since I knew it worked before with them. No luck. Have searched this issue and many thinkpads were affected and tried some solutions that worked for some. I can't change by keyboard shortcuts, installed keytouch but it doesn't register the keys, and few others editing keymaps. I think my issues are because the "event5" input isn't routed or driver is missing. The keys work and i can route function keys to do the  volume but not the rest and I don't want to use the f keys. I have lenovo thinkpad edge, let me know what info/code you need. Thanks in advance.

part of my xorg log

[  4455.372] (II) evdev: Power Button: Configuring as keyboard
[  4455.372] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  4455.372] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  4455.372] (**) Option "xkb_rules" "evdev"
[  4455.372] (**) Option "xkb_model" "pc105"
[  4455.372] (**) Option "xkb_layout" "us"
[  4455.373] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  4455.373] (II) No input driver specified, ignoring this device.
[  4455.373] (II) This device may have been added with another device file.
[  4455.373] (II) config/udev: Adding drm device (/dev/dri/card0)
[  4455.373] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  4455.373] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event5)
[  4455.373] (II) No input driver specified, ignoring this device.
[  4455.373] (II) This device may have been added with another device file.
[  4455.373] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event6)
[  4455.373] (II) No input driver specified, ignoring this device.
[  4455.373] (II) This device may have been added with another device file.
[  4455.374] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event7)
[  4455.374] (II) No input driver specified, ignoring this device.
[  4455.374] (II) This device may have been added with another device file.
[  4455.374] (II) config/udev: Adding input device Integrated Camera (/dev/input/event10)
[  4455.374] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[  4455.374] (II) Using input driver 'evdev' for 'Integrated Camera'
[  4455.374] (**) Integrated Camera: always reports core events
[  4455.374] (**) evdev: Integrated Camera: Device: "/dev/input/event10"

---

### Post by nez2 on 2014-02-16
bump

---

