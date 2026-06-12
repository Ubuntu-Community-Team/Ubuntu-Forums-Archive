---
title: "Stylus Toolbox and path to printer"
date: 2016-07-05
forum: General Help
---

### Post by anon_private on 2016-07-05
Bus 003 Device 003: ID 04b8:0841 Seiko Epson Corp. PX-401A [ME 300/Stylus NX100]

andrew@andrew-Dell-DM061:~$  sudo vdir /dev/bus/usb/003/003

crw-rw-r--+ 1 root lp 189, 258 Jul  5 16:28 /dev/bus/usb/003/003

When I put this as a path into Stylus-Toolbox, I see

andrew@andrew-Dell-DM061:~$ stylus-toolbox

Reading device information ... 
sCommand="/usr/bin/escputil -q -d -r /dev/bus/usb/003/003"
Cannot write to /dev/bus/usb/003/003: Invalid argument

sCommand="/usr/bin/escputil -q -i -m escp2-sx100 -r /dev/bus/usb/003/003"
Cannot write to /dev/bus/usb/003/003: Invalid argument

---

### Post by X-RED_Tech on 2016-07-05
Stylus-toolbox is an outdated software. I'm surprised you were able to install it 14.04 because it has a dependency on HAL.
You need to use the current Epson driver for your printer. What functions it has or hasn't are the one you have to learn how to live with. Stop inventing before you break your system (if you didn't already).

---

### Post by anon_private on 2016-07-06
> **X-RED_Tech said:**
> Stylus-toolbox is an outdated software. I'm surprised you were able to install it 14.04 because it has a dependency on HAL.
You need to use the current Epson driver for your printer. What functions it has or hasn't are the one you have to learn how to live with. Stop inventing before you break your system (if you didn't already).

I installed the software without difficulty and my system works well. I can do as I please with my own technology.

CUPS is managing the printing, but I want to know the actual path from the disk to the printer.

---

### Post by X-RED_Tech on 2016-07-06
> **anon_private said:**
> CUPS is managing the printing, but I want to know the actual path from the disk to the printer.

Care to explain what path is that and why do you think you need it? The printer has a path like everything else in the system. what do you mean by the "actual path from the disk to the printer"?

---

### Post by anon_private on 2016-07-06
> **X-RED_Tech said:**
> Care to explain what path is that and why do you think you need it? The printer has a path like everything else in the system. what do you mean by the "actual path from the disk to the printer"?

The CUPS path to  the printer is:

usb://EPSON/Stylus%20SX100?serial=KQEZ387420&interface=1

I need an actual path for Epson toolbox so that it can check the cartridges etc. This path will be something that corresponds to folders on the hard disk; for example, /dev.../.../ etc

---

### Post by X-RED_Tech on 2016-07-06
You probably got the path to the printer right in the OP. I say probably because I have no printers attached to the PC I'm using right now so I can compare.

The reason why it isn't working is, again and for umpteenth time, because what you're looking for isn't (and never was) provided by the driver. You won't get anything from abandonware which is abandoned software, in this case abandoned in 2008. Why? Probably because whatever they did was made redundant by the driver and software provided by Epson.

Your stubbornness is becoming annoying. As you're probably still not convinced by now and we expect a new thread about it soon, be assured I won't reply again and ignore it like pretty much everybody else. That also should be a clue but some people don't get it...

---

### Post by anon_private on 2016-07-06
> **X-RED_Tech said:**
> You probably got the path to the printer right in the OP. I say probably because I have no printers attached to the PC I'm using right now so I can compare.

The reason why it isn't working is, again and for umpteenth time, because what you're looking for isn't (and never was) provided by the driver. You won't get anything from abandonware which is abandoned software, in this case abandoned in 2008. Why? Probably because whatever they did was made redundant by the driver and software provided by Epson.

Your stubbornness is becoming annoying. As you're probably still not convinced by now and we expect a new thread about it soon, be assured I won't reply again and ignore it like pretty much everybody else. That also should be a clue but some people don't get it...

I am pleased to learn that you will not be replying to my posts - don't change your mind.

---

### Post by QDR06VV9 on 2016-07-06
Let us try to get along here.(Both)
It is in the sprit of trying to help after all...enough said.

---

### Post by anon_private on 2016-07-06
> **runrickus said:**
> Let us try to get along here.(Both)
It is in the sprit of trying to help after all...enough said.

I have done absolutely nothing wrong.

However the comment 

' Your stubbornness is becoming annoying. As you're probably still not  convinced by now and we expect a new thread about it soon, be assured I  won't reply again and ignore it like pretty much everybody else. That  also should be a clue but some people don't get it...'

is offensive, and I have said so

---

### Post by lisati on 2016-07-06
Closed for staff review.

---

