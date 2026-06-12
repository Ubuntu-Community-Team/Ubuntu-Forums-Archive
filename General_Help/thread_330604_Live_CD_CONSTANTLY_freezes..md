---
title: "Live CD CONSTANTLY freezes."
date: 2007-01-03
forum: General Help
---

### Post by Rackerz on 2007-01-03
I have a serial ATA drive and when ever I use the live cd it always freezes while I'm using the CD. I've burned 3 times with different CD's and the ISO file is md5 checked. 

Why does it keep freezing?

---

### Post by earobinson on 2007-01-03
which version of ubuntu is the live cd?

---

### Post by haxer on 2007-01-03
Maybe slow cd? :-k

---

### Post by meng on 2007-01-03
> **Rackerz said:**
> I have a serial ATA drive and when ever I use the live cd it always freezes while I'm using the CD. I've burned 3 times with different CD's and the ISO file is md5 checked. 
What do you mean "while you're using the CD"? Are you booting from the CD, then taking it out and putting in another CD? More info please. System specs would help too.

---

### Post by Rackerz on 2007-01-03
I'm booting and running the live cd and trying to install. I'm not silly enough to take the disc out either. 

I have an Intel 975x motherboard (if that helps)
Intel Core 2 Duo E6600
1GB DDR2 RAM
Nvidia 6800 Ultra PCI-E
2 hard drives, 1 with 2 partitions. 

As far as I can tell, my system should be more than capable of running even the live cd. 

Cheers

---

### Post by wpshooter on 2007-01-03
Have you checked the CD by running the verification function found on the initial Ubuntu boot screen menu ?

Also have you ran the memtest function ?

---

### Post by Rackerz on 2007-01-03
I have. I also just found out that my motherboard has the jmicron chip for the SATA/IDE controller and it has problems in kernels below 2.6.18. It was meant to be fixed in Edgy, but well it looks as if it hasn't been.

---

### Post by wpshooter on 2007-01-03
I am not in front of my machine right now but is not the kernel for Edgy well beyond 2.6.18 now ?  Isn't it up to .27 I think ?

---

### Post by Rackerz on 2007-01-03
Well if so then I don't quite know why the CD freezes. My hard drives are fine, I've checked. 
Anyone have any ideas?

---

### Post by Delkster on 2007-01-03
> **wpshooter said:**
> I am not in front of my machine right now but is not the kernel for Edgy well beyond 2.6.18 now ?  Isn't it up to .27 I think ?

You may be thinking about the 2.4 series of kernels, which Ubuntu doesn't have. The 2.6 series hasn't even reached .27 yet. The latest stable release is 2.6.19, and .20 has had a couple of release candidates but no stable release yet. Edgy comes with 2.6.17. I don't know if it has been specifically patched for the problem with the SATA/IDE controller.

---

### Post by kebes on 2007-01-03
You may be experiencing a variant of this bug:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

Basically newer intel chipsets don't play well with anything but the newest kernel. Which means that if you can somehow manage to install Ubuntu and upgrade to the latest kernel, things will probably be fine. But getting to that stage can be a pain.

There are various kernel flags that you can pass before the install step (like "pci=nommconf" or "noapic") that work in many cases (refer to the link above). It's also possible that doing an install from a USB key, for instance, will sidestep the problem.

Another thing: in my experience with these intel chipset issues using the 'Alternate' Ubuntu install CD (instead of the normal LiveCD/Installer) helps, because it is a simpler text-only installer.

Also worth considering: Fedora Core 6 ships with kernel 2.6.18, which might work. This is what I had to do to get Linux installed on a piece of new hardware (even though I prefer Ubuntu).

---

### Post by Rackerz on 2007-01-04
> **Delkster said:**
> You may be thinking about the 2.4 series of kernels, which Ubuntu doesn't have. The 2.6 series hasn't even reached .27 yet. The latest stable release is 2.6.19, and .20 has had a couple of release candidates but no stable release yet. Edgy comes with 2.6.17. I don't know if it has been specifically patched for the problem with the SATA/IDE controller.

Apparently if it has been patched, it hasn't been done well. I'm hoping Feisty comes with a new kernel and a new fix.

---

### Post by Rackerz on 2007-01-04
> **kebes said:**
> You may be experiencing a variant of this bug:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

Basically newer intel chipsets don't play well with anything but the newest kernel. Which means that if you can somehow manage to install Ubuntu and upgrade to the latest kernel, things will probably be fine. But getting to that stage can be a pain.

There are various kernel flags that you can pass before the install step (like "pci=nommconf" or "noapic") that work in many cases (refer to the link above). It's also possible that doing an install from a USB key, for instance, will sidestep the problem.

Another thing: in my experience with these intel chipset issues using the 'Alternate' Ubuntu install CD (instead of the normal LiveCD/Installer) helps, because it is a simpler text-only installer.

