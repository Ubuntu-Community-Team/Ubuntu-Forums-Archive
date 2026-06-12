---
title: "diNovo Mini"
date: 2008-03-17
forum: General Help
---

### Post by hebetude on 2008-03-17
Yes, even knowing that new hardware isn't always supported by Ubuntu, but I just couldn't help myself.  So it seems about all the buttons work except the touchpad.  

I ran xev and nothing is registering when I use the touchpad.  I don't know the intrencies of the input methods, is there something special I can run to start doing debug on what this thing is sending in place of normal touchpad movements?

FYI, I have both a synaptic touchpad (laptop) and mouse configured in my X.  So, I should be able to pick up whatever it is sending I assume.

---

### Post by hebetude on 2008-03-17
from my dmesg
```

[  313.424674] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2.2/2-2.2:1.0/input/input9
[  313.478045] input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.1-2.2
[  313.490215] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input10
[  313.534954] input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.1-2.3
[  313.534974] usbcore: registered new interface driver usbhid
[  313.534978] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  933.746227] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[  933.746234] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.

```

---

### Post by hebetude on 2008-03-18
I finally retried doing a regular BT pairing with a cheapo BT dongle I bought.  Everything works perfectly!

Yay Hardy!  

p.s. the touchpad does not work with the included USB dongle, I imagine I can enter my PS3 passkey and pair both at the same time.  *shrug*

---

### Post by karmik on 2008-04-12
Woot. Are you stating that with the cheapo bluetooth dongle even the touchpad works? Please let me know, i'm interested in this niffy keyboard for my mediacenter too.

---

### Post by karmik on 2008-04-12
Woot. Are you stating that with the cheapo bluetooth dongle even the touchpad works? Please let me know, i'm interested in this niffy keyboard for my mediacenter too.

---

### Post by hebetude on 2008-04-13
Everything works with regular bluetooth, I couldn't get the touchpad to work with USB.  I haven't tried USB in a while I got one of those slim bluetooth receivers and use that instead.

---

### Post by Paqman on 2008-04-27
So is that a PCI Bluetooth card instead of a USB? :confused:

---

### Post by hebetude on 2008-04-28
usb bluetooth receiver, it comes with a usb receiver for computers w/o bluetooth

---

### Post by dlawson on 2008-04-29
I have recently bought the Dinovo Mini, and after a bit of trouble I managed to get it to work in Ubuntu. So here is some details that should hopefully help other people.

First some facts:

[LIST]
[*]The Dinovo Mini uses Bluetooth, and it comes with a USB dongle transceiver. You do not have to use the USB dongle if you have a Bluetooth module in your PC.
[*]When using the Dinovo Mini with the USB dongle, the keyboard works fine, but ** the touchpad does not work out of the box** (even in Hardy)
[*]When using the Dinovo mini with a Bluechip module built into your PC, **the keyboard and touchpad works fine** (assuming your built-in bluetooth transceiver is working)
[/LIST]

This means, **the problem is only with the USB dongle supplied with the keyboard**.

