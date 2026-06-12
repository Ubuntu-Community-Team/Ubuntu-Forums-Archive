---
title: "Live CD won't show graphics on ATI X850 PCIE"
date: 2005-06-25
forum: General Help
---

### Post by AJI on 2005-06-25
I booted the Kubuntu 5.04 live CD, and all the lines were [OK].  After a moment of blank screen, I got the command prompt.

Following another thread, I tried "startx", but that gave me some errors.  After figuring out how to copy from one Linux box to another, here's the relevant part of the /var/log/Xorg.0.log:

(II) Primary Device is: PCI 05:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X850 Pro (R480)".
(II) ATI:  Unshared 8514/A not probed.
(II) ATI:  Unshared Mach64 at PIO base 0x02EC not probed.
(WW) ATI:  PCI Mach64 in slot 5:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 5:0:1 will not be enabled
 because it conflicts with another non-video PCI device.
(EE) No devices detected.

Fatal server error:
no screens found

My system is a brand-spanking new AMD Athlon64 3200+, with an ATI Sapphire X850Pro video card connected by PCIExpress.

[This thread on Debian.org](http://http://lists.debian.org/debian-user/2004/10/msg03060.html) suggests loading agpgart before loading X.  Sounds great, but **how do I do that with a Live CD?**  Is there something else I should do?

---

### Post by askreet on 2005-06-25
I'm having the same problem with the installation of Ubuntu and my X850XT -- How would loading AGPgart help in any way control a PCIe card? *scratches head*

---

### Post by deltwalrus on 2005-10-29
I am having the exact same problem.  I just downloaded the latest Live CD for AMD64.  I have an X850XT PCI-E video card, and when it tries to start the X server, it tells me:

```
(EE)  No devices detected
Fatal server error:
no screens found
```

Has anyone been able to find a workaround for this?  I'm itching to dump Windows and try Ubuntu, but this is a dealbreaker.  If it won't see my video card.....  :(

---

### Post by sanzo on 2006-01-15
So do i.
Fatal server error:
no screens found

I can read in /var/log/Xorg.0.log grepping (EE):
(EE) No devices detected

and grepping (WW) :

(WW) ATI: PCI Mach64 in slot 5:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 5:0:1 could not be detected!

I have a X850XT. I'm trying ubuntu 5.10 livecd 32 and 64 bit ... but nothing.
But i'm a noob on linux, if you can solve the problem... pleeeeease :rolleyes: :cool:

---

### Post by IconK7 on 2006-02-03
Just tried Ubuntu 5.10, both 32bit and 64bit, both live and hdd install, same result as above. Have ATI X800XL on pcie 16 slot. Took the trouble to remove all removable pci devices, no change. The first attempt corrupted both my hard drives and forced me to Re-Format & Re-Install (sound familiar?) both My WinXP and Mandriva 2006 installations. Many WASTED hours.
    I would greatly appreciate any help on this, as long as it comes in this format:

1: THIS is what's going wrong.
2: THIS is what fixes it.
3: NOW it is JUST WORKING AS ADVERTISED.

    I am totally disillusioned with all Linux 'distros'. The massive amount of problems each and every Linux Distro brings with it are equal to the massive amount of problems each and every Windows Distro brings with it. The only advantage Ubuntu has over Windows is the MASSIVE amount of money Windows rips from all of us. 
    I expect the Microsoft Monopoly to lie & cheat at every turn. I want better from Linux. 
    Do NOT tell me that you have an Operating System that works. You do not. Do NOT tell me that you have an Operating System that works with my new & EXPENSIVE 64-bit hardware. You do NOT. Microsoft does NOT have it, and neither do you.


                                                          - IconK7

---

### Post by clarkee on 2006-07-04
This is a working OS.  Maybe you are the disillusioned one who believes that everything must work first time every time.  Here's a hint - nothing does.  RTFM.

---

### Post by CuBone on 2006-07-07
Maybe you could give som e hints on how to fix this instead of being an arse. I'm trying to test Linux for the first time but I get the same errors as the thread composer. I've tried LiveCD and HDD installation and tried alot of tips from different sources on how to get the graphics running but nothing seems to do the trick. 
Änyone have any ideas?

](*,)

---

### Post by James^H on 2006-07-08
> **CuBone said:**
> Maybe you could give som e hints on how to fix this instead of being an arse. I'm trying to test Linux for the first time but I get the same errors as the thread composer. I've tried LiveCD and HDD installation and tried alot of tips from different sources on how to get the graphics running but nothing seems to do the trick. 
Änyone have any ideas?

](*,)
I was going to register to say the same thing.

Anyway, I am having the *same* problems with installing ubuntu 6 on an x850xt, get the exact same error message.

Now, smart-asses say to provide the error output, but considering this is an INSTALL problem and not once into ubuntu, then it makes it fairly difficult as far as I can see to save the output.

If its possible to put it onto a floppy or whatever then fine, I can cp stuff no probs, where would the output be kept?

I can see that this is a known problem with x series cards, but how can we edit configs to sort it out? Does it mean going through the ISO and editing files or what? I only have XP running to do that with.

Anyway, I had ubuntu running on my 9500 Pro last year for a brief time and I know ATI in linux is crap, but I'd prefer not to build a second pc just for this, although I may in the future anyway.

---

### Post by James^H on 2006-07-08
> **clarkee said:**
> This is a working OS.  Maybe you are the disillusioned one who believes that everything must work first time every time.  Here's a hint - nothing does.  RTFM.

FYI XP has NEVER given me install problems ever, and this is on 50+ different machines of all specs. Something must be generically wrong if you find that nothing works first time.....

---

### Post by James^H on 2006-07-08
[http://ubuntuforums.org/showthread.php?t=190133&highlight=x850](http://ubuntuforums.org/showthread.php?t=190133&highlight=x850)

Going to give it a go when I get home later.

EDIT:

All up and running after a bit of tweaking, had to mess around with refresh rates too but got there in the end.

---

