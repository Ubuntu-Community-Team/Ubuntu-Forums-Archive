---
title: "Touchpad still not working after trying ten different fixes"
date: 2019-12-13
forum: General Help
---

### Post by Jim_Henry on 2019-12-13
A few days ago, I came home to find that my laptop (a Dell Inspiron (?)) had powered off.
There hadn't been a power outage as far as I know.  When I booted it up again, the mouse
pointer no longer responded to the touchpad, either by motion or clicking.

I've found a number of webpages and videos talking about how to fix a recalcitrant
touchpad on Ubuntu, and tried many different fixes.  Diagnostics such as

xinput list

and

less /proc/bus/input/devices

and

xsetpointer -l

suggest that the problem is in software rather than hardware.  The Synaptics
touchpad is recognized and listed in all those programs' output.

However, none of the software fixes I've tried so far have worked:

- gsettings set org.gnome.settings-daemon.plugins.cursor active false

- installing xserver-xorg-input-synaptics

- installing ubuntu-restricted-extras

- editing /etc/default/grub to add "i8042.reset" to GRUB_CMDLINE_LINUX_DEFAULT
  (and running update-grub afterward)

- adding psmouse.proto=bare to GRUB_CMDLINE_LINUX_DEFAULT
  (did update-grub and rebooted both with and without the i8042.reset parameter)

- installing touchpad-indicator

- do Ctrl-Alt-F7, then Ctrl-Alt-F1

- do Ctrl-Alt-F5, then Ctrl-Alt-F1

- `modprobe -r psmouse` followed by `modprobe psmouse proto=bare`

Not necessarily in that order.  I rebooted after most of those fixes, either immediately or after trying another fix.  The mouse pointer still doesn't respond to the touchpad in any way.  Any
more ideas?

---

### Post by rsteinmetz70112 on 2019-12-13
Have you confirmed the hardware still works? 
Try starting the computer with a live session, if it works in a live session it ain't broke and the problem is software.
Post the output from the various commands, perhaps someone can spot something.

---

### Post by Jim_Henry on 2019-12-14
Okay, I created a live USB with 18.04.3 and booted from it, and the touchpad works fine.  Here are the diagnostics commands' output on both my regular setup (as modified by the various fixes I've tried so far):

```

xinput list | grep pointer 

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 04d9:1400                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Synaptics TM3096-006                        id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=17    [slave  pointer  (2)]


grep -B 2 -A 9 Synaptics /proc/bus/input/devices

I: Bus=0018 Vendor=06cb Product=78f6 Version=0100
N: Name="Synaptics TM3096-006"
P: Phys=i2c-DELL078B:00
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-DELL078B:00/0018:06CB:78F6.0003/input/input12
U: Uniq=
H: Handlers=mouse2 event11 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=6f3800001000003



xsetpointer -l | grep Pointer 

2: "Virtual core pointer"    [XPointer]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
11: "HID 04d9:1400"    [XExtensionPointer]
13: "Synaptics TM3096-006"    [XExtensionPointer]
17: "PS/2 Generic Mouse"    [XExtensionPointer]

```

And here are the same diagnostics when running from the live USB:

```

xinput list | grep pointer 

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 04d9:1400 Mouse                         id=13    [slave  pointer  (2)]
&#9116;   &#8627; Synaptics TM3096-006                        id=15    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=19    [slave  pointer  (2)]


grep -B 2 -A 9 Synaptics /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0007 Version=01a1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

--

I: Bus=0018 Vendor=06cb Product=78f6 Version=0100
N: Name="Synaptics TM3096-006"
P: Phys=i2c-DELL078B:00
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-4/i2c-DELL078B:00/0018:06CB:78F6.0003/input/input23
U: Uniq=
H: Handlers=mouse2 event12 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=6f3800001000003



xsetpointer -l | grep Pointer 

2: "Virtual core pointer"    [XPointer]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
13: "HID 04d9:1400 Mouse"    [XExtensionPointer]
15: "Synaptics TM3096-006"    [XExtensionPointer]
19: "SynPS/2 Synaptics TouchPad"    [XExtensionPointer]

```

Right away I see a difference -- the presence of the "SynPS/2 Synaptics TouchPad" in the live USB setup vs.  "PS/2 Generic Mouse" when booting from my hard drive.  I suspect this is related to one of the fixes I tried that didn't work.  I remember seeing the SynPS/2" in the output the first time I ran those diagnostic commands a couple of days ago.  I'm going to try undoing some of the so-called "fixes", starting with removing "psmouse.proto=bare" from GRUB_CMDLINE_LINUX_DEFAULT, and see if that makes the diagnostic commands' output match up better (and if it fixes the touchpad).  Any other ideas for what to do?

For further information, here is the full contents of /proc/bus/input/devices, unfiltered by grep.

```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 leds 
B: PROP=0
B: EV=120013
B: KEY=1100f02902000 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=04d9 Product=1400 Version=0110
N: Name="HID 04d9:1400"
P: Phys=usb-0000:00:14.0-3.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/0003:04D9:1400.0001/input/input7
U: Uniq=
H: Handlers=sysrq kbd event6 leds 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04d9 Product=1400 Version=0110
N: Name="HID 04d9:1400"
P: Phys=usb-0000:00:14.0-3.4/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.1/0003:04D9:1400.0002/input/input8
U: Uniq=
H: Handlers=kbd mouse1 event7 
B: PROP=0
B: EV=17
B: KEY=1f0000 1000002000000 39fad941d001 1e000000000000 0
B: REL=103
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Intel HID events"
P: Phys=
S: Sysfs=/devices/platform/INT33D5:00/input/input9
U: Uniq=
H: Handlers=rfkill kbd event8 
B: PROP=0
B: EV=13
B: KEY=81000300000000 5000004000 1e294000000020 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=
S: Sysfs=/devices/platform/PNP0C14:00/wmi_bus/wmi_bus-PNP0C14:00/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input11
U: Uniq=
H: Handlers=rfkill kbd event10 
B: PROP=0
B: EV=13
B: KEY=800000000000 0 0 101500b00000c00 200300000 e000000000000 0
B: MSC=10

I: Bus=0018 Vendor=06cb Product=78f6 Version=0100
N: Name="Synaptics TM3096-006"
P: Phys=i2c-DELL078B:00
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-DELL078B:00/0018:06CB:78F6.0003/input/input12
U: Uniq=
H: Handlers=mouse2 event11 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=6f3800001000003

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input13
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input14
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input15
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input16
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input17
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input18
U: Uniq=
H: Handlers=event17 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=0bda Product=5769 Version=5268
N: Name="Integrated_Webcam_HD: Integrate"
P: Phys=usb-0000:00:14.0-5/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input19
U: Uniq=
H: Handlers=kbd event18 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

```

---

### Post by mörgæs on 2019-12-14
Does this help?
[https://ubuntuforums.org/showthread.php?t=2432565](https://ubuntuforums.org/showthread.php?t=2432565)

---

### Post by Jim_Henry on 2019-12-14
Installing the 5.0.0-37 kernel using the instructions in that thread fixed the problem; thanks.  

I had also removed "psmouse.proto=bare" from GRUB_CMDLINE_LINUX_DEFAULT before I tried that, which didn't fix the touchpad issue by itself, although it made the output of the various diagnostic commands converge with the output of the same commands on the live USB.

---

