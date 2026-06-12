---
title: "USb ports revisited"
date: 2014-03-07
forum: General Help
---

### Post by Fsirett on 2014-03-07
I posted a problem with this that I thought was solved, but it is now recurring and it is more or less sporadic

First, some of my USB ports, only the back ports, it would appear, work and some, front ports, do not but they do not stop working in total, but are sort of half working. 

I can use usb sticks with no problem. I have an external drive that works, no problem, however when I cable in MP3 memory devices, there is no response most of the time.

The devices seem to be getting charged without any trouble, but when it comes to reading or writing to the contents, . .nothing. 

I thought of he devices , so I bought a new one to check and it does not work either. I changed to the enclosed cable and it did not work. I am going to buy yet another set of cables today to see if that might be the trouble, but the new cable and the new device work just fine on my wife's laptop, although the older MP3 does not show much life there with an old cable. I am addicted to podcasts, so I write and rewrite often enough that my devices have a very short lifespan in any case.  I am not aware of USB ports wearing out though.

I did look and see this:

[http://askubuntu.com/questions/385091/usb-mouse-and-keyboard-suddenly-stopped-working-in-13-10](http://askubuntu.com/questions/385091/usb-mouse-and-keyboard-suddenly-stopped-working-in-13-10)

that looks somewhat similar, but I am not certain how to proceed from this information or even if this applies to my case. I am in need of guidance (again!)

The lsusb looks like this

```
~$ lsusb
Bus 001 Device 004: ID 1058:10a2 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 04e8:329f Samsung Electronics Co., Ltd CLP-325 Color Laser Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The devices that might be unknown are : 
Bus 001 Device 004 - an external drive (I assume)
Bus 001 Device 001 - i have no idea
Bus 002 Device 006 - A built in card reader that is very rarely used
Bus 002 Device 001 - Another mystery to me. 

I notice Bus 1 only does not include a Device 3 and Bus 2 seems to be missing devices 3-5, however I only have 7 USB ports peeking out of the machine all tolled

I did try moving the external drive to another port and it worked fine there but the MP3 devices did not work in the original port for the drive.

The devices seem to be charging, which makes me think this is a software problem. 

I know the last time I ran under live disk the machine recognised the devices which makes me think that the advice in the other post might be of some help...if I only knew how to implement it without causing great pain and hardship to myself. I have learned my lesson and I am no longer going to demonstrate to the world just who the dummy is in the "for Dummies" books.

Cheers again

Frank Sirett

---

### Post by varunendra on 2014-03-07
Hello Frank!

Is this the FULL output of lsusb ?? -
> **Fsirett said:**
> ```
~$ lsusb
Bus 001 Device 004: ID 1058:10a2 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 04e8:329f Samsung Electronics Co., Ltd CLP-325 Color Laser Printer
[COLOR="#0000CD"]**Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**[/COLOR]
Bus 002 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
[COLOR="#0000CD"]**Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**[/COLOR]

```

If so, your system is very seriously short on Internal USB 2 Hubs and most probably that is the reason why some devices work some don't.

What I have highlighted above in blue are those that you didn't understand what they are. Those are the the Internal USB Hubs on your system's motherboard, and all the ports you have are sharing the same USB hubs.

The chip that contains these hubs has inbuilt multiplexer which allows dynamic allocation or switching of connections of ports to these hubs as required by the connected device.

Usually, one internal USB hub controls two ports, which means two hubs can handle at most 4 devices at the same time. If you connect more devices, they simply won't be recognized. However, this is the *usual* case. There are chips that control more than two ports, yours may be one like that.

Now the bummer - IF the above is the complete output of lsusb, and IF the controller is of the usual type that provides only two ports per hub, then Not only you can connect only 4 devices at a time, but also, two of them would be in USB 1.1 mode, if the two USB 2.0 ports are occupied.

As per your above output, the two (perhaps the only two available ones) USB 2 ports are occupied by a printer and a Western Digital drive (usb Hard disk?). So anything else you connect now will be connected in USB 1.1 mode, and you can't enjoy the full functionality of devices like MP3 players at that speed (12 Mbps, or 1.5 MBps, which is about 1 MBps after deducing the data overhead).

Please post the full output of -
```
lsusb -t
```
..preferably with as many devices connected as you can get, so that all or nearly all ports are occupied. Then it'll be easier to guess or confirm what is happening and what you can do about it.

---

### Post by Fsirett on 2014-03-07
Cheers for that! 

The report you wanted is here:

```
$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/10p, 12M
    |__ Port 4: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 8: Dev 6, If 0, Class=Mass Storage, Driver=usb-storage, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/10p, 480M
    |__ Port 3: Dev 2, If 0, Class=Printer, Driver=usblp, 480M
    |__ Port 5: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M

```

As I say, I have 4 ports in the back that are working fine, although I am wondering what the fourth cable is for. I do not remember, I have just always connected it. Must look.

Of the three front ones, they seem to work fine for USB disks and for USB sticks, but other cable devices are not reading but are providing power to recharge the devices.

I have to run away for most of today, but I am certainly going to be back at about seven or eight my time... it is now 11:30 here.

Cheers

Frank Sirett

---

### Post by varunendra on 2014-03-07
Regardless of how many devices were physically connected, the system, as per above output, has recognized only four of them - the same ones as previous output.

From top to bottom in the list -

[indent]**1)** An HID (Human Interface Device) device - connected to USB 1.1 hub, would be a mouse, or a touchpad or trackball etc. Speed = 1.5 Mb/s (0.19 MB/s)
**2)** A memory card reader - connected to USB 1.1 hub - internally or an external one. Speed = 12 Mb/s (1.5 MB/s)

**3)** A printer - connected to USB 2.0 hub. Printers can't work with USB 1.1, so no matter which port you connect it to, it will always be automatically get connected to USB 2.0 hub internally (the internal multiplexer will switch the port connection internally as required). Speed = 480 Mb/s (60 MB/s)
**4)** A Storage device - connected to USB 2.0 hub. A USB Hard-disk drive, a flash disk or a memory card. Speed = 480 Mb/s (60 MB/s)[/indent]

If I understand the lsusb outpus correctly, you can't connect any more device to the system unless you disconnect any one of the above devices. All your seven ports are sharing these four internal port connections, which means only 4 of the 7 will be usable at any given time, and only 2 of these four will be in USB 2.0 or "High Speed" mode.

---

### Post by Fsirett on 2014-03-07
Cheers. 

More information. When I gout home I started up with a live disk and...it showed me everything as per usual. Well, when I say as usual, I mean that it showed my new MP3 but my old one might be knackered. It does not show up at all. That is fine, because I read and write them completely pretty much on a weekly basis I expect them to be short lived. I buy really cheap ones for that reason. they never outlive the warranty and when I claim they tell me that I am out of the "fair use" category. That is okay. I can buy at least two of them for a tenner, sometimes three. I digress.


The fact is that things are working on the live disk that are not working when I use the on board system.

I am not certain that this:

[http://askubuntu.com/questions/38509...rking-in-13-10]("http://askubuntu.com/questions/385091/usb-mouse-and-keyboard-suddenly-stopped-working-in-13-10")

is not the same problem now. What do you think?

The computer is getting a little long in the tooth, more than five years old, probably closer to ten. I really should replace it, but it normally works so well. When I was running Windows the (Microsoft specialist) techs were always telling me I needed a new computer, but that began nearly from the day it was new. From that day and every day since it was "no" and I eventually fell into Ubuntu and have never looked back...more digression? Sorry!

Frank Sirett

---

### Post by varunendra on 2014-03-07
> **Fsirett said:**
> When I gout home I started up with a live disk and...it showed me everything as per usual.

Did you compare the "lsusb -t" results? I would like to see the difference. I find it hard to believe that the Linux kernel can not properly detect an available USB hub of a system so old, unless of course the kernel is broken somehow.

If the output from the Live session shows more hubs or ports detected, you may try to reinstall or upgrade the current kernel on the system.

And the askubuntu post you linked is certainly not related, not even remotely. That is a question where devices were detected, only the drivers for them were not working as expected, whereas in your case even the USB hub/ports are not detected, if they are actually provided by the chip.

---

### Post by Fsirett on 2014-03-07
Right! I am now on Live disk and I am duplicating the conditions that were present the last time, I notice it does not show the MP3 at this time. As I say it is an intermittent problem

The lsusb printout is:

```
lsusb
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 1058:10a2 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 04e8:329f Samsung Electronics Co., Ltd CLP-325 Color Laser Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

 And The Lsusb-t reading is:

```
lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/10p, 12M
    |__ Port 4: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/10p, 480M
    |__ Port 3: Dev 2, If 0, Class=Printer, Driver=usblp, 480M
    |__ Port 5: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 8: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M
ubuntu@ubuntu:~$ 

```

I assure you, I did have the player appearing a little while ago when I first came back. 

I changed ports and cables and I am still getting no response. I am about to restart and try it all again. 

Please standby.

Frank Sirett

---

### Post by Fsirett on 2014-03-07
What I have done is I disconnected the external drive, whixh shoukld make a differennce, but it does not seem to do anything at all.
The new Lsusb is:

```
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 04e8:329f Samsung Electronics Co., Ltd CLP-325 Color Laser Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And the lsusb -t is:

```
lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/10p, 12M
    |__ Port 4: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/10p, 480M
    |__ Port 3: Dev 2, If 0, Class=Printer, Driver=usblp, 480M
    |__ Port 8: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M

```

I have to say this is all a mystery to me. I am not certain of anything here.

Frank Sirett

---

### Post by varunendra on 2014-03-07
I think I understand this situation. You seem to have, like I guessed, one USB hub chip with 4 downstream ports support. Something like this one -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=250944&stc=1&d=1394230503[/IMG]

A quote from the datasheet from which I copied above image -
> The VT6212 / VT6212L **supports 4 downstream facing ports** with 1.5 (low-speed), 12 (full-speed) and 480 (high-speed) Mbps transaction capability. The Root Hub is integrated with physical-layer transceivers **shared by UHCI (for full/low-speed) and EHCI (for high-speed) Host Controllers**.

So unless it shows us something new again, it supports only 4 ports at any given time.

What is the output of -
```
lspci -nnk | grep -iA2 usb
```

---

### Post by Fsirett on 2014-03-07
Something begins to click.

```
~$ lspci -nnk | grep -iA2 usb
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f1]
    Kernel driver in use: ohci-pci
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f2]
    Kernel driver in use: ehci-pci

