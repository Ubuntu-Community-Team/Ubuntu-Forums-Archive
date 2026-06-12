---
title: "iPod Touch Freezes User Input on 10.04"
date: 2012-12-08
forum: General Help
---

### Post by jamesisin on 2012-12-08
I am running Ubu 10.04 on an old PPC Mac.  I just received a new iPod Touch.  If I attach that Touch to the Ubu system mouse and keyboard input freeze (usually even after unattaching the iPod).

I am able to, for instance, login and start top in a terminal.  Then I can attach the iPod and freeze input, but there is still output running through top.  I ought to be able to take advantage of this to troubleshoot the matter.

I didn't see anything running in top which would certainly be an issue, but I'm also not sure what might be possibly an issue.  (Obviously I can rule out X, gnome-termainl, and top.  Nothing has more than 4% (X) of the proc.)

Any suggestions?

---

### Post by Kirk Schnable on 2012-12-08
Have you tried tailing your syslog or dmesg while plugging the iPod in?  This might expose a driver or kernel difficulty which wouldn't be obvious to you in the output of top. 

What I am suggesting is something along the lines of...

1. Start with iPod unplugged. 
2. In a TTY or terminal, run **tail -f /var/log/syslog /var/log/dmesg**
3. Plug in the iPod and look for obvious errors.

---

### Post by jamesisin on 2012-12-08
Thanks.

From syslog I get a few items (nothing from dmesg):

```

Dec 8 11:55:05 [machinename] AptDaemon: INFO: Initializing daemon
Dec 8 11:55:05 [machinename] kernel: [  102.132211] usb 5-2: USB disconnect, address 2
Dec 8 11:55:05 [machinename] kernel: [  102.132216] usb 5-2.1: USB disconnect, address 3
Dec 8 11:55:05 [machinename] kernel: [  102.179312] usb 5-2.3: USB disconnect, address 4
Dec 8 11:55:06 [machinename] kernel: [  102.936542] usb 4-1: USB disconnect, address 2
Dec 8 12:00:06 [machinename] AptDaemon: INFO: Quiting due to inactivity
Dec 8 12:00:06 [machinename] AptDaemon: INFO: Shutdown was requested

```

Is it trying to install something?

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> Is it trying to install something?

