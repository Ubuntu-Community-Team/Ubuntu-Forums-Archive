---
title: "Hibernate has killed my PC"
date: 2006-11-07
forum: General Help
---

### Post by yetanothername on 2006-11-07
Today, my wife (who I had to convince that Linux was a good thing) closed Linux. Instead of shutting down she selected hibernate. I came home and started up the PC (unaware of the hibernate selection).

The PC would not start. I get to the screen where you would normally press (in my case) DEl to edit the BIOS. It gets no further. I cannot enter the BIOS editing screen and grub never materialises. (am dual booting with xp)

In short I can no longer start my PC, I get nothing at all.

What kind of magic button is this Hibernate death switch? If I had known this would be the effect of hibernate I would never ever have installed Ubuntu.

How in the world do I get this PC to get out of hibernate?

Any help would be greatly appreciated. (am using Dapper)

---

### Post by .t. on 2006-11-07
This sounds like a coincidence to me. I doubt hibernate has killed your PC, nor Ubuntu itself. Sounds like failing hardware to me...

---

### Post by yetanothername on 2006-11-07
Thanks for the reply,  

"I doubt hibernate has killed your PC, nor Ubuntu itself." - No offense, but you provide no reason for this statement except your self-doubt that this could be the result of Ubuntu.

I appreciate your input, but it is not very helpful.
The fact is that hibernate was selected, the desktop shut down and will not boot anymore. I am trying to find out more about hibernate, what the expected behaviour is under a desktop environment, and possibly how I can force the PC out of hibernate if the system is unable to do it automatically.

---

### Post by .t. on 2006-11-08
Right, well all Hibernate does is save the working state of the computer to the disk and syncs the hard drives and powers off the PC. It includes various things like the memory, so that when the system is brought up again, it can all be read back and the session loaded as if nothing had happened.

When you first turn on your PC, the Video BIOS is activated and then the main BIOS does a "Power-On Self Check". It sounds like it hangs during either of these two processes, which I don't think Ubuntu touches.

---

### Post by pitkali on 2006-11-08
> **yetanothername said:**
> I am trying to find out more about hibernate, what the expected behaviour is under a desktop environment, and possibly how I can force the PC out of hibernate if the system is unable to do it automatically.
I dual boot with xp and use hibernate regularly. I am a developer and an experienced linux user from 1999.

Now, the expected behaviour of the hibernate is like that:
* The memory state has been saved to the swap partition and computer powered off, as already mentioned in the thread.
* The computer is simply powered off and not in any fancy "hibernate" state, which means that after switching on it should normally boot until grub. There you can choose the system. You can choose windows and use it the usual way. Or you can choose linux. In the latter case the kernel after loading itself will read the memory contents from swap partition and activate the system.

The hibernate process does not mangle the BIOS, etc.

I second the opinion about coincidence.

Regards,

---

### Post by FrankVdb on 2006-11-08
Don't use hibernate. I have three computers (2 desktops on Dapper and one Edgy laptop), and none of them hibernate properly. It's a real nuisance on my laptop, which I often need to switch off temporarily. Suspending doesn't work either, Ubuntu just shuts down.

---

### Post by pitkali on 2006-11-08
[QUOTE=FrankVdb;1730341Suspending doesn't work either, Ubuntu just shuts down.[/QUOTE]
Strange as it should try to suspend. It is, however, undeniable that suspend and hibernate are one of the least supported laptop features. The task of suspending is in itself dependent much on the hardware and it appears it doesn't work on many laptops. (Though personally I had no problems with getting it to work on my laptops.)

---

### Post by yetanothername on 2006-11-08
Thank you guys for answering, you have filled in the missing details that I was unsure about concerning hibernate.

I needed to be able to write off hibernate as a possible issue before I moved to re-flashing the BIOS and failing that, starting to remove bits of my hardware to see what the problem might be. (the PC is almost new but the problem is I have absolutely no faith/trust in the people who put it together - a popular Cal based gaming PC company)

I now have a boot disk incl. some BIOS tools and will try that our tonight. Failing that I will start removing my video cards (SLI), mem etc. and go from there.

Again, thanks for your input.

cheers
Ray

---

### Post by yetanothername on 2006-11-08
Well guys if you are interested in the result:
In my opinion hibernate DID kill my PC. 

I did the following:
To make it easier on myself I started by simply removing my memory sticks (4 500M sticks). I replaced them one at a time and found that the comp started and Linux booted fine. I ended up with all my memory back in their slots and Linux booting fine.

So it was not bad memory, but taking out the memory and reinserting it reinitialised my BIOS (because I had to go back in and edit the BIOS to the original settings - Legacy USB off)

So then as a test I booted Linux several times - everytime Linux worked perfectly. I then set Ubuntu to hibernate instead of shutdown. The system would not start at all - exactly the same as before, with the system stalling before I can even get the BIOS edit screen.

I then removed a memory stick - (reset the BIOS again) and booted linux again. This worked fine - I replaced the missing mem (and reset the Bios again) and can now boot Linux again.

So my conclusion is that (at least for my rig) hibernate is a kill switch.

What do you think - should I report this a a bug? or just ignore it as there is no way we will ever use hibernate again anyway.

---

### Post by pitkali on 2006-11-09
Sounds like a serious hardware compatibility issue. If this is a laptop you should definitely report a bug. Though it remains a question if this is a linux bug, or perhaps a bios bug (in acpi support?).

BTW: since you made computer work again - don't you think kill is too strong a word? ;)

---

### Post by yetanothername on 2006-11-09
"BTW: since you made computer work again - don't you think kill is too strong a word?"

haha - yes a bit strong, maybe "deep semi-permanent hibernate" would be more appropriate (if semi-permanent is even a word)

For ACPI - if I turn it off, Ubuntu is unable to start, so I am not able to toggle that to see if it would make any difference.

It is a desktop rig and I agree that it could easily be my setup (BIOS or otherwise) that is causing this. At least if this occurs to other people they should be able to find this thread in a search to possibly help them. (for the record the motherboard is an Asus P5N32 SLI Deluxe)

The best part is that now the guys at work will stop joking that I will have to wait until spring to get it out of hibernate. :rolleyes:

---

### Post by feest on 2006-11-09
well i doubt if it's even possible for software to affect hardware but a fact is that your pc doesn't boot. maybe you can provide us with a picture of your screen (screenshot will not work without os :P) so we can detect some errors. you can also try to "reset" you bios, if you changed settings in the bios since you bought your motherboard or pc this is not a recomendation, otherwise it just should work. if you open the case (and turn off the power otherwise this could hurt your pc) you'll find a round flat battery on the motherboard (the probably the largest chip in your pc) if you pop it out wait a minute and pop it in again everything is resetted on your motherboard and bios so if some kinda setting was corrupted it will now be back to the factory setting. try booting again, gets it any futher?

---

### Post by darrenm on 2006-11-09
Yes I agree, moving your RAM around is the same as clearing the CMOS as it modifies the ESCD.

I would guess your BIOS isn't correctly flushing the memory when entering into S4 mode (hibernate)

Could be indicative of a faulty board or buggy BIOS.

ACPI is an open standard. Ubuntu / Linux developers have only got the standard to go on.  [http://www.acpi.info/](http://www.acpi.info/)

---

