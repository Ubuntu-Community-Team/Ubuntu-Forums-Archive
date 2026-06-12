---
title: "Best KDE distro"
date: 2007-07-22
forum: General Help
---

### Post by Sandwich on 2007-07-22
I'm looking for a really good, versatile and efficient KDE distro. I was having some difficultied with Kubuntu, so I was wondering what I should go for....i hear OpenSuse is pretty good...:confused:

---

### Post by stmiller on 2007-07-22
I actually like KDE on Fedora. Slick, clean, and polished.

Suse's package manager YAST is annoying to me, though they do default to a KDE desktop.

---

### Post by AlexenderReez on 2007-07-22
i suggest to try linux mint:)

---

### Post by strabes on 2007-07-22
I've heard that PCLinuxOS is the best KDE distro but I've never tried it myself. I use kubuntu without any problems.

---

### Post by tower_ on 2007-07-22
KDE Distribution, try ones: [www.kanotix.com](www.kanotix.com) or [www.sidux.com](www.sidux.com) there have realy good hardware recognition and are also live-cd's with installer and based on debian or see "debian-live" see [http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/) :-)

---

### Post by mikewhatever on 2007-07-22
> **Sandwich said:**
> I'm looking for a really good, versatile and efficient KDE distro. I was having some difficultied with Kubuntu, so I was wondering what I should go for....i hear OpenSuse is pretty good...:confused:

This is kind of vague. Can you explain what best is in your opinion.

---

### Post by Sandwich on 2007-07-22
Thanks for the advice, I'll check all those out.

> **mikewhatever said:**
> This is kind of vague. Can you explain what best is in your opinion.

Really versatile, easy to use, compatible with lots of stuff, and powerful and efficent.

---

### Post by userundefine on 2007-07-22
You just described Kubuntu, IMO.  What were your problems with it?

---

### Post by Sandwich on 2007-07-22
Errors when booting of CD (almost every time) soemthing to do with some timer and something called IO_APIC. :confused:

---

### Post by userundefine on 2007-07-22
Ah, so an installation issue before you ever got to desktop?  Bad burn, maybe?  Did you check the sums of the ISO?  You may give the alternate install disk a try as well.

---

### Post by mikewhatever on 2007-07-22
> Really versatile, easy to use, compatible with lots of stuff, and powerful and efficent.Since errors free is not in the list, Kubuntu it is.

---

### Post by Sandwich on 2007-07-23
lol^^

> **userundefine said:**
> Ah, so an installation issue before you ever got to desktop?  Bad burn, maybe?  Did you check the sums of the ISO?  You may give the alternate install disk a try as well.
Thanks, I'll give that a try.

---

### Post by misfitpierce on 2007-07-23
If you cant get kubuntu going I would try linux mint for KDE as they are derivatives of ubuntu

---

### Post by Dokatz on 2007-07-23
> **stmiller said:**
> I actually like KDE on Fedora. Slick, clean, and polished.

Suse's package manager YAST is annoying to me, though they do default to a KDE desktop.

I can echo Fedora. Best KDE distro I've used so far...But then again I haven't used many.

:lolflag:<---Why does he have goku's hair?

---

### Post by gabhla on 2007-07-23
I'd say PCLOS. Another good one is Mepis.

---

### Post by Gruelius on 2007-07-23
I really liked Kubuntu. THe package managment is great, i havent used another K distro for a long while tho. I tried to install suse 10.2 however the installer crashed and i gave up. 

Sounds like your disc may be a bad burn, that was a good idea to check that.

---

### Post by Sandwich on 2007-07-23
Making a new one right now. :)

---

### Post by Sandwich on 2007-07-23
Still won't work. Reburned it and same thing. Some error 8254 and it suggests to try "noaptic" kernel mode. :confused:

---

### Post by Sandwich on 2007-07-23
Ok so I narrowed the selection down to Echo Fedora
PClinuxOS (maybe)
Mepis
Linux Mint
and KDE Fedora

---

### Post by notwen on 2007-07-23
+1 sidux

---

### Post by Sandwich on 2007-07-23
Sidux, eh?

..Is there a way do disable all that animated stuff in PClinuxOS and other OSs using the same animation thingys (dunno what it's called...window manager?).

---

### Post by Crakie on 2007-07-23
What kind of hardware are you using? Particularly your motherboard and the Sata/Ide controllers on it are interesting. At the very least try booting with any combination of acpi=off noapic nolapic pci=biosirq as kernel parameters, while using the alternate CD (burned at 4x and checksum verified).

---

### Post by NilsHG on 2007-07-23
PC-BSD 
I know I know, it is not Linux. It is based on FreeBSD but it is a really nice system. 1.4 Beta has been released recently. You might want to give it a try.
*edit* [http://www.pcbsd.org/](http://www.pcbsd.org/) */edit*

---

### Post by Sandwich on 2007-07-23
Thanks for the link.

> **Crakie said:**
> What kind of hardware are you using? Particularly your motherboard and the Sata/Ide controllers on it are interesting. At the very least try booting with any combination of acpi=off noapic nolapic pci=biosirq as kernel parameters, while using the alternate CD (burned at 4x and checksum verified).

Me no know how.

---

### Post by Crakie on 2007-07-24
> **Sandwich said:**
> Thanks for the link.



Me no know how.

* Download the alternate install CD
* Burn it as the lowest speed you can (2x or 4x, 8x if you must)
* Reboot from it
* When greeted by a little menu, select the 'boot options' (F6? I forgot the exact name, it should be pretty obvious though)
* From the options it presents, remove the 'quite', 'splash' and '--' option. This will give you a lot more output for debugging
* Add: noapic nolapic acpi=off pci=biosirq
* Boot and cross fingers :-\"

---

### Post by Sandwich on 2007-07-25
Ok, thanks.

---

