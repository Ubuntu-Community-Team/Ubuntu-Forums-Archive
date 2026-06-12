---
title: "My perfect solution for Lexmark printers"
date: 2006-09-19
forum: General Help
---

### Post by pod25 on 2006-09-19
I bought myself a new printer, a *Lexmark*  Doh !!
I soon found out that lexmark do not support Linux (at least not very well).
I wanted my printer to be a network printer running off my ubuntu server machine.
So my perfect solution was :
I installed VMware onto my ubuntu server, then installed Windows XP into VMware, then networked my printer that way.
It was still a bit tricky getting everything working together, but I done it in the end.
I solved my problem.

A heads up tip for all those having the same problem.

---

### Post by tagra123 on 2006-09-19
> **pod25 said:**
> I bought myself a new printer, a *Lexmark*  Doh !!
I soon found out that lexmark do not support Linux (at least not very well).
I wanted my printer to be a network printer running off my ubuntu server machine.
So my perfect solution was :
I installed VMware onto my ubuntu server, then installed Windows XP into VMware, then networked my printer that way.
It was still a bit tricky getting everything working together, but I done it in the end.
I solved my problem.

A heads up tip for all those having the same problem.



Great:

How did you get ubuntu to not interfere with the usbport??

I have an X125 and it can't keep a connection when I try it this way -- ubuntu interfers with it.

---

### Post by pod25 on 2006-09-19
> **tagra123 said:**
> Great:

How did you get ubuntu to not interfere with the usbport??

I have an X125 and it can't keep a connection when I try it this way -- ubuntu interfers with it.

Well during the setup it asks what you would like to include, in my case I told it usb support, so it assigned 2 out of my 6 usb ports, a bit like it does when assigning how much ram to set aside.

Then in vmware, across the top menu under VM/Removeable Devices I activated my printer.

---

### Post by tagra123 on 2006-09-19
Can you post a copy of the VMX file?

---

### Post by pod25 on 2006-09-19
> **tagra123 said:**
> Can you post a copy of the VMX file?

No problem !  Where will that file be ?

---

### Post by tagra123 on 2006-09-19
Its the actual virtual machine file. It should be in your home directory or a directory called vmware. 

I use the vmplayer I think the server works similar.

You can open it it a text editor -- this is how I edited my virtual machines for the vmplayer.

I think you can serch for it using 

PANEL MENU : Places > Search For Files  

and search for

*.vmx

---

### Post by pod25 on 2006-09-19
Here ya go 
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "224"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/hdd"
ide1:0.deviceType = "cdrom-raw"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
displayName = "Windows XP Professional"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d c3 5d 34 56 5d d0-cd 06 2d ff 7e c4 dc 62"
uuid.bios = "56 4d c3 5d 34 56 5d d0-cd 06 2d ff 7e c4 dc 62"
ethernet0.generatedAddress = "00:0c:29:c4:dc:62"
ethernet0.generatedAddressOffset = "0"

usb.autoConnect.device0 = ""

ide1:0.startConnected = "TRUE"
usb.autoConnect.device1 = "path:3/0 autoclean:1"
tools.syncTime = "FALSE"

```

---

### Post by tagra123 on 2006-09-20
Thanks.

I was using vmplayer and upgrade to the server since its now free too. Not a lot of difference from the server to workstation. What a great piece of software for free.

Added bonus: The server seem to be much faster than vmplayer.

X125 printing and scanning like a charm.

---

### Post by pod25 on 2006-09-21
Thats good to hear.
I was told having a setup like this drains the system of it's resources, but i've had no probs (as yet)

---

### Post by Kilz on 2006-09-21
I have a easier solution for a lexmark. The trash can, then buy a epson.

---

### Post by tagra123 on 2006-09-21
I kept the lexmark but I do have a HP Deskjet 3940 that I picked up. It was plug and play for ubuntu.

---

### Post by pod25 on 2006-09-22
> **Kilz said:**
> I have a easier solution for a lexmark. The trash can, then buy a epson.
I could agree with you there, but as mentioned before, I just bought it, plus the Lexmark p6350 is a damn good printer and cheaper than Epson.

---

### Post by nate3711 on 2007-01-17
> **pod25 said:**
> I bought myself a new printer, a *Lexmark*  Doh !!
I soon found out that lexmark do not support Linux (at least not very well).
I wanted my printer to be a network printer running off my ubuntu server machine.
So my perfect solution was :
I installed VMware onto my ubuntu server, then installed Windows XP into VMware, then networked my printer that way.
It was still a bit tricky getting everything working together, but I done it in the end.
I solved my problem.

A heads up tip for all those having the same problem.

So I've installed windows xp and got my lexmark x5270 printer installed. Windows shows that there are no problems but if I go to print a test page in Windows nothing prints. The status says it is but nothing happens. Also, just for future reference, if I network to the printer from Ubuntu, a driver is required before I can use it. How do I get around this since the driver I need does not exist?

Thanks,
Nate

---

### Post by pod25 on 2007-01-28
> **nate3711 said:**
> So I've installed windows xp and got my lexmark x5270 printer installed. Windows shows that there are no problems but if I go to print a test page in Windows nothing prints. The status says it is but nothing happens. Also, just for future reference, if I network to the printer from Ubuntu, a driver is required before I can use it. How do I get around this since the driver I need does not exist?

Thanks,
Nate

Ok, I am guessing you have 2 computers.
If so, this was meant for Windows to Windows networking.
In my case, I have my server running Ubuntu, on my laptop I have Windows.
The setup I did was on my server, with vmware and windows installed on there, then I networked to my Windows laptop.
Otherwise trying to network Windows to Ubuntu kinda defeats the object.
If you are using Ubuntu as your main OS on both computers, then you are going to have to do this vmware/windows on both computers.

Hope that helped.

---

### Post by neoaddict on 2007-02-04
I'm like nate3711, except I just have one computer with Ubuntu as host as Windows XP as guest.

I have the Lexmark X5270 too, and Windows says it detected the printer and tries to print the test page, but nothing happens - I suspect Ubuntu is intefering.

Anyway to stop it from interfering?

---

### Post by neoaddict on 2007-02-08
Bump.

---

### Post by univremonster on 2007-07-17
agreed regarding the trash can.  I have been working on getting my Lexmark to talk to my computer for months.  If anyone can solve this problem they should be nominated for UN rep. to the middle east way before Tony Blair.  

Your perfect solution isn't quite perfect for me for a few reasons.  (1) Using XP in any way shape or form doesn't sit well with me, likewise for emulators, it's much better to have a 'home-grown' solution and (2) I'm not using a server but I take it from those parts of the post which I did understand that this is an essential element of your solution.  

I'd be willing to look the other way about (1) if I could actually get the damn thing running, but (2) is a dealbreaker.  Any ideas?

---

### Post by NumberOne on 2007-07-17
I have a Lexmark E120N laserjet (ethernet conn), and I found a driver for Ubuntu with Google.  The printer works fine.

---

