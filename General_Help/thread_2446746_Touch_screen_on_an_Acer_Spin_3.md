---
title: "Touch screen on an Acer Spin 3"
date: 2020-07-06
forum: General Help
---

### Post by 5thdoctor on 2020-07-06
I recently got an Acer Spin 3 on sale at costco and installed Ubuntu to an external drive (as it's hard for me to live with out GNU on any computer I bring home). The touchpad and touchscreen drivers where not auto detected. Trying to use install additional drives had no effect. In the Uefi setting I was able to change the touchpad to from ic2 to ps2 and it was detected Ubuntu, but now it doesn't behave quite right in windows. However I have yet to find away to get touchscreen support working in Ubuntu. Googling raveled xinput_calibrator however it claims there is no touch screen. I don't remember setting up ubuntu where a device didn't just work, except way back when with a already old Dell XP laptop and it's broadcom wifi, never was sure how I got that working eventually. So my ideas for trouble shooting are limited. I still am in the time frame where if I decided for the money it's not worth it I can try to return it, but otherwise it's a nice little machine I'd like to get working fully in GNU if possible.

---

### Post by ActionParsnip on 2020-07-06
Do you have the latest BIOS? May help

---

### Post by 5thdoctor on 2020-07-06
I checked and there was an optional bios update however there was no change to ubuntu even when booting from a live environment. Xinput list output
```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; HD User Facing: HD User Facing              id=8    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=9    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)
```
 lsusb
```
lsusb
Bus 004 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b64f Chicony Electronics Co., Ltd HD User Facing
Bus 003 Device 002: ID 06cb:00dc Synaptics, Inc. 
Bus 003 Device 004: ID 8087:0026 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
and lsinput
```
sudo lsinput
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : (null) (null)

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : (null) (null)

/dev/input/event2
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : (null) (null) (null) (null) (null)

/dev/input/event3
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 417
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : (null) (null) (null)

/dev/input/event4
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Intel HID events"
   bits ev : (null) (null) (null)

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Intel HID 5 button array"
   bits ev : (null) (null) (null)

/dev/input/event6
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Acer WMI hotkeys"
   phys    : "wmi/input0"
   bits ev : (null) (null) (null)

/dev/input/event7
   bustype : BUS_USB
   vendor  : 0x4f2
   product : 0xb64f
   version : 38473
   name    : "HD User Facing: HD User Facing"
   phys    : "usb-0000:00:14.0-7/button"
   bits ev : (null) (null)

/dev/input/event8
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : (null) (null)

/dev/input/event9
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "sof-hda-dsp Headphone"
   phys    : "ALSA"
   bits ev : (null) (null)

/dev/input/event10
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "sof-hda-dsp HDMI/DP,pcm=3"
   phys    : "ALSA"
   bits ev : (null) (null)

/dev/input/event11
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "sof-hda-dsp HDMI/DP,pcm=4"
   phys    : "ALSA"
   bits ev : (null) (null)

/dev/input/event12
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "sof-hda-dsp HDMI/DP,pcm=5"
   phys    : "ALSA"
   bits ev : (null) (null)
```

---

### Post by mfcarpino on 2020-07-10
You might want to try what I did to get it to work. [https://ubuntuforums.org/showthread.php?t=2445152&highlight=touch+screen](https://ubuntuforums.org/showthread.php?t=2445152&highlight=touch+screen)

---

### Post by jonesmeier on 2021-06-21
Hey, I had the same problem, check out this thread with some boot parameters to make it work: [https://ubuntuforums.org/showthread.php?t=2450981](https://ubuntuforums.org/showthread.php?t=2450981)

---

