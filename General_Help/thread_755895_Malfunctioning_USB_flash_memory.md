---
title: "Malfunctioning USB flash memory"
date: 2008-04-15
forum: General Help
---

### Post by FIONEX on 2008-04-15
Hey

This is probably not the place to be posting but ubuntu busted my USB stick.  I've been using the memory all this time on my laptop with no problems.  I used it once on ubuntu and when I unplugged it, it never worked again on any other system.  Windows says "Unknown device" whenever I plug it in.  The indicator on the stick always flashes now.  This is what the kernel log says in ubuntu:
```

Apr 15 10:19:32 fionex-d kernel: [  956.617828] usb 8-1: new high speed USB device using ehci_hcd and address 65
Apr 15 10:19:33 fionex-d kernel: [  957.667753] usb 8-1: new high speed USB device using ehci_hcd and address 70
Apr 15 10:19:33 fionex-d kernel: [  957.928586] ehci_hcd 0000:00:1d.7: port 1 reset error -110
Apr 15 10:19:33 fionex-d kernel: [  957.928592] hub 8-0:1.0: hub_port_status failed (err = -32)
Apr 15 10:19:34 fionex-d kernel: [  958.539405] ehci_hcd 0000:00:1d.7: port 1 reset error -110
Apr 15 10:19:34 fionex-d kernel: [  958.539410] hub 8-0:1.0: hub_port_status failed (err = -32)
Apr 15 10:19:34 fionex-d kernel: [  958.539412] hub 8-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

```

What do you think my options are?  Is the stick basically dead, because the LED on it still flashes.  I have a feeling that its drivers somehow got wiped from its own memory.

---

### Post by StephanG on 2008-04-15
Did you remember to "Safely Remove" the USB stick.  I know windows has an icon in the bottem that you have to click to remove it, but with ubuntu you have to right click the memory stick's icon on the desktop to remove it.  I know myself that often nothing happens if the stick is just pulled out, but its risky and very probably you might have pulled it one time to many.  I know I have.

---

### Post by FIONEX on 2008-04-15
Maybe that's what happend.  So basically it's hopeless, eh?  Might as well buy a new stick?

---

### Post by ryanhaigh on 2008-04-15
Not safely removing the stick will not kill the device, the filesystem may be corrupted but that could be fixed with a format. Sounds to me like regular old hardware failure, maybe try checking the connection to see if anything has been damaged but it sounds to me like your device just gave up the ghost, I bet its just out of the warranty period too!

The ubuntu thing is a conincidence, OS cannot damage a usb device, a filesystem yes a device no.

---

