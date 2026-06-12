---
title: "Ubuntu does not detect usb cable"
date: 2017-03-27
forum: General Help
---

### Post by offir on 2017-03-27
I'm trying to program an ham radio with chirp

With the device came a cable on one side of its normal USB connection
And on the other side connect pl 3.5 (Attached Image)
I connected to the computer
And Ubuntu does not recognize it

I have tried
```
lsusb
```
or 
```
dmesg
```
And still nothing Ubuntu does not recognize the cable

---

### Post by Autodave on 2017-03-27
What is the purpose of the cable? What does it attach to or what is it supposed to do?  Just a cable used to connect a peripheral will probably not be recognized.

---

### Post by Kris_M on 2017-03-27
Does windows recognize it?

Do you have any drivers for it?

(the chirp software probably has the drivers and you would have to install that.  If windows software you might try playonlinux or wine.)

chirp comes in windows or MAC installers.

further thoughts - since chirp is probably using that connection as a faux rs232 (serial) (which is why linux doesn't see it when you plug it into a usb) it will probably not work under linux under wine, but you can give it a try.

---

### Post by offir on 2017-03-28
Several answers

> What is the purpose of the cable? What does it attach to or what is it supposed to do?
The cable is connected at the other end to a radio
And with the help of a program called chirp, you can program the device
in the part that connects to the computer has a chip

> Does windows recognize it?

Do you have any drivers for it?


no and yes
When I received the cable the CD with driver software was broken
I went into the site of the radio
And downloaded a driver and software for Windows
It detected the cable and asked to do restart the computer
After restarting
The computer did not recognize the cable anymore
On Google search I came to this site Which explains how to install the driver on Windows
[http://www.miklor.com/COM/UV_Drivers.php]("http://www.miklor.com/COM/UV_Drivers.php")
I worked according to the instructions of this guide several times without success
There was always an unknown device written
I tried on 4 computers with windows without success


I prefer Linux

> chirp comes in windows or MAC installers.
chirp is a linux program
```
sudo apt-add-repository ppa:dansmith/chirp-snapshots
sudo apt-get update
sudo apt-get install chirp-daily
```
[http://chirp.danplanet.com/projects/chirp/wiki/Download]("http://chirp.danplanet.com/projects/chirp/wiki/Download")

> the chirp software probably has the drivers and you would have to install that
chirp has the driver for the radio device not to the cable
when i connect the cable to the computer I should see a connection /dev/ttyUSB0
But there is not
what i see is  /dev/ttys0 to /dev/ttys31
no usb
i try this instructions

> serial port permissions

Note that you may need to adjust permissions on the /dev/tty(something) device, or add your users who want to use Chirp to the "dialout" group in order to let non-privileged users access the serial device.

This issue is often indicated by an "access denied" error when accessing serial port.

On ubuntu, for example, this is accomplished with:
```
sudo usermod -aG dialout username
```
where username is your username. You will then need to log out and back in for it to take effect.

I wrote that
```
sudo usermod -aG dialout offir
```
Without success

---

### Post by offir on 2017-03-28
Here are the results of commands

```
lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch
Bus 003 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
 dmesg | tail
[ 2390.981551] usb 1-1.5: device descriptor read/64, error -32
[ 2391.169524] usb 1-1.5: device descriptor read/64, error -32
[ 2391.357531] usb 1-1.5: new full-speed USB device number 8 using ehci-pci
[ 2391.437549] usb 1-1.5: device descriptor read/64, error -32
[ 2391.625552] usb 1-1.5: device descriptor read/64, error -32
[ 2391.813533] usb 1-1.5: new full-speed USB device number 9 using ehci-pci
[ 2392.229540] usb 1-1.5: device not accepting address 9, error -32
[ 2392.313546] usb 1-1.5: new full-speed USB device number 10 using ehci-pci
[ 2392.729537] usb 1-1.5: device not accepting address 10, error -32
[ 2392.729587] usb 1-1-port5: unable to enumerate USB device
```



```
dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.653317] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A

```

---

### Post by Kris_M on 2017-03-28
I don't know the answer.
Here is a FAQ that has info on setting com port number in windows and place to contact for help [http://chirp.danplanet.com/projects/chirp/wiki/FAQ](http://chirp.danplanet.com/projects/chirp/wiki/FAQ)
also [http://chirp.danplanet.com/projects/chirp/wiki/How_To_Get_Help](http://chirp.danplanet.com/projects/chirp/wiki/How_To_Get_Help)
also [http://chirp.danplanet.com/projects/chirp/wiki/Home](http://chirp.danplanet.com/projects/chirp/wiki/Home)
look for linux based live cd [http://chirp.danplanet.com/projects/chirp/wiki/Download](http://chirp.danplanet.com/projects/chirp/wiki/Download)

Good luck!

---

### Post by offir on 2017-03-28
The problem is not in chirp

The problem is that the computer does not recognize the cable

Once the computer detects the cable the rest will work

---

### Post by vidtek on 2017-03-28
> **offir said:**
> The problem is not in chirp

The problem is that the computer does not recognize the cable

Once the computer detects the cable the rest will work

Offir-

The problem is that the radio interface will be either an RS232 or RS485 standard.  
There is also the distinct possibility that your cable is not the best.
There are many cheap Chinese adaptors/cables doing the rounds and some are better than others.  I very much doubt it is a straight-through cable, there will be either a passive resistor/capacitor/coil array or more likely the usb housing will incorporate a small ic. to interface to RS232. Edit: Easily checked with a multimeter:
The other problem you have is ever-decreasing support, both hardware and software for RS232/485.

In your place I would first pick up an older laptop at a car boot type sale that has a serial port, then fabricate a cable for that.  Chances are, it will also have an old copy of windows which has better serial port support, that would cost almost nothing.

Forget linux for this application unless you have a couple of weeks to stuff around with it, or maybe you can find someone else who has managed to get this working on Linux.

Another avenue is to get a more expensive and reliable usb cable/adaptor from RS components or Farnell.  The Samygo (Samsung TV support) forum has information on these cables, the factory interface uses these cables, I have one myself which works after trying several cheapies I gave up and I got one from RS Components.

Best of luck, Tony.

---

### Post by offir on 2017-03-28
> In your place I would first pick up an older laptop at a car boot type sale that has a serial port, then fabricate a cable for that. Chances are, it will also have an old copy of windows which has better serial port support, that would cost almost nothing.

i try on old computer with windows xp
but no go
still dont work 
The same result

i try that on 2 computers with window7 
one computer with windows 10
one computer with windowx xp

---

### Post by vidtek on 2017-03-28
> **offir said:**
> i try on old computer with windows xp
but no go
still dont work 
The same result

i try that on 2 computers with window7 
one computer with windows 10
one computer with windowx xp

Yes, but I presume you are still using the same USB cable, older computers have an actual serial port and you may have to revert to windows 98 to get consistently good results.
You need to either get a good quality usb cable/adaptor or make your own serial cable into an actual serial port.
Trust me, I've spent months playing with serial ports and usb adaptors and this is at the heart of your issues.   To keep plugging a crappy cable into various machine's usb ports will just drive you crazy.
The XP machine, does it have a serial port?
Tony.

---

### Post by offir on 2017-03-28
> The XP machine, does it have a serial port?
yes 
so do all the other computers 
old computer but new OS


about the cable I also think that's the direction

I will try to get another cable to see if it will work

---

### Post by vidtek on 2017-03-28
Good luck, you are better off with a home-brew rs232 cable of your own if you are handy with a soldering iron.

Cheers, Tony

---

### Post by offir on 2017-03-28
> Good luck, you are better off with a home-brew rs232 cable of your own if you are handy with a soldering iron
i am good with soldering iron
I have tools and connectors
But I do not have a sketch of such a cable
I mean, I do not know which leg goes
to which leg on the other side

---

### Post by vidtek on 2017-03-28
Google is your friend, trust in google!!

Don't worry, I can never remember either and I've been playing with rs232 for 30 years.

Tony
Edit: here is a link to the samygo info--[https://wiki.samygo.tv/index.php?title=Ex-Link_Cable_for_C/D/E_Series_and_BD_players]("https://wiki.samygo.tv/index.php?title=Ex-Link_Cable_for_C/D/E_Series_and_BD_players")

Tony

---

