---
title: "Sound on Asus sonicmaster subwoofer."
date: 2018-03-10
forum: General Help
---

### Post by Joao Lacerda on 2018-03-10
Hi friends!
I need some help here:

Ubuntu 16.04 - AsusTek ET2701I-w8

Asus sonicmaster subwoofer is not working in conjunction with the internal speakers.

The output for thesubwoofer was not enable by default.
Then I have used the(hadjackretask) and enabled it:

Black Line Out, Rearside 
Pin ID: 0x1a
internal speaker(LFE )

And it worked fine, I have sound on the subwoofer, but the internal speakers are mute now.

Some Info that maybe will help you help me :p

```
lspci -v | grep -A7 -i "audio"
 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 39
    Memory at f7a00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
```
And
```
aplay -l

**** List ofPLAYBACK Hardware Devices ****
card 0: PCH [HDAIntel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0:subdevice #0
card 0: PCH [HDAIntel PCH], device 1: ALC8  87-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0:subdevice #0 


```
 
Thank you for your time.

---

### Post by Joao Lacerda on 2018-03-10
For the first time no one is helping me ! :(

But I have found a solution, now it works fine internal speakers plus the subwoofer. :D

it worked for me.
Maybe it will help some else: 

Install HDAJackRetask

sudo apt-get install alsa-tools-guitype on the terminal

hdajackretask


see the image below

[ATTACH=CONFIG]278886[/ATTACH]
click apply now
install boot override
reboot the system

Then Change the default sound settings.
Analog Surround  5.1 output

---

### Post by klundermann on 2018-05-22
I have the same problem, but I have a problem using the solution suggested above.  I make the changes in  hdajackreset , click "Apply Now" and, when prompted, enter my password.  Then I get the error message "tee: /sys/clas/sound/hwC1D0/reconfig: Device or resource busy".

Would anyone have any idea what the problem is?

---