```

I have an Nvidia graphics card installed. It is an outdated and quite cheap one, since I do not play games and such.

I also see that the motherboard is using Nvidia. Could there possibly be a problem with the drivers? I use the 319 driver this time, but I am not vcertain what I used before. Would it possibly help if I moved to a slightly older driver? I am grasping, but that is a very uneducated guess.

Cheers

Frank Sirett

---

### Post by varunendra on 2014-03-07
Nvidia is just a brand name. They manufacture many things, not just graphics cards, and evidently, USB controller chips are (or were, when you bought your computer) one of them.

What you see above are USB controller chips, most probably two modules built into one single chip. Unfortunately, I don't know how to look up the **Controller chip ID** (probably opening the case and looking at the chip is the only way) to confirm how many ports you can expect to work simultaneously. A search by device-ID from above output turned up nothing useful.

So for now, I have nothing to add than to re-iterate what I already mentioned in my previous post - don't expect more than 4 devices working simultaneously, or more than 2 "High-speed" devices simultaneously.

---

### Post by Fsirett on 2014-03-08
Cheers. 

It would appear to me I have a hardware problem. 

I can plug in any number of USB sticks and they read just fine, 

I have unplugged the external drive and all of the USB sticks and just plugged in the MP3 I know works and it will not come up. I have tried three cables, one new, and they still do not come up. I am going to first try another new cable and then speak to a hardware technician about the problem. 

I would really rather not have to replace the motherboard, but that might be the upshot of all of this. I have a dual core chip now, but I see replacements are not terribly expensive, so I might upgrade. 

In fact I would like more USB ports and a few more on board SATA ports; ill winds and all that. 

Cheers and thanks again

Frank Sirett

P.S. I will leave this thread open and report the results of the tech report. That might help others who travel down this path.

---

### Post by varunendra on 2014-03-08
You should take a look at the output of "lsusb" or "lsusb -t" if more than 4 devices are detected at ANY given time.

Similarly when the MP3 player is connected (detected or not).

If you ever see more than 4 devices detected in "lsusb", post back the output here. I have personally dealt with ASRock motherboards (my brother's computer) and it has exactly the same kind of problem. The internal switching of the ports is really dodgy on these chips/boards. I don't know it is a fault of the controller chip or the motherboard/BIOS, but it IS common with old/cheap ASRock motherboards.

That being said, you don't need to upgrade the whole motherboard. Assuming you have empty PCI slots available, get a PCI USB-2 card and you'll have your extra ports - much better than these dodgy internal ones.

It won't guaranty the functionality of you MP3 players, but at least you'll have more USB2 ports that will definitely function much better than the internal ones (I know because I've personally tested that, with a dirt-cheap 3+1 port USB2 PCI card.).

---

### Post by kurt18947 on 2014-03-08
> **varunendra said:**
> 
<snip>
That being said, you don't need to upgrade the whole motherboard. Assuming you have empty PCI slots available, get a PCI USB-2 card and you'll have your extra ports - much better than these dodgy internal ones.

It won't guaranty the functionality of you MP3 players, but at least you'll have more USB2 ports that will definitely function much better than the internal ones (I know because I've personally tested that, with a dirt-cheap 3+1 port USB2 PCI card.).

I was having the same thought.  I have a MoBo was an AMD chipset on which the USB ports seem a little .... flaky for want of a better term.  I bought a PCI USB card containing a NEC chipset off Ebay for around $7.00.  Installed it and it works great.  I'd read that NEC chipsets tend to be compatible with most USB devices on Linux.  I believe my PCI card has 4 USB slots.

Output of 'lspci' (relevant parts)

Integral USB: 

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller

PCI card:

03:06.0 USB controller: NEC Corporation OHCI USB Controller (rev 44)
03:06.1 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 05)

Output of 'lsusb':

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If you choose to go the PCI card route, I would not plug a keyboard or mouse into one of its ports.  Those ports may or may not be recognized in BIOS mode before the O.S. loads a USB driver.

---

### Post by Fsirett on 2014-03-19
Cheers again for all your help, I jhave at last solved the problem, but it is a lesson we should all learn. 

I went out and bought two new cables from two different chops and both of them worked just fine with one device but not the other. Now I have found one cable works (almost) just fine with the second device on my wife's laptop. 

I am now looking at the devices and reviewing the problems and buying more cables to try.

Moral of this story: just because it is new, and/or  expensive does not mean it is good! If you have this problem go to every place you can think of and buy cables and try them before you accept the inevitability of a trip to the repair shop (that, in my experience always; a.opt for the most expensive repair they can come up with or b. are a long train ride and walk from where I live) 

In fact, I like the two last suggestions as well. Cards are not very expensive and can often solve a multitude of problems. When I had problems with displays, I went out and bought the cheapest graphics card I could find and everything cleared up in an instant. Too bad I do not always take my own counsel...or even remember it when the time comes. 

I think I can mark this thread as now solved!

Cheers

Frank Sirett

---

