---
title: "Disable touchpad while typing"
date: 2024-02-06
forum: General Help
---

### Post by adrian-tres on 2024-02-06
Hi,

I must have the largest freaking palms in the world because every I type I  accidentally press on my touchpad and focus on a different window or a  different line in the file that I'm typing in. This has finally pissed  me off to the point of posting on here. 

I enabled "Disable while typing" in gnome-tweaks, but that didn't work.  I'm not sure what all these virtual keyboard are, but I can at least see  that "ELAN0683:00 04F3:320B Touchpad" does in fact have  "disable-w-typing" enabled.

Output of xinput:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; keyd virtual pointer                        id=18    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 Synaptics TrackPoint                 id=15    [slave  pointer  (2)]
&#9116;   &#8627; ELAN0683:00 04F3:320B Touchpad              id=12    [slave  pointer  (2)]
&#9116;   &#8627; ELAN0683:00 04F3:320B Mouse                 id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=13    [slave  keyboard (3)]
    &#8627; Integrated RGB Camera: Integrat             id=10    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=16    [slave  keyboard (3)]
    &#8627; keyd virtual keyboard                       id=17    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Integrated RGB Camera: Integrat             id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]

```

Output of libinput show-devices:

```
Device:           ELAN0683:00 04F3:320B Touchpad
Kernel:           /dev/input/event6
Group:            6
Seat:             seat0, default
Size:             114x65mm
Capabilities:     pointer gesture
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    *button-areas clickfinger 
Disable-w-typing: enabled
Accel profiles:   flat *adaptive
Rotation:         n/a
...
Device:           AT Translated Set 2 keyboard
Kernel:           /dev/input/event3
Group:            8
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a

...

Device:           keyd virtual keyboard
Kernel:           /dev/input/event14
Group:            11
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a

Device:           keyd virtual pointer
Kernel:           /dev/input/event15
Group:            12
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      identity matrix
Scroll methods:   button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a

```


P.S typing this post up triggered the touchpad five freaking times... 

Thanks
]

---

### Post by ajgreeny on 2024-02-06
Run terminal command
**inxi -Fzx**
and paste the full output back here using code tags please.
See my signature below for a how-to of code tags. 

There is normally a setting in the mouse/touchpad config window to do what you want but maybe it's missing from some versions and may depend on your touch pad type.

---

### Post by adrian-tres on 2024-02-06
Here you go sir:
```
$ inxi -Fzx
System:
  Kernel: 6.1.0-1029-oem x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 21D6004TUS v: ThinkPad P16 Gen 1
    serial: <superuser required>
  Mobo: LENOVO model: 21D6004TUS v: SDK0T76530 WIN
    serial: <superuser required> UEFI: LENOVO v: N3FET36W (1.21 )
    date: 05/31/2023
Battery:
  ID-1: BAT0 charge: 95.9 Wh (100.0%) condition: 95.9/94.0 Wh (102.0%)
    volts: 13.1 min: 11.6 model: LGES 5B10W51894 status: Full
CPU:
  Info: 16-core (8-mt/8-st) model: 12th Gen Intel Core i7-12800HX bits: 64
    type: MST AMCP arch: Alder Lake rev: 2 cache: L1: 1.4 MiB L2: 14 MiB
    L3: 25 MiB
  Speed (MHz): avg: 805 high: 869 min/max: 800/4700:4800:3400 cores: 1: 818
    2: 800 3: 800 4: 800 5: 869 6: 800 7: 808 8: 800 9: 831 10: 800 11: 800
    12: 800 13: 800 14: 800 15: 800 16: 800 17: 800 18: 800 19: 800 20: 800
    21: 800 22: 816 23: 800 24: 800 bogomips: 110592
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA vendor: Lenovo driver: nvidia v: 535.154.05
    bus-ID: 01:00.0
  Device-2: Acer Integrated RGB Camera type: USB driver: uvcvideo
    bus-ID: 1-4:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia resolution:
    1: 3840x2400~60Hz 2: 10240x2880~240Hz
  OpenGL: renderer: NVIDIA RTX A1000 Laptop GPU/PCIe/SSE2
    v: 4.6.0 NVIDIA 535.154.05 direct render: Yes
Audio:
  Device-1: Intel vendor: Lenovo driver: sof-audio-pci-intel-tgl
    bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Lenovo driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k6.1.0-1029-oem running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel driver: iwlwifi v: kernel port: N/A bus-ID: 00:14.3
  IF: wlp0s20f3 state: up mac: <filter>
  IF-ID-1: docker0 state: down mac: <filter>
  IF-ID-2: virbr0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus-ID: 1-14:4
  Report: hciconfig ID: hci0 rfk-id: 2 state: up address: <filter>
Drives:
  Local Storage: total: 953.87 GiB used: 93.26 GiB (9.8%)
  ID-1: /dev/nvme0n1 vendor: KIOXIA model: N/A size: 953.87 GiB
    temp: 52.9 C
Partition:
  ID-1: / size: 937.33 GiB used: 93.25 GiB (9.9%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 46.0 C mobo: N/A gpu: nvidia temp: 56 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 473 Uptime: 1h 31m Memory: 31.11 GiB used: 7.98 GiB (25.6%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2412 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


```

---

### Post by Rubi1200 on 2024-02-07
Have you tried this

```
xinput disable 12

```

Where 12 is your touchpad ID?

If it works or when you need the touchpad, simply replace disable with enable in the command.

---

### Post by adrian-tres on 2024-02-08
This completely disables the touchpad, which isn't what I want to do. I just want it to not be active while I type

---

### Post by #&amp;thj^% on 2024-02-08
From your terminal will show you ie:
```
gsettings get org.gnome.desktop.peripherals.touchpad disable-while-typing
true

```
That's my output
this should have what you want: 
```
 gsettings set org.gnome.desktop.peripherals.touchpad disable-while-typing true

```
To revert
```
gsettings set org.gnome.desktop.peripherals.touchpad disable-while-typing false

```
Check:
```
gsettings get org.gnome.desktop.peripherals.touchpad disable-while-typing
false

```

---

### Post by him610 on 2024-02-08
Evidently, there are several ways to accomplish the same thing. I have defined some ***alias*** to disable/enable the trackpad. 
Run it from a terminal.
```

alias trkon="synclient TouchpadOff=0"
alias trkof="synclient TouchpadOff=1"

```

---

### Post by Holger_Gehrke on 2024-02-09
The problem reads to me like the timeout after a keypress is a bit to short (the trackpad suppression basically works by disregarding all input from the trackpad after a key press for a certain time). In XFCE there is a slider to set the length of this timeout in the graphical 'Mouse and Trackpad' settings applet. I'd be surprised if there wasn't something similar in Gnome.

If there isn't and you're not using Wayland, you might want to try using 'syndaemon' from the package 'xserver-xorg-input-synaptics' to implement this functionality instead of what's built into Gnome. You can set the length of the timeout with the option '-i <length of timeout in seconds>'. I don't think syndaemon works with Wayland, but you could try whether it does ...

Holger

---

### Post by psychohermit on 2024-02-10
I have my touchpad disabled and am using a wired USB mouse.  I can't seem to get the hang of the touchpad.

--glenn

---

