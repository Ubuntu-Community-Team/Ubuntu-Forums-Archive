---
title: "Touchpad stops working after login"
date: 2021-01-14
forum: General Help
---

### Post by robehickman on 2021-01-14
(provisionally solved, see edits)

Hi,

The touchpad on my Asus VivoBook used to work fine, however after installing updated packages through apt, it stopped working after login, yet works fine on the login screen.  After logging in the pointer snaps to the bottom right of the screen and won't move unless I connect an external mouse.

xinput shows this:

```

xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=8    [slave  pointer  (2)]
&#9116;   &#8627; ASUE1201:00 04F3:3125 Mouse                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; ASUE1201:00 04F3:3125 Touchpad              id=11    [slave  pointer  (2)]

```

cat /proc/bus/input/devices

```

I: Bus=0018 Vendor=04f3 Product=3125 Version=0100
N: Name="ASUE1201:00 04F3:3125 Mouse"
P: Phys=i2c-ASUE1201:00
S: Sysfs=/devices/platform/AMDI0010:03/i2c-0/i2c-ASUE1201:00/0018:04F3:3125.0001/input/input7
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=1943
B: MSC=10

I: Bus=0018 Vendor=04f3 Product=3125 Version=0100
N: Name="ASUE1201:00 04F3:3125 Touchpad"
P: Phys=i2c-ASUE1201:00
S: Sysfs=/devices/platform/AMDI0010:03/i2c-0/i2c-ASUE1201:00/0018:04F3:3125.0001/input/input8
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20

```

-------- edit ------------

I was just looking through the system settings panel and found that 'touchpad' under 'mouse and touchpad' was disabled for some reason, though I never touched that setting myself. Just want to try logging out to see if it happens again.


-------- edit ------------

Touchpad remains working after logging off and logging in again, and also after a full reboot. I guess something in the updates lead to the touchpad being disabled in the settings, though I have no idea why.

---

