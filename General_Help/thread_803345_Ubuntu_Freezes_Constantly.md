---
title: "Ubuntu Freezes Constantly"
date: 2008-05-22
forum: General Help
---

### Post by somody on 2008-05-22
Hey guys,

I have managed to overcome my other problem, and I'm now running a fully-functional Ubuntu system.

However, I have another problem now!  Every 5 minutes or so, everything freezes, random pixels turn green, then the screen goes black, and I have to reset the computer.

Any ideas?

--CS

---

### Post by danwood76 on 2008-05-22
What is your system spec?
(CPU, RAM, Graphics, HD, etc)

---

### Post by somody on 2008-05-22
> **danwood76 said:**
> What is your system spec?
(CPU, RAM, Graphics, HD, etc)
CPU = AMD Athlon 64 5000+ (2.60 GHz)
RAM = 2 GB of OCZ Platinum
Graphics Card = Integrated ATI Radeon X1250-based graphics
HDD = 500 GB Caviar (60 GB of which is partitioned for Ubuntu)

---

### Post by danwood76 on 2008-05-22
Which graphics drivers are you using?
(did you install them through the restricted drivers manager?)

Could be a graphics issue if random pixels are changing colour.

---

### Post by somody on 2008-05-22
> **danwood76 said:**
> Which graphics drivers are you using?
(did you install them through the restricted drivers manager?)

Could be a graphics issue if random pixels are changing colour.
I've tried standard and restricted drivers: both have the same effect.  I was having the same issue while installing Ubuntu.  I thought it was a graphics issue; however, it once froze in the shell while apt-get was running, and it said something about the CPU being unusable for 11 seconds, but 11 seconds later it said it again.  So it could be the CPU as well.

---

### Post by Kane_of_NOD on 2008-05-22
I had that problem once...
It happened regularly on ubuntu, but not on wind0w$

I changed my motherboard -> problem solved  =)

ohh, and do you have USB modem?  or ethernet connection?

My ex-modem (it was an HuaweE220, USB connection) made my BIOS to stop. I mean, the computer starts, when the BIOS screen is showed. the computer freezes.. LOL.. I just desconected the USB modem and the computer continue the boot. LOL

But I am just a god damn noob.... Good luck!

---

### Post by somody on 2008-05-24
> **Kane_of_NOD said:**
> I had that problem once...
It happened regularly on ubuntu, but not on wind0w$

I changed my motherboard -> problem solved  =)

ohh, and do you have USB modem?  or ethernet connection?

My ex-modem (it was an HuaweE220, USB connection) made my BIOS to stop. I mean, the computer starts, when the BIOS screen is showed. the computer freezes.. LOL.. I just desconected the USB modem and the computer continue the boot. LOL

But I am just a god damn noob.... Good luck!
Well, I'm using a motherboard that I think is quite common: the Asus M2A-VM.  If this is indeed the problem, then Ubuntu coders should really find out what's wrong.  Oh, and I have an ethernet connection (I don't think that's the problem here).

---

### Post by somody on 2008-06-20
I was having the same problem with all non-XP operating systems.  My problem has been solved through experimentation.  The culprit is AMD Live and AMD Virtualization!  Disable both!

---