But, it is possible to get the touchpad working while using the USB dongle. I got the details from [http://home.att.net/~Tom.Horsley/mini.html]("http://home.att.net/~Tom.Horsley/mini.html") - awesome stuff, thanks Tom. All that is required is to add the following line to */etc/modprobe.d/options*,

```
options usbhid quirks=0x046d:0xc71f:0x00080000
```

---

### Post by debaser42 on 2008-05-05
i still can't get the touchpad to work. i modified the options file like suggested and re-paired the device (with the included usb dongle). Doesn't work. (i'm using hardy btw)

I also have an old bt dongle, but for some reason it doesn't want to pair with it.

I'd really appreciate any suggestions as I'm excited to get rid of the bulky keyboard that has been taking up my coffee table for quite a bit. However, I don't want to run Myth so having a touchpad is really the reason I bought this device in the first place.

---

### Post by hebetude on 2008-05-05
It's a bit tricky to pair bluetooth in ubuntu.  I would make sure the BT dongle doesn't work before trying to use the usb device.  BT works much better than the usb.  Be sure you go into the services tab and add the device to the approved list under the bluetooth manager.

---

### Post by dlawson on 2008-05-06
> **debaser42 said:**
> i still can't get the touchpad to work. i modified the options file like suggested and re-paired the device (with the included usb dongle). Doesn't work. (i'm using hardy btw)

I am using Hardy too BTW, and the fix I posted works with that for me - sorry it didn't work for you.

> **debaser42 said:**
> I'd really appreciate any suggestions as I'm excited to get rid of the bulky keyboard that has been taking up my coffee table for quite a bit. However, I don't want to run Myth so having a touchpad is really the reason I bought this device in the first place.

Yeh I know what you mean - that is the exact same reason I wanted it :).

I am no expert, but have you tried anything with your /etc/X11/xorg.conf file - in particular the "InputDevice" Section for your mouse. If the problem is in here, it might explain why you can't get either BT or USB to work. This is what I have,

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection
```

Best of luck.

---

### Post by electronikjunkie on 2008-05-07
i just plugged mine in and it worked. didn't do anything special at all. running fiesty.

---

### Post by medions on 2008-05-08
Hi debaser42,

Do you still got the problem, or did you find a solution? - Coz i'm having the exact same problems as you had! - I just can't get the mouse working?!

---

### Post by trouble1313 on 2008-05-08
Same issue here. Trackpad is not working even with the kernel option. I took a look in usbhid-quirks.c and don't even see the device in there.

-Trouble

---

### Post by debaser42 on 2008-05-09
I have had some other issues with my HTPC and Hardy so I've gone back to Gutsy. I'm going to try out the xorg config after I get this back up as well as a few other things. So far its the same on Gutsy (keyboard is instant but mouse pointer isn't responding
). I'll post results.

---

### Post by Dionikon on 2008-05-16
I briefly had my mini working 100%.

Then after rebooting my system it doesn't anymore.

I added the extra line to the options file as in the post above, then before rebooting unplugged my normal wireless (2.4G) mouse and restarted the system.

Very strange.

The keyboard works perfectly, just not the track pad.

---

### Post by sugspace on 2008-05-26
i had mine working 100% as well until i installed the latest updates 3 days ago.

---

### Post by evilash00 on 2008-05-31
> **dlawson said:**
> I have recently bought the Dinovo Mini, and after a bit of trouble I managed to get it to work in Ubuntu. So here is some details that should hopefully help other people.

First some facts:

[LIST]
[*]The Dinovo Mini uses Bluetooth, and it comes with a USB dongle transceiver. You do not have to use the USB dongle if you have a Bluetooth module in your PC.
[*]When using the Dinovo Mini with the USB dongle, the keyboard works fine, but ** the touchpad does not work out of the box** (even in Hardy)
[*]When using the Dinovo mini with a Bluechip module built into your PC, **the keyboard and touchpad works fine** (assuming your built-in bluetooth transceiver is working)
[/LIST]

This means, **the problem is only with the USB dongle supplied with the keyboard**.

But, it is possible to get the touchpad working while using the USB dongle. I got the details from [http://home.att.net/~Tom.Horsley/mini.html]("http://home.att.net/~Tom.Horsley/mini.html") - awesome stuff, thanks Tom. All that is required is to add the following line to */etc/modprobe.d/options*,

```
options usbhid quirks=0x046d:0xc71f:0x00080000
```

wenever i put this code in the kboot prompt. it tells me it is not found. can someone help me? i really want to get this touccpad working. i just need the exact code to put in and exactly the way you need to put it in(ex.: do you really need to put that comma after options in the code?)

---

### Post by abarbaccia on 2008-06-03
So I have it working in a base hardy install with a few modifications. 

Add the following line to */etc/modprobe.d/options*
```
options usbhid quirks=0x046d:0xc71f:0x00080000
```

Once booted into your desktop, reload the usbhid module
```
sudo rmmod usbhid
sudo modprobe usbhid
```

Enjoy your mouse pointer.

I'm still trying to figure out why this is happening. More testing is needed before filing to Launchpad. 

Anyone know a way of having the modules reload automatically after login?

Please help so we can find a *working* solution for Hardy b/c the patch for this is not going to be seen until Ibex.

---

### Post by abarbaccia on 2008-06-04
Update:

Apparently the reason why usbhid is not loading with the correct options at boot is because its being called by the initramfs.

To update your initramfs with the new module options use the following code:
```
sudo update-initramfs -u
```

Not tested but should work.

Cred to Tom for pointing me in the direction of initrd!

---

### Post by Ultimadlamer on 2008-06-06
> **abarbaccia said:**
> Update:

Apparently the reason why usbhid is not loading with the correct options at boot is because its being called by the initramfs.

To update your initramfs with the new module options use the following code:
```
sudo update-initramfs -u
```

Not tested but should work.

Cred to Tom for pointing me in the direction of initrd!

It seems to work.  I'm typing this on mine now.  The mouse works even after 2 restarts.

```

sudo rmmod usbhid
```

Do NOT type this if your other keyboard/mouse is USB too!  	#-o

---

### Post by lymz on 2008-06-19
> **abarbaccia said:**
> Add the following line to */etc/modprobe.d/options*
```
options usbhid quirks=0x046d:0xc71f:0x00080000
```

Once booted into your desktop, reload the usbhid module

I didn't need to reboot.

> **abarbaccia said:**
> ```
sudo rmmod usbhid
```

As noted by Ultimadlamer, my other keyboard/mouse was also usb.  I had to unplug and plug it back, it seemed to pick them up again without further commands.

> **abarbaccia said:**
> To update your initramfs with the new module options use the following code:
```
sudo update-initramfs -u
```

After a reboot the mouse still worked (I tried without this and had to reload usbhid module again).  By the way I am on mythbuntu 8.04.

---

### Post by Sharebear on 2008-06-25
:-( All these success stories aren't making me too happy.

I've just bought the Danish/Norwegian version of the diNovo mini and like many others found that with the provided dongle the keyboard works fine but the trackpad does not.

I tried adding the suggested quirk to the modprobe options but this appears to have no effect.

If I try and connect it with a normal bluetooth dongle then moving the mouse pointer appears to work fine, although trying to click the mouse does not. If I change the mode of the trackpad to the directional/home-media mode, it seems to then send a continuous stream of evente to my terminal, either scrolling fast through my bash history or doing something that causes my terminal to beep continuously.

Anyone have some good advice on how to debug this?

As a side note, if I connect it to my MacBook the whole laptop becomes unresponsive until I turn off the diNovo, so I assume it's flooding something with events there too.

Any help appreciated.

Jon

---

### Post by /tilt/ on 2008-06-28
Thanks to the posts on this thread the mouse on my diNovo mini is now functional. This is on Hardy Heron 8.04.

Added the following to /etc/modprobe.d/options

# diNovo Mini Keyboard USB Dongle Fix
options usbhid quirks=0x046d:0xc71f:0x00080000

Then issued: 
sudo update-initramfs -u

Works perfectly and the settings keep.

THANKS!! :P

---

