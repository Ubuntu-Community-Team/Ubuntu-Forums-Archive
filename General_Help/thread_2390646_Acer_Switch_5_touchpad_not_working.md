---
title: "Acer Switch 5 touchpad not working"
date: 2018-04-30
forum: General Help
---

### Post by eclipse182 on 2018-04-30
Hi guys! I always wanted to try linux. I tried to install the latest version of linux mint and ubuntu, but i cant get the touchpad to work.
I tried almost everything, now im just trying ubuntu on a live boot cd, but the system doesn't recognize my touchpad. This computer is a 2-1, so probably the so recognize as a tablet and not a laptop. My attached keyboard has touchpad in it.

Can someone help me please??

---

### Post by mörgæs on 2018-05-01
Hi, welcome to the fora.

People who know about this area, which I don't, often request the output from ```
xinput list
``` Please post it in CODE tags.

---

### Post by eclipse182 on 2018-05-01
Thank you for your reply

xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Chicony ACER Tablet Keyboard            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ELAN5515:00 04F3:22F0                   	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; Chicony ACER Tablet Keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Chicony ACER Tablet Keyboard            	id=19	[slave  keyboard (3)]
    &#8627; ELAN5515:00 04F3:22F0 Pen               	id=15	[slave  keyboard (3)]
    &#8627; USB Camera: USB Camera                  	id=13	[slave  keyboard (3)]
    &#8627; Intel Virtual Button driver             	id=16	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=17	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys 
```

---

### Post by cruzer001 on 2018-05-01
Hello

There is a reference to Elantech in that output, but nothing about a touchpad.  Is the touchpad turned on?

[https://community.acer.com/en/discussion/77457/touchpad-not-working](https://community.acer.com/en/discussion/77457/touchpad-not-working)

Possibly changing the boot parameter would do it adding "i8042.nomux=1" and/or "i8042.reset" to /etc/default/grub.

line:
GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"
or
GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux=1 i8042.reset quiet splash"

[https://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu](https://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu)
[https://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux](https://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux)
[https://ubuntuforums.org/showthread.php?t=2020719](https://ubuntuforums.org/showthread.php?t=2020719)
more here
[https://www.google.com/search?client=ubuntu&hs=ylC&channel=fs&biw=1067&bih=549&ei=32DoWvfBEsvAjwPtsangDg&q=acer+elantech+touchpad+linux+ubuntu&oq=acer+elantech+touchpad+linux+ubuntu&gs_l=psy-ab.12...33240.35946.0.42446.4.4.0.0.0.0.142.530.0j4.4.0....0...1..64.psy-ab..0.3.418...33i10k1j35i39k1.0.kHVpZ4nvYRE](https://www.google.com/search?client=ubuntu&hs=ylC&channel=fs&biw=1067&bih=549&ei=32DoWvfBEsvAjwPtsangDg&q=acer+elantech+touchpad+linux+ubuntu&oq=acer+elantech+touchpad+linux+ubuntu&gs_l=psy-ab.12...33240.35946.0.42446.4.4.0.0.0.0.142.530.0j4.4.0....0...1..64.psy-ab..0.3.418...33i10k1j35i39k1.0.kHVpZ4nvYRE)

I do not own an Acer, this is just my findings.  Give your thread some time and maybe a Acer person will show up :)

---

### Post by eclipse182 on 2018-05-02
Hello! I tried to do that, but i could't get it. Still not working, so any other suggestion?

---

### Post by cruzer001 on 2018-05-02
Does the kernel see a touchpad?

```
cat /proc/bus/input/devices
```

---

### Post by eclipse182 on 2018-05-02
Well I think the kernel doesn't recognize my touchpad, just recognize my keyboard and my pen stylus.
The touchpad is in the keyboard.

(I don't know how to put the code in a envelope, can someone teach me?)

```
 I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input3
U: Uniq=
H: Handlers=event3 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 leds 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3802078f870f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=06cb Product=81a7 Version=0111
N: Name="Chicony ACER Tablet Keyboard"
P: Phys=usb-0000:00:14.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:06CB:81A7.0001/input/input6
U: Uniq=
H: Handlers=sysrq kbd event6 leds 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=06cb Product=81a7 Version=0111
N: Name="Chicony ACER Tablet Keyboard"
P: Phys=usb-0000:00:14.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/0003:06CB:81A7.0002/input/input8
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=1f
B: KEY=3f0003007f 0 0 483ffff17aff32d bf54444600000000 1 930f938b17c000 677bfad941dfed 9ed68000004400 10000002
B: REL=40
B: ABS=ffffff0100000000
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Intel Virtual Button driver"
P: Phys=
S: Sysfs=/devices/platform/INT33D6:00/input/input10
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=13
B: KEY=1000000000000 0 1c000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input11
U: Uniq=
H: Handlers=rfkill kbd event10 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 1600800000c00 300000 0 0
B: MSC=10

I: Bus=0003 Vendor=0bda Product=56c1 Version=0019
N: Name="USB Camera: USB Camera"
P: Phys=usb-0000:00:14.0-7/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input12
U: Uniq=
H: Handlers=kbd event11 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
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

I: Bus=0018 Vendor=04f3 Product=22f0 Version=0100
N: Name="ELAN5515:00 04F3:22F0"
P: Phys=i2c-ELAN5515:00
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-6/i2c-ELAN5515:00/0018:04F3:22F0.0008/input/input19
U: Uniq=
H: Handlers=mouse0 event18 
B: PROP=2
B: EV=1b
B: KEY=400 0 0 0 0 0
B: ABS=3273800000000003
B: MSC=20

I: Bus=0018 Vendor=04f3 Product=22f0 Version=0100
N: Name="ELAN5515:00 04F3:22F0 Pen"
P: Phys=i2c-ELAN5515:00
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-6/i2c-ELAN5515:00/0018:04F3:22F0.0008/input/input22
U: Uniq=
H: Handlers=mouse1 event19 
B: PROP=0
B: EV=1b
B: KEY=c03 0 0 0 0 0
B: ABS=1000003
B: MSC=10 
```

---

### Post by cruzer001 on 2018-05-02
Again no direct reference to a touchpad so I went back to the Acer community and dug around so more.

Got a direct hit on the same model and same problem

[https://community.acer.com/en/discussion/542762/acer-switch-5-linux-mint-touchpad-not-working](https://community.acer.com/en/discussion/542762/acer-switch-5-linux-mint-touchpad-not-working)

with no solution.  May even be your thread.  Sorry, I have no further suggestions.

---

### Post by eclipse182 on 2018-05-02
Well, yeah the kernel just made a reference to elantech. That's the port of my stylus pen. So the kernel just recognize my keyboard and my stylus pen not the touchpad.
That thread is mine, I got no luck in Acer forums.
Thank you for your help, I'll keep investigating.

---

### Post by resilience1 on 2018-12-19
Hi all, 
I have the same problem and I have tried to follow different directions. I hope it will be solved soon since i would like to use ubuntu on that model of Acer. 
Thank you

---

