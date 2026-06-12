---
title: "Fresh install Ubuntu Mate 22.04 and no printers..."
date: 2024-11-12
forum: General Help
---

### Post by mittsy on 2024-11-12
Hello all
Fresh install Ubuntu Mate and I have no printers to use.  A URI is asked for.  URI?  I have a Brother HL-L2300D that is USB wired.  Could someone please tell me how to install the drivers or? to get them to work.  
I'm old and slow so please be tolerant.  I'm a wanna be geek.  LOL

Thanks
mittsy

---

### Post by 1fallen on 2024-11-12
I've never heard of this model, but have a look here: [https://ubuntuforums.org/showthread.php?t=2468600](https://ubuntuforums.org/showthread.php?t=2468600)

---

### Post by yancek on 2024-11-12
Driver download at the Brother website at the link below.  Have you tried that?

[https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2300d_us_eu_as](https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2300d_us_eu_as)

---

### Post by grahammechanical on 2024-11-12
Are you saying that you do not have a printer?

The operating system uses IP addresses (URLs) to connect to things like printers and modem as if it is connecting to machines on a network. All the equipment is networked together. IP addresses are used to connect our computers into a network to access this forum.

The printer manual should give you the IP address (URL) or there may be a sticker on the printer giving the IP address.

The printer is connected by USB. Linux comes with USB drivers as standard. 

Regards

---

### Post by oldfred on 2024-11-12
I have Brother printer and have not needed to install any drivers. It just works.
But it seems to install several printers & only one works with 24.04. Test install of 24.10 only showed the one printer that does work.

What does these show?
[FONT=monospace][COLOR=#000000]lpstat -t[/COLOR]
driverless

Does this have a long list of details?
lpinfo -l -v
[/FONT]

---

### Post by mittsy on 2024-11-12
Hi oldfred
I get the below 

ralph@ralph-MS-7B86:~$ lpstat -t
driverless
scheduler is running
no system default destination
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.

---

### Post by mittsy on 2024-11-12
**Hi **[URL="https://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]grahammechanical

I have the printer connected via USB.  I don't know what the problem is, but my install did not pick up the printers.  I have 2: Brother HL-L2300D AND A SAMSUNG SLM2835DW
[/COLOR][/B][/URL]

---

### Post by mittsy on 2024-11-12
Let me go there now...

---

### Post by mittsy on 2024-11-12
[FONT=monospace]Report from lpinfo -l -v

```
@ralph-MS-7B86:~$ lpinfo -l -v
Device: uri = beh
        class = network
        info = Backend Error Handler
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = lpd
        class = network
        info = LPD/LPR Host or Printer
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = http
        class = network
        info = Internet Printing Protocol (http)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = ipp
        class = network
        info = Internet Printing Protocol (ipp)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = socket
        class = network
        info = AppSocket/HP JetDirect
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = cups-brf:/
        class = file
        info = CUPS-BRF
        make-and-model = Virtual Braille BRF Printer
        device-id = MFG:Generic;MDL:CUPS-BRF Printer;DES:Generic CUPS-BRF Printer;CLS:PRINTER;CMD:BRF;
        location = 
Device: uri = ipps
        class = network
        info = Internet Printing Protocol (ipps)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = serial:/dev/ttyS0?baud=115200
        class = serial
        info = Serial Port #1
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = https
        class = network
        info = Internet Printing Protocol (https)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = hp
        class = direct
        info = HP Printer (HPLIP)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = smb
        class = network
        info = Windows Printer via SAMBA
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = parallel:/dev/lp0
        class = direct
        info = LPT #1
        make-and-model = unknown
        device-id = 
        location = 
Device: uri = hpfax
        class = direct
        info = HP Fax (HPLIP)
        make-and-model = Unknown
        device-id = 
        location = 
ralph@ralph-MS-7B86:~$ 


```
[/FONT]

---

### Post by mittsy on 2024-11-12
old fred

I'm really getting confused with trying to read and answer all the different people.  I did get some drivers, I think.  See image[IMG]/home/ralph/Pictures/2024-11-12_18-35.png[/IMG]

Thanks

---

### Post by oldfred on 2024-11-12
Cannot see images on your system.
Use forum's Go Advanced Editor and paper clip icon.
Also for terminal output use code tags to preserve formatting.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]


It is not seeing your printer.
Ubuntu now is supposed to be driverless and printers are handled automatically.
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

Have you rebooted with printer connected and on?

Does this show printer on usb port?
lsusb

This is part of my output.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsusb [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 0c45:760a Microdia USB Keyboard 
Bus 001 Device 003: ID 0461:4e22 Primax Electronics, Ltd Dell Mouse, 2 Buttons, Modell: MS111-P 
Bus 001 Device 004: ID 8087:0a2b Intel Corp. Bluetooth wireless interface 
Bus 001 Device 005: ID 04f9:0428 Brother Industries, Ltd HL-L2390DW


[/FONT]
```

---

### Post by yancek on 2024-11-13
The obvious asked above.  Is your printer  securely plugged into a power source and the power cord is secure on the printer and the usb is securely attached to the computer and the printer and is turned on?  Check all these connections and make sure the printer is turned on before you reboot.  If it still fails, good luck.

---

### Post by tucsonmediastudio on 2024-11-13
you need to properly install the the drivers because Brother-L2300D is a USB wired printer.
I will let you know step by step. Can you tell me what Ubuntu version Your are using right now.

---

### Post by mittsy on 2024-11-13
Hello

1) Cannot see images on your system.
2) Use forum's Go Advanced Editor and paper clip icon.
3) Also for terminal output use code tags to preserve formatting.
4) If using Quick Reply then ```
 at the beginning and 
``` at the end. 

1) What does this mean?
2) I'm using the Advanced editor now (I think), and the paper clip is for attachments.
3) I have no idea what you mean
4) I don't know code, so I will just use the Advanced Editor...right?

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 1a2c:4c5e China Resource Semico Co., Ltd USB Keyboard
Bus 005 Device 002: ID 0557:8021 ATEN International Co., Ltd Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 003: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 003 Device 002: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I am not a polished user of Ubuntu or of any forum.  Sorry
mittsy

---

### Post by mittsy on 2024-11-13
Yes it is plugged in and working

Thanks

---

### Post by mittsy on 2024-11-13
Hi  				 				 					 						 	[**[COLOR=#000000]tucsonmediastudio[/COLOR]**]("https://ubuntuforums.org/member.php?u=2192424")[B][COLOR=#000000],

I am using Ubuntu Mate 22.04

mittsy
[/COLOR][/B]

---

### Post by oldfred on 2024-11-13
You do not show Brother in USB list?
Are you plugging printer into hub? If so try plugging in directly and see if then seen?

---

### Post by mittsy on 2024-11-13
Thank You for your help.

---

### Post by mittsy on 2024-11-13
oldfred,

You gave me the kick in the ass to remind me about my printer switch.  I run Windows 10 also.  Been a long time since I used Linux (6 months).  I was in the hospital with a few mini strokes, etc.etc.(long story).  

Take care, and thanks to all who helped with this "problem".

mittsy

---

