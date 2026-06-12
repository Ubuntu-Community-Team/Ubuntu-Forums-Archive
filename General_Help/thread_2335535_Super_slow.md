---
title: "Super slow"
date: 2016-08-29
forum: General Help
---

### Post by matt18 on 2016-08-29
Ello All:)

I have a intel p4 hyerthreading with 3.20 ghrz cpu, 2 gb ddr2 ram, and a 500 gb 7200 rpm WD HDD. I am running ubuntu 14.04(i686) with cinnomin as my DE. 

I have a 1gig swap as well. ALl i can say is that this PC is SLOW. youtube does not play well at all. its plays about 2 seconds, then video pauses but sound continues, then after about 5 seconds, another short burst. Facebook is sloooww. Most blogs and pinterest are sloow. applications are slow as well but not crawling speeds but just slow. 

I have no idea why either. System monitor shows all normal signs and behavior. no spikes in CPU or MEM. 

GPU is onboard AMD/ATI RC410 RADON EXPRESS

thanks

---

### Post by Jimysbil on 2016-08-29
I think the problem could be a GPU driver or a faulty hardware (Probably your AMD).
It could also be your low ram.
Your processor on the other hand is good enough.
Have you fglrx driver installed??
You may check [here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") how to install it.

---

### Post by QIII on 2016-08-29
Hello!

The fglrx driver suitable for that card has not worked with Ubuntu since some time in 2009.  AMD stopped maintaining it for cards that old and that version will not work with versions of X Server since then.

Furthermore, if you are using 16.04 or later, fglrx is not available and cannot be installed.

That is an old GPU from before AMD bought ATI.  It is very underpowered for Unity and, running the Radeon driver, I'm not surprised you are having problems.

You might get better performance using a lighter flavor such as Xubuntu or Lubuntu.

---

### Post by RobGoss on 2016-08-29
Have you try a lighter version of Ubuntu? maybe the 14.04 maybe to heavy for that machine. Try [Lubunt]("http://lubuntu.net/")[u ]("http://lubuntu.net/")it's light and fast for machines with less resources

---

### Post by Geoffrey_Arndt on 2016-08-29
My son has a very similar system . . . Xubuntu 16.04 runs very snappy . . . no delays, no issues with Youtube at all.

BTW . . . best to stick with the default DE in Ubuntu, Xubuntu, Mate, etc. etc. etc.    XFCE has turned out to give the "best bang for the buck" in Linux DE's.   Stable, fast, customizable.    My 2econd favorite DE after Unity - (which are on newer machines only).

---

### Post by matt18 on 2016-08-31
> **QIII said:**
> Hello!

The fglrx driver suitable for that card has not worked with Ubuntu since some time in 2009.  AMD stopped maintaining it for cards that old and that version will not work with versions of X Server since then.

Furthermore, if you are using 16.04 or later, fglrx is not available and cannot be installed.

That is an old GPU from before AMD bought ATI.  It is very underpowered for Unity and, running the Radeon driver, I'm not surprised you are having problems.

You might get better performance using a lighter flavor such as Xubuntu or Lubuntu.

i am not running unity:) never have with ubuntu because of how much it hogs. I am actually running Cinnamon. Though that is a nive looking DE it may be stressing my GPU that is under powered. 

I was hoping 2 gigs of ram was good enough for this system. Its used for basic stuff, like youtube, email, facebook, but is having issues with all of that:) 

thanks

---

### Post by matt18 on 2016-08-31
> **RobGoss said:**
> Have you try a lighter version of Ubuntu? maybe the 14.04 maybe to heavy for that machine. Try [Lubunt]("http://lubuntu.net/")[u ]("http://lubuntu.net/")it's light and fast for machines with less resources

thought about it BUT i dont want to re-install again. If there is anything i can disable, i will do that. I may have to install another DE. It just needs to look nice is all. i dont want it to look like win 3.1 haha. i would like it to look modern. thats why i like cinnomin

i have cario dock installed and my DAD LOVES IT!!! haha

should i install XFCE4 from the ubunut software center or is there a better way?

thanks

---

### Post by mörgæs on 2016-09-04
Did you find a solution?

---

### Post by Bucky Ball on 2016-09-04
Not sure if you saw this, but pretty much says it all.

> **QIII said:**
> Hello!

The fglrx driver suitable for that card has not worked with Ubuntu since some time in 2009.  AMD stopped maintaining it for cards that old and that version will not work with versions of X Server since then.

Furthermore, if you are using 16.04 or later, fglrx is not available and cannot be installed.

That is an old GPU from before AMD bought ATI.  It is very underpowered for Unity and, running the Radeon driver, I'm not surprised you are having problems.

You might get better performance using a lighter flavor such as Xubuntu or Lubuntu.

Your messed up graphics would be effecting all sorts. I was running Xubuntu 14.04 on a P4 3Ghz with 1Gb of RAM with no issues whatsoever, but I didn't have that dog's breakfast graphics card set up. Not just old, obsolete unfortunately. :|

As QIII says, you might get a better experience with a lighter flavour to start with. You also might not. Even though you're using a lighter DE, doesn't mean much. You still installed a full Ubuntu along with all the default bloat you don't need and will probably never use. Still a resource hog. It's not all about the DE. :)

You're only option with this card is probably to use the open-source nouveau driver, which you probably already are. Issue this in a terminal, hit 'enter' and check at 'driver=' in the output.

```
sudo lshw -C video
```

---

### Post by matt18 on 2016-12-31
*-display               
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200/1100]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:17 memory:d0000000-d7ffffff ioport:ec00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff

---

### Post by mörgæs on 2017-01-01
When Bucky Ball wrote 

> Your only option with this card is probably to use the open-source nouveau driver

I think he meant Radeon, which is what you use. 

You could try installing a minimal Buntu in a dual boot with the present one, for example using this guide:
[https://ubuntuforums.org/showthread.php?t=2346891](https://ubuntuforums.org/showthread.php?t=2346891)

This will give you two operative systems for comparison. 


By the way, a moderator could consider merging the two threads on the same or almost-the same problem.

---

