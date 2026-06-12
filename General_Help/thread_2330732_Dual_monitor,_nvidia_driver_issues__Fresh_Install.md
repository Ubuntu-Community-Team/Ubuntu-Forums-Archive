---
title: "Dual monitor, nvidia driver issues | Fresh Install"
date: 2016-07-14
forum: General Help
---

### Post by blackhawk871 on 2016-07-14
Hey team,

Over the past four days I have frantically trying to install Ubuntu 16.04 onto my hard drive so that I can dual boot that and Windows. I've managed to install it a few times now and each time I run into a few deal breaking issues. 

Firstly, using the default nouveau graphics drivers I am able to have both of my monitors plugged in via DVI and working (although the mouse is flickery and disappears a little), however as soon as I install the NVIDIA drivers (any version that is and with secure boot disabled) Ubuntu can only detect one of the monitors and when I activate the other one in Nvidia X Server Settings (which does detect it), it turns on but remains black (I can move my mouse onto it but it displays a big X). I have tried follow some tutorials online but had no success.

My current GPU setup is as follows: I currently have one GTX 690 (Part Number: 04G-P4-2690-KR), although from what I understand the GTX 690 has two chips on the one card so it may be that Ubuntu is treating it as two cards (in NVIDA X-Settings it does state GPU 0 and GPU 1). The 690 is plugged into the first PCI slot on my motherboard. In terms of the inputs the back of the 690 has three DVI slots (see [http://images10.newegg.com/ProductIm...130-781-10.jpg]("http://images10.newegg.com/ProductImage/14-130-781-10.jpg") for reference). My individual setup is that I have a DVI cord coming from each monitor into the two DVI slots on the same level (pictured[https://goo.gl/photos/3GMAUdoKnxw1fUYX9](https://goo.gl/photos/3GMAUdoKnxw1fUYX9)). In terms of configuration, they have just been plugged in and then had the drivers installed. 

To combat these I have tried reinstalling 16.04 twice, trying 14.04 and even trying Fedora 24 Workstation, but the problems remain persistent across all operating systems. Furthermore, I have tried numerous online solutions for each problem with no avail.

My current hardware is:
[LIST]
[*]CPU: i5 6600k
[*]Motherboard: ASUS Maximus VIII Hero
[*]RAM: 16gb Corsair LPX 3200Mhz
[*]Sound Device: Realtek HD Audio
[*]GPU: GTX 690
[/LIST]

I'd love to get Ubuntu working so that I can use it as my OS for developing on (I am a university student). 

Let me know if you have any ideas or need anymore information. The current OS I have installed is Fedora so if you need Linux information I can use that or reinstall to Ubuntu. I'd prefer to be running Ubuntu in the end.

---

### Post by blackhawk871 on 2016-07-14
As an update, I have now reinstalled a fresh version of Ubuntu 16.04 LTS onto my machine. I'll wait to make any changes.

---

### Post by Bashing-om on 2016-07-14
blackhawk871; Hello;

What driver and from which source(s) are you installing ?
Nvidia recommends the 367 version driver for the GTX 690 .
That driver is available in 16.04 from our trusted PPA.
Do you want to try it and see what now results ?

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by blackhawk871 on 2016-07-14
First of all thanks for the reply.

So far I have tried the drivers directly through the "Additional Drivers" part of Linux what didn't work out. I then on another install tried the drivers by adding the PPA repository what produced the same result. I can give it another crack, but I do believe I have already covered the "try a different driver" bases.

What are your thoughts?

---

### Post by Bashing-om on 2016-07-14
blackhawk871; Well ..

My thought remains the same .. to install the PPA and try the 367 version driver .
But that is your call IF you are comfortable with installing the PPA and running proprietary software on your system .
Graphic's driver make a world of difference.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by blackhawk871 on 2016-07-14
Fair enough. I'll definitely give 367 a try from the PPA repository and report back.

---

### Post by blackhawk871 on 2016-07-15
I installed 367 from the PPA repository and am still running into the same issues.

---

### Post by Bashing-om on 2016-07-15
blackhawk871; Well, that ^ ain't good .

Let's look and see what the system reports for the status of X :
```

cat /var/log/Xorg.0.log

```

The driver found and accepted ? :
```

cat /var/log/gpu-manager.log

```

What is reported for the display status ? :
```

cat .xsession-errors

```

now we see where we go from these.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by blackhawk871 on 2016-07-15
Xorg.0.log: [http://pastebin.com/wM6nzxy5](http://pastebin.com/wM6nzxy5)
gpu-manager.log: [http://pastebin.com/HvB6paYc](http://pastebin.com/HvB6paYc)
cat .xsession-errors from ~ outputs:

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0

```

---

### Post by Bashing-om on 2016-07-15
blackhawk871; Yuk;

I am stumped here also.
The system does see that card as 2 individual intities:
> 
19.554] (--) PCI:*(0:3:0:0) 10de:1188:3842:2690 rev 161, Mem @ 0xde000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ [color=red]0x0000d000/128[/color], BIOS @ 0x????????/524288
[    19.554] (--) PCI: (0:4:0:0) 10de:1188:3842:2690 rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/134217728, 0xc8000000/33554432, I/O @ [color=red]0x0000c000/128[/color]

occupying  2 buss positions. And the system happily builds the 367 version driver .
It is above my skill set to tell the system what is taking place here.
Perhaps others here will jump in and tell us what is going on and how to tell the system.

[INDENT][INDENT]one of those times
[INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by blackhawk871 on 2016-07-15
I see. Thanks a bunch for trying to help out anyway. I guess I can always revert back to the Nouveau drivers and put up with the flickering, but it would be preferable to be using the NVIDIA drivers. I'll wait to see what others say.

Appreciate the help so far!

---

### Post by blackhawk871 on 2016-07-18
Still looking to get this fixed if anyone has any ideas.

Edit: I have managed to work this out by changing the DVI port of the second monitor into another port. I believe this is a 690 only issue but it appears that you need to use these two on Ubuntu for multi monitors to work.

These two: [http://cdn.overclock.net/7/7e/7e09887f_ZlAs.png](http://cdn.overclock.net/7/7e/7e09887f_ZlAs.png)

This is now solved!

---

### Post by Bashing-om on 2016-07-18
blackhawk871; Well !

I would never have thunk it ... very pleased you provided the resolution.
I will keep the pinning under advisement for the future.

[INDENT][INDENT]what were they thinking
[/INDENT][/INDENT]

---

