---
title: "Problem with suspend in 22.04 jammy on new build - Gigabyte B550 Vision DP"
date: 2022-05-26
forum: General Help
---

### Post by xoorox2 on 2022-05-26
I had a problem with not being able to suspend - the machine would suspend (you'd hear the click as the power supply turned off) and then immediately wake.  I've got a fix now but I thought I'd share in case it's helpful to someone else.

I first did a little digging... tried the tweaks lid setting (even though it's a desktop).
In the end [this post in the linuxmint]("https://forums.linuxmint.com/viewtopic.php?p=1772976#p1772976") forum pushed me in the right direction.

In my case though, it wasn't a bluetooth mouse causing the problem.  I methodically ruled out external devices (usb audio interface, a midi interface, wireless dongle for mouse/keyboard) just by unplugging them.

Using **cat /proc/bus/input/devices** to look at my list of input devices gave me

```
cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=046d Product=4023 Version=0111
N: Name="Logitech Wireless Keyboard PID:4023"
P: Phys=usb-0000:02:00.0-10.1/input1:1
S: Sysfs=/devices/pci0000:00/0000:00:01.2/[COLOR=#b22222]_**0000:02:00.0**_[/COLOR]/usb1/1-10/1-10.1/1-10.1:1.1/0003:046D:C534.0003/0003:046D:4023.0004/input/input17
U: Uniq=4023-00-00-00-00
H: Handlers=sysrq kbd event2 leds 
B: PROP=0
B: EV=12001f
B: KEY=3f000307ff 0 0 483ffff17aff32d bfd4444600000000 1 130ff38b17d007 ffff7bfad941dfff ffbeffdfffefffff fffffffffffffffe
B: REL=1040
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=4091 Version=0111
N: Name="Logitech Wireless Mouse"
P: Phys=usb-0000:02:00.0-10.1/input1:2
S: Sysfs=/devices/pci0000:00/0000:00:01.2/[COLOR=#b22222]_**0000:02:00.0**_[/COLOR]/usb1/1-10/1-10.1/1-10.1:1.1/0003:046D:C534.0003/0003:046D:4091.0005/input/input18
U: Uniq=4091-00-00-00-00
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=1943
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input19
U: Uniq=
H: Handlers=event4 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input20
U: Uniq=
H: Handlers=event5 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input21
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input22
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input23
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=11"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input24
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=12"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.1/0000:53:00.1/sound/card0/input25
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input26
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input27
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input28
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Line Out Front"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input29
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Line Out Surround"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input30
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Line Out CLFE"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input31
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:08.1/0000:55:00.4/sound/card2/input32
U: Uniq=
H: Handlers=event17 
B: PROP=0
B: EV=21
B: SW=4

```

This I compare with the output of **cat /proc/acpi/wakeup**

```
cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
GP12      S4    *enabled   pci:0000:00:07.1
GP13      S4    *disabled  pci:0000:00:08.1
XHC0      S4    *enabled   pci:0000:55:00.3
GP30      S4    *disabled
GP31      S4    *disabled
PS2K      S3    *disabled
PS2M      S3    *disabled
[COLOR=#006400]GPP0      S4    *enabled   pci:0000:00:01.1[/COLOR]
GPP8      S4    *enabled   pci:0000:00:03.1
_[COLOR=#b22222]**PTXH      S4    *enabled   pci:0000:02:00.0**[/COLOR]_
PT20      S4    *enabled   pci:0000:03:00.0
PT23      S4    *disabled
PT24      S4    *enabled   pci:0000:03:04.0
PT26      S4    *disabled
PT27      S4    *disabled
PT28      S4    *enabled   pci:0000:03:08.0
PT29      S4    *enabled   pci:0000:03:09.0

```

To toggle on and off a line, I would use (for example) **echo PTXH | sudo tee /proc/acpi/wakeup** to stop the mouse/keyboard from being able to wake the machine up.  **[COLOR=#800080]*_But in my case it wasn't this_*[/COLOR]**.  (I re-enabled as I'd like to be able to wake the machine using the mouse/keyboard).

I didn't find a culprit in the list of input devices.  I tried GPP8 as this appeared to cover off everything related to my monitor.  In the end I looked at the output of **lspci** as before I tried disabling the other items in the list, I wanted to know what they were.
In the end it was disabling [COLOR=#006400]GPP0[/COLOR] that fixed things for me.  In 

```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
_[COLOR=#006400]**00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge**[/COLOR]_
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
...
```

So I don't know quite what's going on here, but it does seem to have solved my problem for the time being.

---

### Post by xoorox2 on 2022-06-07
So I've marked this unsolved again - when you restart the setting is lost.  I can have the command run at startup... but surely there's a better fix out there, anyone?

---

### Post by xoorox2 on 2022-06-08
For the record, I successfully followed these instructions here - [https://askubuntu.com/questions/1146264/apply-the-proc-acpi-wakeup-settings-permanently](https://askubuntu.com/questions/1146264/apply-the-proc-acpi-wakeup-settings-permanently) to set up a script to create a service to run a script to disable chosen devices (if they are enabled).

---

### Post by skrueger on 2023-05-22
You are my hero! Thank you! Disabling GPP0 fix this for me. I have the same Gigabyte B550 Vision DP and it was failing to suspend. It would crash after I tried to suspend with the same power click after it appeared to suspend just like you said. The motherboard post code / Debug LED code showed 21, and on the manual the description for those are under "Reserved.".  Doing sudo sh -c "echo GPP0 > /proc/acpi/wakeup", to switch GPP0 from *enabled to *disabled state did the trick!

---

