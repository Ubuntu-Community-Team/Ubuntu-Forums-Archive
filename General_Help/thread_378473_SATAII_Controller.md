---
title: "SATAII Controller"
date: 2007-03-07
forum: General Help
---

### Post by RichGuk on 2007-03-07
Hello,

Wondering if anyone can recommend a 4 port SATAII controller for my Kubuntu (Edgy) box. Software RAID is fine, I'm looking to add to a current JBOD but I don't have any SATA ports left on the motherboard.

By the way, I live in the UK, all I could find were things like the Adaptec AAR-1420SA from [Overclockers UK]("http://www.overclockers.co.uk/showproduct.php?prodid=CC-022-AD"), does that even work under Ubuntu?


Thanks,

Rich

---

### Post by RichGuk on 2007-03-07
*bmp*

---

### Post by Redeyes_Gambit on 2007-03-07
[COLOR="Silver"]I know that I CAN NOT recommend the Promise SATA300 TX2plus controller. I'm STILL trying to compile the driver for that thing. The instructions are all in red-hat-ees and these very forums, which are usually quite helpful, have not been able to rectify my issues[/COLOR].** -No longer true. See my post below.**

The support on the promise site you say? Guess what, the site requires IE 5+. So much for support.

---

### Post by RichGuk on 2007-03-08
Not the one to go for then :). I stil need drivers if I'm not going to use the hardware raid feature? Just basically want extra sataII ports (4 more in fact :P).

---

### Post by Nemix77 on 2007-03-08
got Promise SATA300 TX4 running fine on edgy out of the box...

---

### Post by RichGuk on 2007-03-08
What about the Highpoint Rocket Raid 1740LF? Work under ubuntu? :p

---

### Post by Redeyes_Gambit on 2007-03-09
Not sure. Oh, as for your question about whether or not you can use the ports; no, without drivers you cannot use the SATAII ports. The tx2 plus actually has 2 SATAII ports and 1 IDE port. The IDE port is functional but not the SATAII ports. Lol, don't ask me why. When you plug in SATA drives they just plain don't show up.

When it comes to buying a RAID card there are a few things to keep in mind:

1. If you plan on using it in a RAID mode, just about any card under $100 is going to be a SOFTWARE or FAKE RAID card. In other words the CPU is going to have to handle a lot of the RAID duties, the card just makes it possible. 

A HARDWARE RAID card is better because the card is actually what is doing all the RAID related stuff. This results in higher speeds. If you can get your hands on the manual to the card before you buy it (the website for the manufacturer probably has the manual in a PDF format) you can tell if the card is a fake RAID or a true hardware RAID. If the instructions specify that you should set options for RAID in a BIOS or pre-OS screen, then chances are its a true hardware RAID array. If the array is set up using software in Windows/Linux then chances are it's a fake/software RAID array.

2. If the card specifies Debian as an OS it supports then chances are it will work in Ubuntu. If you can get your hands on an Ubuntu .deb package of the driver then you have found a miracle card and should buy it post-haste ;) .

3. If you have to compile the drivers from source be ready for a nightmare lol.

---

### Post by RichGuk on 2007-03-09
Ah, sounds like fun.

I don't even want hardware RAID...already got linear via mdadm I basically just want to expand on that if possible but I've run out of ports.

Quite a limited choice, lol.

Thanks for the info though (y)

---

### Post by Redeyes_Gambit on 2007-03-10
AHA! I found a page that lists supported SATA chipsets for Linux:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

Now you just need to find out what chipset each card you're looking at uses :rolleyes:

---

### Post by Redeyes_Gambit on 2007-03-18
Well I'll be dipped in Ubuntu!

I CAN recommend the promise SATA 300tx2 plus card! All the time I spent trying to compile a driver could have been saved IF I HAD JUST CHECKED THE SATA POWER CONNECTOR!!!!! Silly thing was mis-wired (Doh!) Now my drives are recognised, installed, RAIDed and formatted! Works like a charm.

---

### Post by borahshadow on 2007-06-16
I'm wondering about buying a SATAII controller card is[this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816102061") the card that you thought you were having trouble with? or [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816102064") other then price and reviews they look identical but they have different item #s

and just to clarify you would recommend this? what version of Ubuntu are you running?
thanks

---

