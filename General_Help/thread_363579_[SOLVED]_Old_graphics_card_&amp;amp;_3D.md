---
title: "[SOLVED] Old graphics card &amp;amp; 3D"
date: 2007-02-17
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-02-17
I have an old Intel with what I think is the i810 chip/graphics. I can not get thing like Google Earth and some screen savers to work due to this old card. How can I get drivers, etc. I see all this talk about ATI drivers and such, but what will my system require to get better graphics (3D) Please provide code for me to give more info on my machine if it will help, thanks, Sally

---

### Post by an.echte.trilingue on 2007-02-17
will you let us see the output of lspci, please?

Thanks
-mat

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
> **an.echte.trilingue said:**
> will you let us see the output of lspci, please?

Thanks
-mat

00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:07.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
:popcorn:

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
Sorry to "Bump" again but I would like some help please :)  Sally

---

### Post by Maestro23 on 2007-02-17
> **MustangSallydd said:**
> Sorry to "Bump" again but I would like some help please :)  Sally

Does your system meet the min req for running a program like google earth: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

What are your system specs?

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
> **Maestro23 said:**
> Does your system meet the min req for running a program like google earth: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

What are your system specs?

Specs are in beginning of thread, Thanks for reply, Sally ** EDIT:** if yo require more specs, please provide code for me to obtain them from terminal :)

---

### Post by Maestro23 on 2007-02-17
> **MustangSallydd said:**
> Specs are in beginning of thread, Thanks for reply, Sally ** EDIT:** if yo require more specs, please provide code for me to obtain them from terminal :)

What kind of processor? How much RAM? Hard Drive size? etc...  Sounds like the graphics card is an integrated one, so it will use some of your RAM to process the graphics.  Stuff like google earth, Ubuntu eye-candy is not going to run or if it does, it will be like watching a slideshow.

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
> **Maestro23 said:**
> What kind of processor? How much RAM? Hard Drive size? etc...  Sounds like the graphics card is an integrated one, so it will use some of your RAM to process the graphics.  Stuff like google earth, Ubuntu eye-candy is not going to run or if it does, it will be like watching a slideshow.

It's an Intel Celeron w/40GB hard drive and I think it's got 348 or (close to it) RAM. And yes google earth is "jumpy" and freezes. But can't I change driver or some thing. Also what is the code to find RAM and related specs, thanks for your input, Sally

---

### Post by glotz on 2007-02-17
Try

**cat /proc/cpuinfo**

and

[B]cat /proc/meminfo | grep MemTotal
[/B]

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Celeron (Coppermine)
stepping        : 10
cpu MHz         : 1096.745
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 2195.13
clflush size    : 32
 cat /proc/meminfo | grep MemTotal
MemTotal:       254608 kB:::: Some one care to explain for me please?

---

### Post by glotz on 2007-02-17
Well, it's a 1100 MHz celeron (half cache) processor [http://en.wikipedia.org/wiki/Celeron#Coppermine-128](http://en.wikipedia.org/wiki/Celeron#Coppermine-128)

And you've got 255 megs of memory. This is probably limiting your performance. (Besides the video and the half cache.)

I really can't answer your original question though...

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
> **glotz said:**
> Well, it's a 1100 MHz celeron (half cache) processor [http://en.wikipedia.org/wiki/Celeron#Coppermine-128](http://en.wikipedia.org/wiki/Celeron#Coppermine-128)

And you've got 255 megs of memory. This is probably limiting your performance. (Besides the video and the half cache.)

I really can't answer your original question though...

Thank you, so I gather that getting google earth is out the question? Any way to update the graphics card?

---

### Post by IusedTObeSOMEONEelse on 2007-02-18
oOP's Bump  :popcorn:

---

### Post by Pelekophori on 2007-02-18
I assume that the computer is a desktop rather than a laptop.  If so you should be able to purchase a separate graphics card which will be more powerful than the inbuilt graphics.  However I suspect that the computer may not have the kind of interface slot which current graphics cards expect.  If so you may find it slightly difficult to get a compatible graphics card new.     You could take it to a local computer shop for advice, or, if you are confident about identifying the interface (probably AGP), you should be able to pick up something appropriate from Ebay.

I think the available Linux drivers will cover most ATI/NVIDIA cards you might come across in your search, but when you do settle on a card, you should also do a bit of googling to double check for that card.

---

### Post by IusedTObeSOMEONEelse on 2007-02-18
Maybe it's me, but I'm not hearing what I'd like to hear!! Any suggestions please? Sally:(

---

### Post by Maestro23 on 2007-02-18
> **MustangSallydd said:**
> Maybe it's me, but I'm not hearing what I'd like to hear!! Any suggestions please? Sally:(

Updating the graphics card as suggested above will be your best bet.  Today's 3D-apps are not going to run smooth with that combination of processor, RAM, and integrated video card.  No new driver is going to improve the performance a great deal either.

If you are thinking about upgrading, you need to find out what kind of video slot is on the motherboard of the computer.  More RAM would not hurt either. Then start looking at video cards.

---

### Post by IusedTObeSOMEONEelse on 2007-02-18
> **Maestro23 said:**
> 

If you are thinking about upgrading, you need to find out what kind of video slot is on the motherboard of the computer.  More RAM would not hurt either. Then start looking at video cards.

Thanks for the reply! How do I find out what kind of "video slot" I have? Would there even be one on this machine? :confused:

---

### Post by Maestro23 on 2007-02-18
> **MustangSallydd said:**
> Thanks for the reply! How do I find out what kind of "video slot" I have? Would there even be one on this machine? :confused:

Who makes the laptop?  Find that out, then you can google for the manufacturer's website and get some specs on the system.

---

### Post by IusedTObeSOMEONEelse on 2007-02-18
It's a desktop, Dell with Intel motherboard. I believe the specs were earlier posted. Thanks for your help.

---

### Post by Maestro23 on 2007-02-18
> **MustangSallydd said:**
> It's a desktop, Dell with Intel motherboard. I believe the specs were earlier posted. Thanks for your help.

Then you should be able to go to Dell's website and find out what is under the hood. Motherboard type, how many memory slots, video card slot type, etc...

Should be able to go there and look up your model number and find it.  If they still support it.

Good luck.

---

### Post by IusedTObeSOMEONEelse on 2007-02-18
Thank you, Sally

---

