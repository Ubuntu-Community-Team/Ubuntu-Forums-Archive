---
title: "Does ALDI block linux from being installed ???"
date: 2007-02-15
forum: General Help
---

### Post by Maxwell7 on 2007-02-15
Hi everyone, 

Last year my father bought a new desktop from ALDI . It is the first time we didn't buy our computer from a 'certified' retailer. But apart from a broken RAM chip everything went fine. Since it was a very powerful pc, I was curious to see if I could install Ubuntu on it. 

So I pop in the Live CD (I tried both edgy and dapper; both Kubuntu and Ubuntu) but all cd's hang after a while. So they do not ever start up. The same thing happens when I try to boot from the Knoppix live cd. It starts ok, then after loading some things it just completely stops. 

And I was patient ( i waited longer for this one then for my P I 133MHz). 

Could it be that the computers from ALDI are altered so that you cannot install any other OS on it then Windows ???   

That would really frustrate me ! ](*,) ](*,) #-o 

Greetings, 
Maxwell

ps : for those not familiar with ALDI, I do mean the german supermarket chain you find in western europe :)

---

### Post by austin on 2007-02-15
maybe you should start by doing a memory test (this tool can be reached from the first menu of all ubuntu cds as far as I remember)

---

### Post by ckempo on 2007-02-15
> **Maxwell7 said:**
> Could it be that the computers from ALDI are altered so that you cannot install any other OS on it then Windows ???

Nope. I have used Mepis, Foresight and three versions of Ubuntu on mine with no real problems.  Biggest issue I had was the TV card needed unplugging - something to do with the motherboard setup - but it's fine without.

You don't mention the spec of the machine you're trying - if you list it, maybe someone will spot an incompatibility.

---

### Post by Maxwell7 on 2007-04-07
OK, I finally found the time and the good mood to start fiddling with it again. This thing is really bringing me down. 

So here are the specs of the PC : 

*Medion 8800 
 intel Pentium D dual core processor 830
 3.0 GHz, 2x1 MB L2 cache, 800MHz FSB
 (they mention 64 bit support ? i think ...see below)

*1GB RAM DDR2 533MHz
 64 bits dual channel

*250GB HD 
S-ATA 150-interface

*NVIDIA GeForce 6700XL

*tv card, sony dual layer dvd burner, sony dvd rom, ...

Now I just noticed something that I hadn't paid attention to before. They mention somewhere in small print that this pc is "prepared for the future by 64 bits support". Does this mean that is actually is a 64bit CPU ? So that I would have to use the 64bit Ubuntu ? And not the normal ones that i tried? :confused: 

Darn, if that's the reason, i'd feel really stupid :"> 

Otherwise, does anyone spot any incompatibilities with Ubuntu ? 


All your help will be greatly appreciated. I really want to get Ubuntu running on this one, so that I can introduce my parents to the wonderful world of Linux. :guitar:

---

### Post by use a name on 2007-04-13
My experience with medion is real good, actually. I've got Ubuntu running on a medion laptop, also bought from Aldi. It did have bad memory too, so I called them, told I checked with an OS independent memtest, which was readily recognized as memtest86 (ok, is not linux only) and shipping was accepted immediately (they collect it).
I also asked what would happen to my partitions and I was told that it *might* be reset if necessary, but they would otherwise not touch it.
It only took one week, including shipment. Partitions untouched.

On to your problem:

It's indeed a 64 bit proc. I don't know if that makes it necessary to use the 64 bit Ubuntu disc. Anyone?

Do you get the boot menu at all? Do you get any messages on the screen when booting? Did you check the md5sum of the downloads? Have you tried any other bootoptions? (noapic, acpi=off)

---

### Post by Famicommie on 2007-04-13
I have a 64 bit AMD processor, but I prefer running 32 bit Ubuntu. You do not need to use 64 bit Ubuntu with a 64 bit processor. In fact, I recommend running 32 bit since 64 bit doesn't have good library support yet.

---

