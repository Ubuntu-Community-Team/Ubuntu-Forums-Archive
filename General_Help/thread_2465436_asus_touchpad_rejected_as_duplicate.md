---
title: "asus touchpad rejected as duplicate"
date: 2021-08-01
forum: General Help
---

### Post by porphyry52 on 2021-08-01
Seems as if (from final line) that X rejects my Touchpad as a duplicate of the mouse, only, no mouse on laptop.
Lubuntu 21.04 on Asus L210
```
~ $ inxi
CPU: Dual Core Intel Celeron N4020 (-MCP-) speed/min/max: 2783/800/2800 MHz 
Kernel: 5.11.0-25-generic x86_64 Up: 1h 05m Mem: 1187.4/3749.8 MiB (31.7%) 
Storage: 177.33 GiB (48.1% used) Procs: 176 Shell: Bash inxi: 3.3.01 
~ $ cat /var/log/Xorg.0.log|grep Touchpad
[    10.673] (II) config/udev: Adding input device ASUE1409:00 04F3:3157 Touchpad (/dev/input/event7)
[    10.674] (**) ASUE1409:00 04F3:3157 Touchpad: Applying InputClass "libinput touchpad catchall"
[    10.674] (**) ASUE1409:00 04F3:3157 Touchpad: Applying InputClass "touchpad catchall"
[    10.674] (**) ASUE1409:00 04F3:3157 Touchpad: Applying InputClass "Default clickpad buttons"
[    10.723] (II) Using input driver 'synaptics' for 'ASUE1409:00 04F3:3157 Touchpad'
[    10.723] (**) ASUE1409:00 04F3:3157 Touchpad: always reports core events
[    10.754] (II) synaptics: ASUE1409:00 04F3:3157 Touchpad: found clickpad property
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: x-axis range 0 - 3204 (res 31)
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: y-axis range 0 - 1833 (res 31)
[    10.754] (II) synaptics: ASUE1409:00 04F3:3157 Touchpad: device does not report pressure, will use touch data.
[    10.754] (II) synaptics: ASUE1409:00 04F3:3157 Touchpad: device does not report finger width.
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: buttons: left double triple
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: Vendor 0x4f3 Product 0x3157
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: invalid pressure range.  defaulting to 0 - 255
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: invalid finger width range.  defaulting to 0 - 15
[    10.754] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: touchpad found
[    10.754] (**) ASUE1409:00 04F3:3157 Touchpad: always reports core events
[    10.794] (II) XINPUT: Adding extended input device "ASUE1409:00 04F3:3157 Touchpad" (type: TOUCHPAD, id 10)
[    10.794] (**) synaptics: ASUE1409:00 04F3:3157 Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    10.794] (**) synaptics: ASUE1409:00 04F3:3157 Touchpad: (accel) MaxSpeed is now 1.75
[    10.794] (**) synaptics: ASUE1409:00 04F3:3157 Touchpad: (accel) AccelFactor is now 0.054
[    10.795] (**) ASUE1409:00 04F3:3157 Touchpad: (accel) keeping acceleration scheme 1
[    10.795] (**) ASUE1409:00 04F3:3157 Touchpad: (accel) acceleration profile 1
[    10.795] (**) ASUE1409:00 04F3:3157 Touchpad: (accel) acceleration factor: 2.000
[    10.795] (**) ASUE1409:00 04F3:3157 Touchpad: (accel) acceleration threshold: 4
[    10.795] (--) synaptics: ASUE1409:00 04F3:3157 Touchpad: touchpad found
[    10.797] (II) config/udev: Adding input device ASUE1409:00 04F3:3157 Touchpad (/dev/input/mouse1)
[    10.797] (**) ASUE1409:00 04F3:3157 Touchpad: Ignoring device from InputClass "touchpad ignore duplicates" 

```

So I have no middle click paste. How should I fix this?

---

### Post by porphyry52 on 2021-08-04
The usual 'synclient Touchpad3=2' works but only if entered as an AutoStart. It didn't work for me at the cmdline, which threw me off.

---

