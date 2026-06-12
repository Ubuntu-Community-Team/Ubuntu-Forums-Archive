---
title: "Need individual configuration settings for multiple mice (mouses)"
date: 2008-03-26
forum: General Help
---

### Post by MountainX on 2008-03-26
I have 3 usb mice plugged in. They all work fine without any special configuration. However, I need to swap buttons 2 and 3 on just one of the mice. How can I do this?

When I edit xorg.conf and specify "ButtonMapping" "1 3 2" it obviously changes all my mice.

I thought I might be able to specify the configurations individually in xorg.conf, but I'm not sure about some of the details. I found examples that would work if my mice all used different drivers, but these are all regular USB mice.

In one xorg.conf example, I see the following:
```

 Option  "Dev Phys" "usb-0000:00:1d.3-*/input0"

```
Can I use the sysfs identifier in a similar way?

Here is the output of cat /proc/bus/input/devices. My main mouse is the  "Contour Design RollerMouse Pro" and this is the one I want to swap the buttons on. The others are fine with the default settings.

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input1
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=05f3 Product=0203 Version=0100
N: Name="P.I. Engineering PC Keyboard/Mouse to USB  Adapter"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120013
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05f3 Product=0203 Version=0100
N: Name="P.I. Engineering PC Keyboard/Mouse to USB  Adapter"
P: Phys=usb-0000:00:02.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=0b33 Product=0700 Version=0110
N: Name="Contour Design RollerMouse Pro"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
U: Uniq=
H: Handlers=mouse3 event4 
B: EV=1f
B: KEY=1f0003 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0


```

Thanks.

---

### Post by forrestcupp on 2008-03-26
Do you actually have separate cursors that these mice control, or are they all controlling the same cursor?

---

### Post by MountainX on 2008-03-26
They are controlling the same cursor.

So far I tried some settings using "Dev Phys" and the result was diasterous. I certainly could use some advice.

---

### Post by MountainX on 2008-03-26
I found the solution here:
[http://articles.rootsmith.ca/linux/logitech-mx-revolution-mouse-on-linux](http://articles.rootsmith.ca/linux/logitech-mx-revolution-mouse-on-linux)

 # Just configure ***one*** of the following two Options
        Option          "Phys"  "usb-*/input0" # USB port independant
#       Option          "Device" "/dev/input/event1" # USB port dependant

I had two things configured before. I went with this style
Option          "Device" "/dev/input/event[COLOR="Red"]**X**[/COLOR]" # USB port dependant

where **[COLOR="Red"]X[/COLOR]** comes from the device as listed in cat /proc/bus/input/devices

The reason I went with the "USB port dependent" method was because, if you look at my output of cat /proc/bus/input/devices, they would all match the pattern  "usb-*/input0"
For example, here are two of my devices:
P: Phys=usb-0000:00:02.0-2/input0
P: Phys=usb-0000:00:02.0-3/input0

I figured if I changed the pattern to  "usb-*-2/input0" it might not be port independent anymore -- and it might also not work, so I went with something a bit more likely to work.

**If anyone can tell me how to do what I did in a port independent manner, please tell me.**

Also note this comment - this tripped me up previously:
        Option          "CorePointer" # must exist after Phys or Devic

---

### Post by forrestcupp on 2008-03-26
Thank you for posting the solution when you found it.

---

### Post by MountainX on 2008-03-26
> **forrestcupp said:**
> Thank you for posting the solution when you found it.

Yeah, I like it when people do that too.

I'm been continuing to experiment and I learned one more fact. The output of cat /proc/bus/input/devices lists two handlers for each mouse. Either one works as the device option in xorg.conf as shown below in bold

Section "InputDevice"
	# I: Bus=0003 Vendor=0b33 Product=0700 Version=0110
	# N: Name="Contour Design RollerMouse Pro"
	# P: Phys=usb-0000:00:02.0-4/input0
	# S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
	# U: Uniq=
	#** H: Handlers=mouse3 event4 **
	# B: EV=1f
	# B: KEY=1f0003 0 0 0 0 0 0 0 0
	# B: REL=103
	# B: ABS=300 0
	# B: MSC=10
	# Option		"Dev Phys"	"usb-0000:00:02.0-4/input0"
	Identifier	"RollerMouse"
	Driver		"mouse"
	#either one of these will work. 
	#Option		"Device"	"/dev/input/event4"
	**Option		"Device"	"/dev/input/mouse3**

---

### Post by MountainX on 2008-03-30
All I need to do now, to completely solve this issue, is to be able to specify input devices in xorg.conf in a **USB-port-independent** manner. Does anyone know how to do this? Thanks

---

