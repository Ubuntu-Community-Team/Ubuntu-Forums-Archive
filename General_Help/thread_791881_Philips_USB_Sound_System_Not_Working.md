---
title: "Philips USB Sound System Not Working"
date: 2008-05-12
forum: General Help
---

### Post by phibit on 2008-05-12
I have a Philips FWM779 Mini HiFi System like this one:
 [http://www2.shopping.com/xPF-Philips-FWM779-Mini-HiFi-System-with-5-CD-Changer-with-USB-PCLink](http://www2.shopping.com/xPF-Philips-FWM779-Mini-HiFi-System-with-5-CD-Changer-with-USB-PCLink)

The sound system has a USB Interface that works fine in Windows XP, provided the drivers are installed. There is also a Windows-only software called Philips Sound Agent 2, which controls the interface.

My question is, is there any way I could get this USB interface to work in Ubuntu Hardy? It's a great sound system and I'd like to put it to good use.

Output of lsusb:

```
Bus 002 Device 009: ID 0471:0111 Philips 
Bus 002 Device 003: ID 045e:009d Microsoft Corp. 
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Output of dmesg on connection:

```
[ 1410.344307] usb 2-10: new full speed USB device using ohci_hcd and address 7
[ 2085.161478] usb 2-10: new full speed USB device using ohci_hcd and address 9
[ 2085.378518] usb 2-10: configuration #1 chosen from 1 choice
[ 2085.639810] input: Philips Philips Audio Set as /devices/pci0000:00/0000:00:0b.0/usb2/2-10/2-10:1.3/input/input10
[ 2085.694935] input,hidraw3: USB HID v1.00 Device [Philips Philips Audio Set] on usb-0000:00:0b.0-10
```

So it seems that it's recognized as an Audio device, but there is no actual sound being passed through.

Output of 'less /proc/bus/usb/devices'

```
T:  Bus=02 Lev=01 Prnt=01 Port=09 Cnt=03 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0471 ProdID=0111 Rev= 4.02
S:  Manufacturer=Philips
S:  Product=Philips Audio Set
S:  SerialNumber=PHI922
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS= 200 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=84(I) Atr=09(Isoc) MxPS= 200 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=1ms
```

Is there anything I can try that will make this work?

---

### Post by phibit on 2008-05-13
So far I have tried running it in VirtualBox but no luck there. It's not even detected through VirtualBox... :(

---

### Post by Kg001 on 2008-05-22
That Figures 

There seems to be an issue with USB & VirtualBox & considering 75% of my drive space is on USB drives Including my linux partition that's a real issue for me. Can't help withthe Philips USB Sounds like you are stymied unless you can find a driver. I will continue looking for a post to fix the Vbox USB issues & post back if I solve it.

---

### Post by kuolas on 2008-10-11
I have a similar Philips "USB PC Link" Audio Set... It doesn't work either! You shoul contact the ALSA developers on their mailing list.

[http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)

Subscribe here:
[http://mailman.alsa-project.org/mailman/listinfo/alsa-devel](http://mailman.alsa-project.org/mailman/listinfo/alsa-devel)

---

### Post by macrex on 2008-10-25
Works with VirtualBox!

It worked for me with a strange workaround:
As you noticed, this Micro-System is recognised by Linux, however, no sound comes through the speakers. Even when the audio output is correctly configured. So, one of theses days, I found out one way to make it work:
1. Plug the Micro-System to your computer (Linux box);
2. Startup VirtualBox (binary with USB support) and install the manufacturer driver in a Windows virtual machine;
3. Plug the USB Philips device into your virtual machine (use the top menu on your virtual box...) when the driver installation requests that you do so. The driver installation will be successful and your micro-system will be completely connected and correctly working.
4. Play any type of sound inside Windows to make sure everything is ok (don't worry if the sound quality is poor...).
5. Now close the virtual machine (save the virtual machine state, for instance...). For now on, you have the micro-system completely working on Linux. (as an example, you can control the micro-system volume properties using alsamixer).
6. As soon as you do not turn off your micro-system, it will be working on Linux.

Finally, I came to realise that the snd-usb-audio Linux module lacks something that the Widows driver can do. Appearently, the Windows driver 'switches on' the USB device on the Micro-System.
I will research more and I will try to propose a patch for the snd-usb-audio module. However, I've been in a hurry recently, and I cannot promise anything. So, if anyone can lead this course of action, that would be great too (right now, I am using 'strace' to trace VirtuaBox binary actions to see how it changed the usb's communication with the Micro-System...).

Have fun with your system for now with this workaround...

I use gentoo, and I have no issue with VirtualBox usb support... It worked out of the box for me. Just a hint: did you make sure that your user is in the 'usb' group?!

---

### Post by kuolas on 2008-12-03
I have MCM595, and does not work under linux either.

I filled this bug report, please check it out:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/282232](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/282232)

I filled an ALSA Mantis bug ticket, it's linked on the launchpad report.

I've tried you idea with VirtualBox 2.0 and Hardy 8.04LTS and it didn't work for me. So, I will keep looking for a solution.

Damn you non-standard USB Audio.

---

### Post by marco_macarena on 2009-04-02
Hi!

So guys, has anyone found a solution??
I have this problem too... whit a MCM-530 MicroSystem...
I didn't have try the VirtualBox yet, but would be nice if we could use this without those alternative ways... 

thanks,
Macarena

---

