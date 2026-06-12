---
title: "Optical mouse not working"
date: 2014-04-21
forum: General Help
---

### Post by ivo_popov on 2014-04-21
Hello, i have just isntalled ubuntu 14.04 as second os, and my optical mouse is not working. When i plug in my old laser mouse it works, but my optical one doesnt. 
I dont know how but at one point it started to work but when i restarted the system it stopped again, it happened that it would work about 2 times and now i doesnt again.
My mouse is not branded, it sasy stealth series CNL-MBMS002, it works without a problem in windows.
Thanks

---

### Post by varunendra on 2014-04-22
Welcome to the forums ivo_popov!

While the problematic mouse is connected, please open a terminal (Ctrl-Alt-T) and run these commands in it -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If this doesn't activate the mouse, repeat the above commands, with the second one slightly changed -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

If any of these help, we may try to make it automatic. If not, please run the following command in the terminal -
```
xinput
```
..then change the mouse with the working one, and post back (copy-paste) the full output of the above last command in your next post here. The output of the last command may give us something more to try.

---

### Post by ivo_popov on 2014-04-22
hello, thanks for the help but it tidnt work :( here is the output
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Novatek Ultra Flat Keyboard             	id=9	[slave  keyboard (3)]
    &#8627; Novatek Ultra Flat Keyboard             	id=10	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=11	[slave  keyboard (3)]

---

### Post by varunendra on 2014-04-22
Please edit your post above to wrap the output within 'Code' tags. It preserves the formatting and makes the output look cleaner and more readable. Please follow the "Use Code Tags" link in my signature below to see a quick How To with screenshots.

Onto the problem - your mouse is not detected at all! Was it connected when you ran 'xinput' command? Is it a PS/2 mouse or a USB one? If it is a USB mouse, please post back the output of -
```
lsusb
```
..while it is connected. (And don't forget to use 'Code' tags for posting the outputs :))

---

### Post by ivo_popov on 2014-04-23
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Yes it is an usb mouse, iv reinstalled ubuntu, the mouse didnt work during the install, but after the first restart it worked, but now it doesnt again

---

### Post by ivo_popov on 2014-04-23
```

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; A4Tech PS/2+USB Mouse                       id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Novatek Ultra Flat Keyboard                 id=8    [slave  keyboard (3)]
    &#8627; Novatek Ultra Flat Keyboard                 id=9    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=10    [slave  keyboard (3)]

```

here is the xinput again with the both mouses connected at once, the old laser one is working but my new optical one isnt

---

### Post by varunendra on 2014-04-24
There is still only one physical Mouse detected and that is obviously your working one.

I am also curious about this (from your 'lsusb' output) -
```
Bus 003 Device 006: ID 0603:00f2 Novatek Microelectronics Corp.
```
This is the only USB device detected by the system (the other entries seem to be internal devices and hubs). But a quick search suggests it is a USB keyboard.

So.. do you have a USB keyboard as well? How many USB devices were plugged in when you ran the 'lsusb' command. If not sure now, please remove ALL USB devices, replug only the mouse (if you have a PS/2 keyboard to work with) and check lsusb again. If it is different than above, post it back.

If you only have a USB keyboard, not a PS/2 one, you may keep it plugged in, but no other device except the mouse.

With the mouse (only the non-working one) plugged in, please also post back the outputs of -
```
cat /proc/bus/input/devices
usb-devices
grep -i mouse /var/log/Xorg.0.log
lsmod
```
(you may plug in the working mouse AFTER running the above commands, to be able to copy-paste the outputs)

---

### Post by ivo_popov on 2014-04-24
Hello, when i started today the mouse worked again, here are the outputs when the optical mouse is working lsusb
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1d57:0010 Xenta 
Bus 003 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
i think the bus 003 is the mouse

and the output of the last code you sugested
```

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
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

I: Bus=0003 Vendor=1d57 Product=0010 Version=0110
N: Name="HID-Compliant Mouse usb mouse with wheel"
P: Phys=usb-0000:00:14.0-9/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event2 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=303
B: MSC=10

I: Bus=0003 Vendor=1d57 Product=0010 Version=0110
N: Name="HID-Compliant Mouse usb mouse with wheel"
P: Phys=usb-0000:00:14.0-9/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.1/input/input5
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0603 Product=00f2 Version=0110
N: Name="Novatek Ultra Flat Keyboard"
P: Phys=usb-0000:00:14.0-10/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/input/input6
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0603 Product=00f2 Version=0110
N: Name="Novatek Ultra Flat Keyboard"
P: Phys=usb-0000:00:14.0-10/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.1/input/input7
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=13
B: KEY=42bc00000000 f00 8000100000000001 40002040000 401878d800d408 1e000000000000 0
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=11"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Eee PC WMI hotkeys"
P: Phys=eeepc-wmi/input0
S: Sysfs=/devices/platform/eeepc-wmi/input/input20
U: Uniq=
H: Handlers=rfkill kbd event17 
B: PROP=0
B: EV=100013
B: KEY=7e40000 0 800000000000 0 0 1400b00100000 300180001100800 e000000000000 2
B: MSC=10

ivo@ivo-All-Series:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0603 ProdID=00f2 Rev=01.10
S:  Manufacturer=Novatek
S:  Product=Ultra Flat Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=350mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1d57 ProdID=0010 Rev=00.01
S:  Manufacturer=HID-Compliant Mouse
S:  Product=usb mouse with wheel
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
ivo@ivo-All-Series:~$ grep -i mouse /var/log/Xorg.0.log
[    11.648] (==) fglrx(0): Silken mouse enabled
[    11.821] (--) evdev: Novatek Ultra Flat Keyboard: Found 1 mouse buttons
[    11.821] (II) evdev: Novatek Ultra Flat Keyboard: Configuring as mouse
[    11.822] (II) config/udev: Adding input device HID-Compliant Mouse usb mouse with wheel (/dev/input/event2)
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: Applying InputClass "evdev pointer catchall"
[    11.822] (II) Using input driver 'evdev' for 'HID-Compliant Mouse usb mouse with wheel'
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: always reports core events
[    11.822] (**) evdev: HID-Compliant Mouse usb mouse with wheel: Device: "/dev/input/event2"
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Vendor 0x1d57 Product 0x10
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Found 12 mouse buttons
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Found scroll wheel(s)
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Found relative axes
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Found x and y relative axes
[    11.822] (II) evdev: HID-Compliant Mouse usb mouse with wheel: Configuring as mouse
[    11.822] (II) evdev: HID-Compliant Mouse usb mouse with wheel: Adding scrollwheel support
[    11.822] (**) evdev: HID-Compliant Mouse usb mouse with wheel: YAxisMapping: buttons 4 and 5
[    11.822] (**) evdev: HID-Compliant Mouse usb mouse with wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.822] (II) XINPUT: Adding extended input device "HID-Compliant Mouse usb mouse with wheel" (type: MOUSE, id 10)
[    11.822] (II) evdev: HID-Compliant Mouse usb mouse with wheel: initialized for relative axes.
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: (accel) keeping acceleration scheme 1
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: (accel) acceleration profile 0
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: (accel) acceleration factor: 2.000
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: (accel) acceleration threshold: 4
[    11.822] (II) config/udev: Adding input device HID-Compliant Mouse usb mouse with wheel (/dev/input/mouse0)
[    11.822] (II) config/udev: Adding input device HID-Compliant Mouse usb mouse with wheel (/dev/input/event3)
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: Applying InputClass "evdev keyboard catchall"
[    11.822] (II) Using input driver 'evdev' for 'HID-Compliant Mouse usb mouse with wheel'
[    11.822] (**) HID-Compliant Mouse usb mouse with wheel: always reports core events
[    11.822] (**) evdev: HID-Compliant Mouse usb mouse with wheel: Device: "/dev/input/event3"
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Vendor 0x1d57 Product 0x10
[    11.822] (--) evdev: HID-Compliant Mouse usb mouse with wheel: Found keys
[    11.822] (II) evdev: HID-Compliant Mouse usb mouse with wheel: Configuring as keyboard
[    11.822] (II) XINPUT: Adding extended input device "HID-Compliant Mouse usb mouse with wheel" (type: KEYBOARD, id 11)

```

Yes i have an usb keyboard, i will try to restart the system now to see if the mouse will continue to work or not

---

### Post by ivo_popov on 2014-04-24
it worked 2 times when i restardet the pc, when i shut i down and started it again it didtn, here are the outputs when only the not working mouse and the uxb keyboard are connected 
```

ivo@ivo-All-Series:~$ cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
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

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Eee PC WMI hotkeys"
P: Phys=eeepc-wmi/input0
S: Sysfs=/devices/platform/eeepc-wmi/input/input5
U: Uniq=
H: Handlers=rfkill kbd event2 
B: PROP=0
B: EV=100013
B: KEY=7e40000 0 800000000000 0 0 1400b00100000 300180001100800 e000000000000 2
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event3 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event4 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event5 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=11"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=0603 Product=00f2 Version=0110
N: Name="Novatek Ultra Flat Keyboard"
P: Phys=usb-0000:00:14.0-10/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/input/input17
U: Uniq=
H: Handlers=sysrq kbd event14 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0603 Product=00f2 Version=0110
N: Name="Novatek Ultra Flat Keyboard"
P: Phys=usb-0000:00:14.0-10/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.1/input/input18
U: Uniq=
H: Handlers=kbd event15 
B: PROP=0
B: EV=13
B: KEY=42bc00000000 f00 8000100000000001 40002040000 401878d800d408 1e000000000000 0
B: MSC=10

ivo@ivo-All-Series:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=01 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0603 ProdID=00f2 Rev=01.10
S:  Manufacturer=Novatek
S:  Product=Ultra Flat Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=350mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
ivo@ivo-All-Series:~$ grep -i mouse /var/log/xorg.0.log
grep: /var/log/xorg.0.log: No such file or directory
ivo@ivo-All-Series:~$ lsmod
Module                  Size  Used by
hid_a4tech             12651  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  3 hid_a4tech,hid_generic,usbhid
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
psmouse               102222  0 
serio_raw              13462  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82274  1 mei_me
lpc_ich                21080  0 
soundcore              12680  1 snd
fglrx                8085343  123 
amd_iommu_v2           19054  1 fglrx
parport_pc             32701  0 
ppdev                  17671  0 
video                  19476  1 asus_wmi
mac_hid                13205  0 
wmi                    19177  1 asus_wmi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

```

---

### Post by varunendra on 2014-04-24
Hmm.. with this kind of dodgy behaviour, I wonder if the mouse, or the USB port, or the mouse cable is malfunctioning.

Does the mouse 'Always' work on a different system?

---

### Post by ivo_popov on 2014-04-24
Yes the mouse always works in windows, never had a problem with it, strange thing. i have tried to put linux mint and fedora on a usb stick and then live boot from it and it didnt work in them too, so the problem probably isnt only in ubuntu.

---

### Post by ivo_popov on 2014-04-24
when isntalling ubuntu i didnt install any chipset drivers, only the graphic driver, can this somehow cause it?

---

### Post by varunendra on 2014-04-24
Chipset drivers are not required to be installed separately in Linux. Whatever part of it is necessary, is already available in the kernel.

But if none of the log files (Xorg.0.log, syslog, kern.log) give any hints when it goes missing, I don't know where to start looking for a clue.

As a shot in the dark, you may try these when it doesn't get recognized -
```
sudo modprobe -rv psmouse usbhid && sudo modprobe -v usbhid && sudo modprobe -v psmouse
```
IMPORTANT! The "modprobe -rv.." command would remove the "usbhid" driver due to which your keyboard may become non-functional. So it is important to supply the command to reload it in the same line (by appending it with "&&") so that the reloading is done automatically. (otherwise you won't be able to run the command to reload it without a working keyboard ;))

If anything goes wrong with the above command (e.g., keyboard gets stuck too), a reboot will fix it again.

Frankly, I've got no clues so far on what may be going wrong, and whatever I'm suggesting are just some wild guesses.

**PS:**
It is capital 'X' in "Xorg.0.log". Case of letters is very important in Linux!

---

### Post by Magdalena_Williams on 2014-05-06
using the latest released Logitech MX series,the [best wireless mouse]("http://bestwirelessmouse.biz/") may solved this problem

---

### Post by d-aravinthan on 2015-04-13
My laptop have Ubuntu 14.04 LTS. If USB optical mouse connect before ON / restart the system its work fine. But, after "ON" if connect the USB optical mouse, then it  is not work.In windows OS mouse works fine. Also, I have tried with another new mouse, the problem is same.

---

### Post by compaq4ml on 2015-04-13
I meet the same problem.
The wireless optical mouse doesn't work on HP CQ14 laptop with Ubuntu 14.04 LTS.
I have tried all the ways above but the problem still here.

---