My hunch is no...
[http://ubuntuforums.org/showthread.php?t=1935775](http://ubuntuforums.org/showthread.php?t=1935775)

---

### Post by jamesisin on 2012-12-08
Yeah, I ran those commands again and that Apt portion seems to be part of something which runs perhaps every login event.

The USB stuff seems more interesting.  It's possible that the USB keyboard and mouse are getting shafted when the iPod connects.  Is it possible to look more into what's happening surrounding USB here?

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> Yeah, I ran those commands again and that Apt portion seems to be part of something which runs perhaps every login event.

The USB stuff seems more interesting.  It's possible that the USB keyboard and mouse are getting shafted when the iPod connects.  Is it possible to look more into what's happening surrounding USB here?

Anything's possible. :P

It's worth a look. You can use **lsusb** to see what USB devices your system is recognizing. You can make the output fairly real time by "watching" it. 

```
watch lsusb
```

---

### Post by jamesisin on 2012-12-08
Thanks for the additional command.  I'll try it out momentarily.

I picked up my laptop (also running Ubu 10.04 but with Intel 32 bit arch) and tried all three.  This is what I get in syslog (this machine does not freeze but does not mount the iPod either):

```

Dec  8 16:37:51 [machinename] kernel: [  639.016107] hub 3-0:1.0: over-current change on port 1
Dec  8 16:37:51 [machinename] kernel: [  639.120056] hub 2-0:1.0: over-current change on port 1

```

Nothing from dmesg nor watch lsusb.

---

### Post by jamesisin on 2012-12-08
I'm pretty convinced the iPod is causing everything USB to flop.  I attached a USB keyboard to this laptop.  It showed up under watch lsusb.  When I attached the iPod it vanished and lost functionality.

One question of use is, can I restart USB without restarting the machine (say, using a command via ssh)?  (This would prevent me from hard-restarting the machine after each test.)

Of course the larger question remains: how can I get this iPod to function as expected?

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> Thanks for the additional command.  I'll try it out momentarily.

I picked up my laptop (also running Ubu 10.04 but with Intel 32 bit arch) and tried all three.  This is what I get in syslog (this machine does not freeze but does not mount the iPod either):

```

Dec  8 16:37:51 [machinename] kernel: [  639.016107] hub 3-0:1.0: over-current change on port 1
Dec  8 16:37:51 [machinename] kernel: [  639.120056] hub 2-0:1.0: over-current change on port 1

```

Nothing from dmesg nor watch lsusb.

The over-current error probably means your iPod is trying to draw more electricity than the USB bus on your laptop is designed to supply. (Or the combination of the iPod and the other USB devices on the same bus is too much power draw).

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> I'm pretty convinced the iPod is causing everything USB to flop.  I attached a USB keyboard to this laptop.  It showed up under watch lsusb.  When I attached the iPod it vanished and lost functionality.

Is it possible that there's something wrong with your iPod or charge cable? Maybe your USB bus is shorting out when you're plugging it in?

Does the iPod charge with the same cable on other computers or a wall charger, etc?

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> One question of use is, can I restart USB without restarting the machine (say, using a command via ssh)?  (This would prevent me from hard-restarting the machine after each test.)

According to this: [http://queleimporta.com/como-re-iniciar-el-subsistema-usb-en-ubuntu/](http://queleimporta.com/como-re-iniciar-el-subsistema-usb-en-ubuntu/)

Running this command will restart your USB subsystem without rebooting. 
(I haven't tested it, but it sounds like it's in the right ballpark, and the command isn't dangerous.)
```
sudo /etc/init.d/udev restart
```

---

### Post by jamesisin on 2012-12-08
As of this moment unattaching the iPod reattaches the other USB devices.  Not clear why it's changed.  [shrugs]

Here is some (perhaps more useful) output from syslog:

```

Dec  8 16:54:59 [machinename] kernel: [  691.084864] usb 5-2: USB disconnect, address 8
Dec  8 16:54:59 [machinename] kernel: [  691.084870] usb 5-2.1: USB disconnect, address 9
Dec  8 16:54:59 [machinename] kernel: [  691.144760] usb 5-2.3: USB disconnect, address 10
Dec  8 16:55:00 [machinename] kernel: [  691.900282] hub 1-0:1.0: over-current change on port 1
Dec  8 16:55:00 [machinename] kernel: [  692.004282] hub 1-0:1.0: over-current change on port 2
Dec  8 16:55:00 [machinename] kernel: [  692.108264] hub 1-0:1.0: over-current change on port 3
Dec  8 16:55:00 [machinename] kernel: [  692.212279] hub 1-0:1.0: over-current change on port 4
Dec  8 16:55:00 [machinename] kernel: [  692.316265] hub 1-0:1.0: over-current change on port 5
Dec  8 16:55:00 [machinename] kernel: [  692.420275] usb 4-1: USB disconnect, address 4
Dec  8 16:55:11 [machinename] kernel: [  703.155179] hub 1-0:1.0: over-current change on port 1
Dec  8 16:55:11 [machinename] kernel: [  703.256269] hub 1-0:1.0: over-current change on port 2
Dec  8 16:55:11 [machinename] kernel: [  703.360262] hub 1-0:1.0: over-current change on port 3
Dec  8 16:55:11 [machinename] kernel: [  703.464300] hub 1-0:1.0: over-current change on port 4
Dec  8 16:55:12 [machinename] kernel: [  703.808285] hub 1-0:1.0: over-current change on port 5
Dec  8 16:55:13 [machinename] kernel: [  704.824260] usb 5-2: new full speed USB device using ohci_hcd and address 11
Dec  8 16:55:13 [machinename] kernel: [  705.036523] usb 5-2: configuration #1 chosen from 1 choice
Dec  8 16:55:13 [machinename] kernel: [  705.045633] hub 5-2:1.0: USB hub found
Dec  8 16:55:13 [machinename] kernel: [  705.048373] hub 5-2:1.0: 3 ports detected
Dec  8 16:55:14 [machinename] kernel: [  706.216254] usb 4-1: new full speed USB device using ohci_hcd and address 5
Dec  8 16:55:14 [machinename] kernel: [  706.428716] usb 4-1: configuration #1 chosen from 1 choice
Dec  8 16:55:14 [machinename] kernel: [  706.510028] input: Burr-Brown from TI               USB Audio DAC    as /devices/pci0001:00/0001:00:02.0/0001:05:0b.0/usb4/4-1/4-1:1.2/input/input14
Dec  8 16:55:14 [machinename] kernel: [  706.510221] generic-usb 0003:08BB:2706.000D: input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI               USB Audio DAC   ] on usb-0001:05:0b.0-1/input2
Dec  8 16:55:15 [machinename] kernel: [  706.592356] usb 5-2.1: new full speed USB device using ohci_hcd and address 12
Dec  8 16:55:15 [machinename] kernel: [  706.713642] usb 5-2.1: configuration #1 chosen from 1 choice
Dec  8 16:55:15 [machinename] kernel: [  706.728957] input: NMB Dell USB 7HK Keyboard as /devices/pci0001:00/0001:00:02.0/0001:05:0b.1/usb5/5-2/5-2.1/5-2.1:1.0/input/input15
Dec  8 16:55:15 [machinename] kernel: [  706.729201] generic-usb 0003:413C:2001.000E: input,hidraw1: USB HID v1.00 Keyboard [NMB Dell USB 7HK Keyboard] on usb-0001:05:0b.1-2.1/input0
Dec  8 16:55:15 [machinename] kernel: [  706.741635] input: NMB Dell USB 7HK Keyboard as /devices/pci0001:00/0001:00:02.0/0001:05:0b.1/usb5/5-2/5-2.1/5-2.1:1.1/input/input16
Dec  8 16:55:15 [machinename] kernel: [  706.741974] generic-usb 0003:413C:2001.000F: input,hiddev96,hidraw2: USB HID v1.00 Device [NMB Dell USB 7HK Keyboard] on usb-0001:05:0b.1-2.1/input1
Dec  8 16:55:15 [machinename] pulseaudio[1379]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Dec  8 16:55:15 [machinename] pulseaudio[1379]: ratelimit.c: 15 events suppressed
Dec  8 16:55:15 [machinename] kernel: [  706.829328] usb 5-2.3: new low speed USB device using ohci_hcd and address 13
Dec  8 16:55:15 [machinename] kernel: [  706.943631] usb 5-2.3: configuration #1 chosen from 1 choice
Dec  8 16:55:15 [machinename] kernel: [  706.953815] input: Kensington Kensington USB/PS2 Orbit as /devices/pci0001:00/0001:00:02.0/0001:05:0b.1/usb5/5-2/5-2.3/5-2.3:1.0/input/input17
Dec  8 16:55:15 [machinename] kernel: [  706.954092] generic-usb 0003:047D:1003.0010: input,hidraw3: USB HID v1.00 Mouse [Kensington Kensington USB/PS2 Orbit] on usb-0001:05:0b.1-2.3/input0

```

Not much of interest from lsusb beyond that the devices vanish and then reappear.

---

### Post by jamesisin on 2012-12-08
This iPod is brand new.  I can try attaching it to some other gear as well.

(Could you edit your previous post and remove my machine name.  Thanks.)

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> This iPod is brand new.  I can try attaching it to some other gear as well.
Hmm. Please do try it on other equipment anyway if possible. Car chargers, wall USB chargers, or other computers... I have a 4th Generation iPod Touch and I have never had difficulty with plugging it in to my Ubuntu machines. 

> **jamesisin said:**
> (Could you edit your previous post and remove my machine name.  Thanks.)
I believe I already did, unless I missed one.

---

### Post by jamesisin on 2012-12-08
I attached it to a MacBook:

```
USB Over Current Notice
A USB device is currently drawing too much power.
The hub to which it is attached will be deactivated.
```

Ouch.  Presumably be taking that one back.  I'll check Google after dinner.

---

### Post by Kirk Schnable on 2012-12-08
> **jamesisin said:**
> I attached it to a MacBook:

```
USB Over Current Notice
A USB device is currently drawing too much power.
The hub to which it is attached will be deactivated.
```

Ouch.  Presumably be taking that one back.  I'll check Google after dinner.

Weird. If you have a friend with an iPod, iPhone, or iPad try using their charge cable. It could just be a faulty connection with your cable.  (Not necessarily affecting the iPod itself).

---

### Post by jamesisin on 2012-12-09
Apple Store replaced the cable.  All's good.  Thanks for helping.

---

### Post by Kirk Schnable on 2012-12-10
> **jamesisin said:**
> Apple Store replaced the cable.  All's good.  Thanks for helping.

Anytime, glad you got this sorted out!

---

### Post by jamesisin on 2012-12-13
Well, "sorted" may be premature.

[http://ubuntuforums.org/showthread.php?p=12402087](http://ubuntuforums.org/showthread.php?p=12402087)

I don't know how far I want to go down this rabbit hole.  There are plenty of FLAC friendly portable music players out there.

---