Also worth considering: Fedora Core 6 ships with kernel 2.6.18, which might work. This is what I had to do to get Linux installed on a piece of new hardware (even though I prefer Ubuntu).

Thanks for the info :). I tried using the alternate cd (I prefer it) however it does not mount because of the chipset problem. Would I be able to enter those flags in the same way as a desktop cd?

---

### Post by kebes on 2007-01-04
> **Rackerz said:**
> Thanks for the info :). I tried using the alternate cd (I prefer it) however it does not mount because of the chipset problem. Would I be able to enter those flags in the same way as a desktop cd?

Yes you enter the flags before selecting "Install." So, wait for the install CD to boot up to the menu that gives you options (Install, memtest, etc.). Then you hit a key for "other options" (it's F6 or something like that) and you'll see a list of the current kernel boot options listed. To that add the ones you need to. Here are some that have helped me with similar issues in the past:

all-generic-ide
pci=nommconf
irqpoll
acpi=off
noapic
nolapic

You can issue multiple flags separated by spaces. You will probably have to experiment a bit with different combinations of flags (it's a bit different for every chipset, so I don't know about yours). Also, refer to the link I sent before and try some of the things they suggest (such as turning off "USB Legacy Support" in BIOS or whatever).

Also remember that if the install CD appears to freeze, you may still be able to go "Ctrl+Alt+F1" (try also Ctrl+Alt+F2, F3, etc.) and see the background output from the kernel. Those error messages may help you figure out what problem you're running into (hence know what kernel parameter to pass).


Are you trying to install from an IDE CD-ROM to a SATA hard drive? If so then with new Intel chipsets (which have removed on-board legacy IDE support!) you may end up having to install from a USB key or something. 


Lastly, it might be worth trying to install the development version of Ubuntu (Feisty Fawn):
[http://cdimage.ubuntu.com/releases/feisty/herd-1/](http://cdimage.ubuntu.com/releases/feisty/herd-1/)
This uses the newest kernel (2.6.20 I think) and should boot and install (may require kernel options "all-generic-ide pci=nommconf irqpoll"). This is, of course, an "unstable" version of Ubuntu... but if you're able to install it, this would be a useful clue (and perhaps once installed you could use it to downgrade to Edgy?).

---

### Post by Rackerz on 2007-01-04
I was thinking about Feisty earlier, but it's really early. I'll give those parameters a go now, see what works (if anything) and what doesn't. 

I'm trying to install from a SATA DVD to an IDE hard drive, I'm guessing there has been problems with this in the past? 

Thanks again :).

---

### Post by Rackerz on 2007-01-04
Ok, I tried all those parameters before booting the CD and well I'm talking to you from my Ubuntu installation :). Everything is working, none of my drives are missing, I suppose I'm just waiting for Ubuntu to freeze now. I'm gonna try and update now and see what comes of it, wish me luck and thanks again for all your help!

---

### Post by kebes on 2007-01-04
Excellent work! I'd be very interested to know exactly what combination of boot flags worked in the end... please post if you get a chance.

Now that you have a proper install you can upgrade to the latest kernel, too! Congrats!

---

### Post by Rackerz on 2007-01-04
Hey I'm back, with a still working Ubuntu :D. Got my graphics card drivers installed, updates done and no problems.

I wrote down all the flags you listed and was thinking of trying them one by one but I thought I'd just go for the whole thing. 

> all-generic-ide
pci=nommconf
irqpoll
acpi=off
noapic

However I missed out 'nolapic' because my hand writing is terrible and I couldn't remember if I put a 1 or an l. 

Once again thanks for all your help on this, I wouldn't of gotten very far otherwise :).

---

### Post by Mena.T.L on 2007-01-04
[COLOR=Red][B]What If You Make A Swap Partition .... Becuse This Was Happenng with me too ....

Accutly At the first time it run automatic with no errores and install it but i take the hard disk and put it in another one motherboard etc, and it didnt work ... then i found swap partition was made by the first instaltion and it was 705.98 MB ...[/B][/COLOR] 


**[COLOR=Blue] I know About the partition through[/COLOR]**[COLOR=SlateGray][COLOR=Blue][B]
System >>>Administration>>>Gnome Partion Editor

Then I found The Partition And Make It On 
By doing that 
Right Click On The swap Partion >>>  Choose Swap On 

After Doing That The live Cd Working Good And I had Install Ubuntu...
[/B][/COLOR][/COLOR]
** Thanks **
[B][COLOR=DarkOrange]
I hope I Give You The Solution And Plz If My Answer Was Wrong Or SOmething Was wrong Plz Tell Me Here 
[/COLOR][/B] 
[B] Thanks Again 

Mena
God Bless[/B]

---

