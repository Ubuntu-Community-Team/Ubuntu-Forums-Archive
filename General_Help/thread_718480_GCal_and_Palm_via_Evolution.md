---
title: "GCal and Palm via Evolution"
date: 2008-03-08
forum: General Help
---

### Post by teilnehmer on 2008-03-08
Okay, 

I'd like to share some insights I had when trying to synchronize my Google Calendar with my Zire 72. 

I now use **ScheduleWorld** to get my Google Calendars into my Evolution. Each GCal-Calendar corresponds with one calendar in ScheduleWorld, which corresponds to 1 calendar in Evolution. I have yet to work out how to sync both with my Palm...
Documentation for ScheduleWorld <-> Evolution is allright. Getting things working between Evolution (using gnome-pilot) and my Palm (Zire 72) was a lot harder. I assume you, as well, have searched a lot if you found this. 
Unfortunately, I can't reproduce all the steps I made (was a bit messy, all in all), but I'll try to describe some cornerstones.
Here are some tips:

**Gnome-Pilot** worked out in the end. It's the default solution with evolution (and should be accessible in Evolution by clicking Edit > Synchronization Options - if not, get gnome-pilot), and it does work. There were three things that might have prevented it from imnmediately working on my machine: 
(a) At one point, I had KPilot running as well. Possibly the 2 daemons fight each other. 
(b) I was using "usb:" instead of "/ttyUSB0", which I use now. "usb:" works without the visor module, but didn't work out in the end. Try both on your machine.
(c) I didn't have the Visor module activated. After typing "sudo modprobe visor" to activate the module, /ttyUSB1 worked fine. This was also viewable in /var/log/messages, where before the OS registered some USB device, but didn't see it being a Palm (see below).
* What irritated me was that I didn't know if the Gnome-Pilot did anything or was active. Pressing "Strg+Esc" showed me "gpilotd" was there. That's the daemon listening for incoming connections. Pressing "HotSync" on your Palm should set this off. If it doesn't, go Troubleshooting. 

Some troubleshooting tips:
Connect via USB and start HotSync on your Palm. After that, enter "dmesg" in the shell, which will show you debugging information. Alternatively, see /var/log/messages. 
You would want something like: 
```
[ 8298.652000] visor 2-2.2:1.0: Handspring Visor / Palm OS converter detected
[ 8298.652000] usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
[ 8298.652000] usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1

```

If you only get something like this, Visor is not enabled:
```
[ 4826.352000] usb 2-2.2: new full speed USB device using ehci_hcd and address 6
[ 4826.444000] usb 2-2.2: configuration #1 chosen from 1 choice
[ 4957.216000] usb 2-2.2: USB disconnect, address 6
```

Type "sudo modprobe visor" to start that module. If that helps, put visor in your /etc/modules
That's as far as I got. I'll post new insights if I have any. I hope this helps someone. !

:), 

Jan

---

### Post by teilnehmer on 2008-03-08
Update: Hach, I thought I had it. It worked once, but now it's off again. 
The difference is this:
The output when it's working:
```

Mar  8 12:39:10 holly2 kernel: [ 8288.040000] usbcore: registered new interface driver usbserial
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] usbcore: registered new interface driver usbserial_generic
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] usbcore: registered new interface driver visor
Mar  8 12:39:10 holly2 kernel: [ 8288.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Mar  8 12:39:17 holly2 kernel: [ 8294.956000] usb 2-2.2: new full speed USB device using ehci_hcd and address 19
Mar  8 12:39:17 holly2 kernel: [ 8295.048000] usb 2-2.2: configuration #1 chosen from 1 choice
Mar  8 12:39:17 holly2 kernel: [ 8295.048000] visor 2-2.2:1.0: Handspring Visor / Palm OS converter detected
Mar  8 12:39:17 holly2 kernel: [ 8295.048000] usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Mar  8 12:39:17 holly2 kernel: [ 8295.048000] usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Mar  8 12:39:20 holly2 kernel: [ 8298.104000] usb 2-2.2: USB disconnect, address 19
Mar  8 12:39:20 holly2 kernel: [ 8298.104000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Mar  8 12:39:20 holly2 kernel: [ 8298.104000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1

```

Now that it's not working, I get this (note: usb 1-2-2 instead of 2-2-2):
```

Mar  8 14:21:02 holly2 kernel: [   91.704000] usbcore: registered new interface driver usbserial
Mar  8 14:21:02 holly2 kernel: [   91.704000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Mar  8 14:21:02 holly2 kernel: [   91.704000] usbcore: registered new interface driver usbserial_generic
Mar  8 14:21:02 holly2 kernel: [   91.704000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Mar  8 14:21:02 holly2 kernel: [   91.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Mar  8 14:21:02 holly2 kernel: [   91.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Mar  8 14:21:02 holly2 kernel: [   91.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Mar  8 14:21:02 holly2 kernel: [   91.708000] usbcore: registered new interface driver visor
Mar  8 14:21:02 holly2 kernel: [   91.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Mar  8 14:21:49 holly2 kernel: [  139.036000] usb 1-2.2: new full speed USB device using ehci_hcd and address 4
Mar  8 14:21:49 holly2 kernel: [  139.128000] usb 1-2.2: configuration #1 chosen from 1 choice
Mar  8 14:21:49 holly2 kernel: [  139.128000] visor 1-2.2:1.0: Handspring Visor / Palm OS converter detected
Mar  8 14:21:49 holly2 kernel: [  139.128000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Mar  8 14:21:49 holly2 kernel: [  139.128000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Mar  8 14:21:53 holly2 kernel: [  143.452000] usb 1-2.2: USB disconnect, address 4
Mar  8 14:21:53 holly2 kernel: [  143.452000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Mar  8 14:21:53 holly2 kernel: [  143.452000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1

```

The different usb is the only difference I see, but I believe it could be the cause... So, maybe my first post wasn't all that helpful...
Does anyone have an idea how to manipulate the used usb? What is the number, anway? USB 1 and USB 2? Or something entirely else?

Thank you, 
Jan

---

