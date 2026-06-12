---
title: "How can I access my digital camera that interfaces via serial?"
date: 2006-11-23
forum: General Help
---

### Post by contriver on 2006-11-23
Hi, I have a Kodak DC215 and I want to download the pics from it.  The problem is that it interfaces only via serial.  I don't have a Windows computer that has a serial port.  My desktop has a serial port, but it only has Ubuntu running on it.  Is there any way I can access the camera while its hooked up via serial using Ubuntu?

---

### Post by taurus on 2006-11-23
With serial port, I think you need to plug it in before you turn on your computer!!!  Try to reboot while your camera is connected to your computer and see if the kernel picks it up!

```
dmesg | more
```

---

### Post by contriver on 2006-11-23
OK, I will try that now.  Thanks!

---

### Post by contriver on 2006-11-23
OK, I tried that and it didn't work.  Any other suggestions?  Can I access it via the terminal somehow?

---

### Post by taurus on 2006-11-23
I assume you know that you have to mount it by hand!!!  It won't do automount, if that's what you have in mind.  Paste the following command here then...

```
dmesg | more
(hit the space bar for the next 24 lines...)
```

---

### Post by contriver on 2006-11-23
I see...no, I did not know that.  Thanks for the heads up.

---

### Post by contriver on 2006-11-23
OK, tried that, then I went to Disk Manager, but its not there.  Any other ideas?

---

### Post by taurus on 2006-11-23
Can you show me the output of the command from my previous post?  I want to see if your kernel detects it or not.

---

### Post by contriver on 2006-11-23
I just sent you the output via PM.

---

### Post by taurus on 2006-11-23
> **contriver said:**
> I just sent you the output via PM.
Okay, but it has not showed up...

---

### Post by knahrvorn on 2007-02-19
> **contriver said:**
> Hi, I have a Kodak DC215 and I want to download the pics from it.  The problem is that it interfaces only via serial.

I have an old Kodak DC215, too, and I just managed to access it from Ubuntu via the serial cable. I connected the camera while the computer being turned off, then installed gtkam (get it via Synaptic in the System -> Administration menu). In gtkam I clicked Camera -> Add camera and selected "Kodak DC215" in the drop down menu. Welcome to a *SLOW* experience, but it works... You probably want to disable the thumbnail feature first chance you get if you have many pictures in your camera.

A much better solution is probably to buy a cheap SD card reader and get the images through USB2 :)

---

