---
title: "USB to Serial Cable -- no data from ttyUSB0"
date: 2008-07-08
forum: General Help
---

### Post by Xuor on 2008-07-08
I have an LCD monitor with serial output for touchscreen functionality. My desktop does not have a serial port, so I grabbed a USB-RS232 adapter cable. The cable has an ark3116 chip, and is apparently recognized properly--that is, dmesg reports 

> 
usb-12.2: ark3116 converter now attached to ttyUSB0"


However, performing:

> 
sudo cat </dev/ttyUSB0


retrieves no data at all, regardless of whether I plug the monitor or a serial mouse into the adapter.

lsusb describes this adapter cable as follows:
> 
ID 6547:0232


I'm willing to test the device with a voltmeter to verify functionality, but I really don't know which pins to probe.

I'm running Xubuntu 8.04 with kernel 2.6.24-16 generic.

Any thoughts on how to retrieve data from this device?

---

### Post by Xuor on 2008-07-08
Update...now I'm trying things on a system with a serial port. Same software configuration, everything.

I have the serial mouse in the first serial port, the monitor in the second. When I sudo cat either /dev/ttyS0 or /dev/ttyS1, I get zero input no matter what I do with the devices.

Any thoughts?

---

### Post by Xuor on 2008-07-08
More thoughts...I think the reason cat isn't returning anything from the serial ports is 'cause some other process already has access to the serial ports. How do I determine what that process might be?

---

### Post by Car60n on 2008-07-08
we  know your id--> ID 6547:0232 
so i think you use this command to activate your device--
```
sudo modprobe usbserial vendor=0×6547 product=0×0232
```

hope it helps..

---

### Post by Xuor on 2008-07-08
Bingo...we're getting somewhere now. The command to detect which process has a file/device open is lsof. Beautiful piece of knowledge, that.

The issue with no read on /dev/ttyS0 was because ttyS0 was owned by root instead of uucp, per [http://www.nslu2-linux.org/wiki/HowTo/AddASerialPort](http://www.nslu2-linux.org/wiki/HowTo/AddASerialPort) under "Accessing the Terminal" (How in the world was anyone supposed to know that? And why was root the owner anyway?)

Now I'm getting data reads from ttyS1, the mouse, but not ttyS0, the monitor. And cat still doesn't return anything. I've had to use, instead:

> 
cu -s 1200 -l /dev/ttyS1


Not entirely sure what that does, but I'm workin' on it...

---

### Post by Car60n on 2008-07-08
can you tell the output when you type dmesg..

---

### Post by Xuor on 2008-07-08
@ Car60n:

Yeah, been there, tried that. But thanks.

That should activate the device if Linux wasn't detecting it properly, but that doesn't seem to be an issue. It's  loading fine, and attaching to ttyUSB0. But I couldn't read anything from /dev/ttyUSB0 after attaching.

I think I've moved on from the USB-to-serial idea now, for various logistical reasons. I'm concentrating on the plain-Jane serial port at the moment.

---

### Post by Xuor on 2008-07-08
dmesg? After inserting the USB cable from the serial adapter, I get:

> 
[ 3896.896604] usb 1-2.3: new full speed USB device using uhci_hcd and address 8
[ 3897.017775] usb 1-2.3: configuration #1 chosen from 1 choice
[ 3897.332389] usbcore: registered new interface driver usbserial
[ 3897.333744] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 3897.335753] usbcore: registered new interface driver usbserial_generic
[ 3897.335772] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 3897.375674] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for ark3116
[ 3897.377673] ark3116 1-2.3:1.0: ark3116 converter detected
[ 3897.418139] usb 1-2.3: ark3116 converter now attached to ttyUSB0
[ 3897.418193] usbcore: registered new interface driver ark3116


---

### Post by Car60n on 2008-07-08
hmmm....
your device is at ttyUSB0, 
don't know what the problem is but you can try to log the device
using ttylog...

---

### Post by ramjet_1953 on 2008-07-08
I don't know why, but the Ubuntu developers see fit to install [COLOR="Blue"]brltty[/COLOR] as a default.

This is a package that allows blind people to use a Braille reader.

Unfortunately, it interferes with serial communications for other uses.

Go into Synaptic package manager and ensure that these 3 packages are NOT installed:

1. brltty
2. brltty-flite
3. brltty-x11

Hopefully, after they are removed your USB to Serial will come to life.

Regards,
Roger :cool:

---

### Post by sles on 2008-07-09
I have absolutely the same problem- I can't connect to cisco router using ttyS0 or ttyUSB0 since upgrade to 8.04.
Almost the same problem on my colleague computer- serial port connection hangs very soon with 8.04. 7.10 had no such problem.
btw, brltty etc, are removed

---

### Post by cszikszoy on 2008-07-09
> **sles said:**
> I have absolutely the same problem- I can't connect to cisco router using ttyS0 or ttyUSB0 since upgrade to 8.04.
Almost the same problem on my colleague computer- serial port connection hangs very soon with 8.04. 7.10 had no such problem.
btw, brltty etc, are removed

Do you know what chipset the USB --> serial converter you have is based on?  I haven't had any problems with my usb serial, and it's based on the FTDI chipset.

Can you post any information from dmesg after you plug in the usb serial device?

---

### Post by sles on 2008-07-09
> **cszikszoy said:**
> Do you know what chipset the USB --> serial converter you have is based on?
pl2303
but, as I wrote, problem is not in converter, minicom in 8.04 doesn't work with onboard serial port!

---

### Post by cszikszoy on 2008-07-09
OK.. have you tried any other terminal programs, GTKterm?

> **cszikszoy said:**
> Can you post any information from dmesg after you plug in the usb serial device?

---

### Post by ramjet_1953 on 2008-07-10
+1 to FTDI Chip!

After removing brltty, it just works!
No need for any special drivers, or patches.

Regards,
Roger :cool:

---

### Post by sles on 2008-07-11
> **cszikszoy said:**
> OK.. have you tried any other terminal programs, GTKterm?


Yes. There is no difference...

---

### Post by sles on 2008-07-21
btw, we found that minicom (or, more correctly, ubuntu 8.04) receives data from serial port, but sends nothing- I mean we can see router bouut messages, but our input is ignored...

---

### Post by cszikszoy on 2008-07-21
> **cszikszoy said:**
> Can you post any information from dmesg after you plug in the usb serial device?

 .

---

### Post by sles on 2008-07-23
I'm talking about /dev/ttyS0 which is on board- there no difference between it and /dev/ttyUSB0

---

### Post by xjjoe01 on 2008-09-17
> **ramjet_1953 said:**
> I don't know why, but the Ubuntu developers see fit to install [COLOR="Blue"]brltty[/COLOR] as a default.

This is a package that allows blind people to use a Braille reader.

Unfortunately, it interferes with serial communications for other uses.

Go into Synaptic package manager and ensure that these 3 packages are NOT installed:

1. brltty
2. brltty-flite
3. brltty-x11

Hopefully, after they are removed your USB to Serial will come to life.

Regards,
Roger :cool:


Thanks!! This fixed my problem with my serial connection also!!

:guitar:


Joe

---

