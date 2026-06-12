---
title: "Virtual COM Port"
date: 2013-11-23
forum: General Help
---

### Post by manudo on 2013-11-23
Hi, I'm new at Ubuntu and I need something like when I connect an USB the computer recognizes as a serial device, how I can do that?
I Googled a lot but I need that for a Wine program so any ideas, feel free to tell. ;)

---

### Post by Lars Noodén on 2013-11-23
There are USB-to-serial adapters that allow you to connect to a serial device even if your machine does not have a serial port.  Is that what you are asking about?

---

### Post by manudo on 2013-11-23
> **Lars Noodén said:**
> There are USB-to-serial adapters that allow you to connect to a serial device even if your machine does not have a serial port.  Is that what you are asking about?

Thanks for your fast reply, but I have a printer that connects in USB port, but I need that the port can be recognized as a serial (ttys0) port, because I need it in a Windows wine program.
By the way, the USB-Serial adapter couldn't be a bad idea, thanks. :)

---

### Post by Lars Noodén on 2013-11-23
Ok.  Have you looked for some /dev/ttyUSB0 or something like that when you've plugged in your USB printer?

---

### Post by manudo on 2013-11-23
> **Lars Noodén said:**
> Ok.  Have you looked for some /dev/ttyUSB0 or something like that when you've plugged in your USB printer?

If that's a way that a USB can be used as a serial port then yes, exactly. How I can configure it?

---

### Post by Lars Noodén on 2013-11-24
Caveat: I'm not into hardware.

It's not a matter of configuring it, it's there if the device already appears to Ubuntu to be a serial device.  If that is the case then you should be able to connect to it like any other serial device.  

Does /dev/ttyUSB0 or similar appear when you plug in that device?

---

### Post by manudo on 2013-11-24
> **Lars Noodén said:**
> Caveat: I'm not into hardware.

It's not a matter of configuring it, it's there if the device already appears to Ubuntu to be a serial device.  If that is the case then you should be able to connect to it like any other serial device.  

Does /dev/ttyUSB0 or similar appear when you plug in that device?

It's USB.
But the printer has an option that let you print in a Virtual COM port, so I'll try if I connect the printer in that state the ttyUSB0 appears, but, wait a minute... How I can know if the printer is recognized? Is there a devmgmt.msc in ubuntu?

---

### Post by manudo on 2013-11-26
Any ideas?

---

### Post by Lars Noodén on 2013-11-26
Does /dev/ttyUSB0 or something similar appear when you plug in the printer via USB?  If so, try connecting to that device as if it were a serial port.

---

### Post by ian-weisser on 2013-11-26
This old thread seems to successfully cover a lot of this territory: [http://ubuntuforums.org/showthread.php?t=1335098](http://ubuntuforums.org/showthread.php?t=1335098)

---

### Post by manudo on 2013-11-26
> **Lars Noodén said:**
> Does /dev/ttyUSB0 or something similar  appear when you plug in the printer via USB?  If so, try connecting to  that device as if it were a serial port.

No, I configured the printer to Virtual COM mode and nothing happens, no ttyUSB0 file. It's curious because when I connect the printer in USB mode it creates a folder called "usb" when I plug the printer to the PC.

> **ian-weisser said:**
> This old thread seems to successfully cover a lot of this territory: [http://ubuntuforums.org/showthread.php?t=1335098](http://ubuntuforums.org/showthread.php?t=1335098)

Dude, that's awesome, that's exactly I want to do, a serial port to be recognized as a COM1 port in Wine, really thank you.

But you guys can help me with the ttyUSB0 problem? It doesn't appears. D:

---Just to make things clear, that printer has the option to emulate a serial port with a USB cable, I use that cable, not a Serial-USB adapter, just in case.---

---

### Post by Lars Noodén on 2013-11-26
When you have the printer set to emulate a serial connection, which device shows up in /dev when you plug it in?  Try connecting to that one.

---

### Post by manudo on 2013-11-26
> **Lars Noodén said:**
> When you have the printer set to emulate a serial connection, which device shows up in /dev when you plug it in?  Try connecting to that one.

Here's the list of files in /dev when it's nothing connected.
 [ATTACH=CONFIG]248115[/ATTACH] 

Here's the list of files in /dev when I connect the printer with Virtual COM emulation.
[ATTACH=CONFIG]248114[/ATTACH]
No difference.

And here's a screenshot when I connect it with USB normal mode, see that it creates a directory called usb/ and when I cd to it has a lp0 file. The printer works this way, even when I send an echo to /dev/usb/lp0.
[ATTACH=CONFIG]248116[/ATTACH]

---

### Post by manudo on 2013-11-26
I have to create a ttyUSB0 file?

---

### Post by manudo on 2013-11-28
Well, problem solved, I just connected it in USB mode and did this.

```
sudo ln -s /dev/usb/lp0 ~/.wine/dosdevices/com1
```

Links the printer to that port, and if I do an echo works. Thanks.

---

