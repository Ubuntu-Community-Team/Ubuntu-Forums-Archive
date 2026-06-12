---
title: "Touchpad doesn't work after update to Ubuntu 16.04"
date: 2017-05-08
forum: General Help
---

### Post by phoenixofstorm on 2017-05-08
Hi all,
Yesterday I decided to update my Ubuntu 12.04. At first I upgraded to 14.04. That is when I lost my touchpad. That is why I decided to upgrade further to 16.04. Still, the touchpad didn't work. So I updated the kernel to 4.8.0-51-lowlatency - it didn't help. 
The weird part is that it isn't even listed in /proc/bus/input/devices. Here's what i get:
```
I: Bus=0019 Vendor=0000 Product=0005 Version=0000N: Name="Lid Switch"
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


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:25/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=abba
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event5 leds 
B: PROP=0
B: EV=120013
B: KEY=20000 20 0 0 1500f02140003 3803078f900d401 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP Wireless hotkeys"
P: Phys=hpq6001/input0
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=3
B: KEY=80000000000000 0 0 0


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input10
U: Uniq=
H: Handlers=event6 js0 
B: PROP=0
B: EV=9
B: ABS=7


I: Bus=0003 Vendor=064e Product=9302 Version=0102
N: Name="HP Truevision HD"
P: Phys=usb-0000:00:14.0-9/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/input/input11
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input12
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input13
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input14
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input15
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input16
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input17
U: Uniq=
H: Handlers=kbd event14 
B: PROP=0
B: EV=33
B: KEY=4000000000 0 1000700000000 2102400 0 0
B: MSC=10
B: SW=22


I: Bus=0003 Vendor=0000 Product=0538 Version=0111
N: Name=" USB OPTICAL MOUSE"
P: Phys=usb-0000:00:14.0-6/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/0003:0000:0538.0001/input/input18
U: Uniq=
H: Handlers=mouse0 event15 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10



```

When i do xinput --list i get
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=12    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=13    [slave  keyboard (3)]
```

I tried reinstalling xserver-xorg-input-synaptics to no avail. Also I did some manual configurations for grub which also didn't help. Last but not least - the touchpad used to work fine in 12.04.
The laptop in question is HP Pavilion 15.
Any help would be greatly appreciated!

---

### Post by phoenixofstorm on 2017-05-09
I solved it myself. The problem was in the synaptics-touchpad package, which came pre-installed on my 12.04. So for all of you HP owners out there - after upgrading your system you should go and
```
sudo apt-get purge synaptics-touchpad
```
and than
```
sudo apt-get install --reinstall xserver-xorg-input-synaptics
```

After this reboot and everything should work fine.

---

