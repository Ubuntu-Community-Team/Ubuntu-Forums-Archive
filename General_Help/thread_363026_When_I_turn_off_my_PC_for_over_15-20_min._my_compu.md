---
title: "When I turn off my PC for over 15-20 min. my computer freezes at the BIOS screen.help"
date: 2007-02-16
forum: General Help
---

### Post by billdotson on 2007-02-16
If I turn my computer off for more than 15-20 minutes or so my computer will freeze at my Asus BIOS screen and I just have to turn it off and reboot. Why is it doing this? 

I posted this topic in the official Windows forum and the guy said that he thought that sounded like a failing PSU.  I replied by saying

I have a Antec TruePower 2.0 550Watt PSU, so I don't think the size is the problem. I have an Asus P5B Deluxe/Wi-f AP edition, an nVidia 7800GT, Core 2 Duo E6600, 2 gigs XMS2 DDR2800MHz RAM, Hauppauge HVR-1600 TV Tuner, 2 DVD drives and a Sundblaster Audigy 4. I switched some of the fans in my case so my PC runs cooler than it used to.. and because the Antec TruePower 2.0 has a thermal management fan the power supply fan runs at only 800RPM.

How do I know for sure I am having a dying power supply? If it dies on me I will be angry because I just spend $2000 to build a new one after my other PC's PSU failed and fried my motherboard. :mad:

---

### Post by hardyn on 2007-02-16
well you have ALOT of hardware in that case... and just becuase you have a name brand powe supply doesn't mean its not broken ;) 

unplug EVERYTHING that isn't a motherboard and a video card, this includes the second strip of ram.

try again.

if you still have a crash swap rams.

are you sure that the motherboard manuf. has approved your ram and processor?

does the motherboard have integrated video? if so try without the monster nvidia board

still no?

inspect the motherboard board for blown capacitors.

start swapping parts with your friends or other machines.

its a basic troubleshooting list, but really... 550 watts doesn't sound like alot of power for all that hardware.  i bet that video card is consuming 150-200 right away.

good luck.

---

### Post by tribble222 on 2007-02-16
Problems like this are hard to diagnose.  The best way to figure it out is to swap out your components, one at a time, with known working ones.  Unfortunately this requires you to have spare components.  If you don't have anything to swap in you could just try unplugging non-essential components (like hard drive, pci cards).

---

### Post by billdotson on 2007-02-16
Yes the CPU and the RAM are approved with the motherboard.  The motherboard is one of the Core 2 Duo boards and I checked the compatibility of the RAM before getting it.  The RAM sticks are the same [both are Corsair XMS2 DDR2 RAM]

I have no onboard video.  I don't see any blown capacitors.

I don't have any spare parts and the only PCI card that requires power directly is my nVidia 7800GT (256mb PCIeX16)

Should I just get a 700-750 watt PSU so I will have a big enough one to upgrade to a DirectX10 videocard later?  (I want to get a DirectX10 card later when I get Vista to play some DX10 games)

I have been running my PC for about 4-5 months.

---

### Post by hardyn on 2007-02-16
see if a dealer will let you "try one out" before buying.

try running on one strip of ram.

ram unfortunately is sort of a common failure.

---

### Post by billdotson on 2007-02-16
I unplugged everything that had power to it except for the case fans and the videocard (I have no onboard video) so both DVD drives, the hard drive, and the 7in1 media bay were unplugged.

I let it sit for 15-25 minutes and then booted it back up. I didn't see the BIOS screen it just straight to loading Ubuntu from my external hard drive. Sometimes the monitor won't receive a signal for awhile (monitor light is orange) and then it will show up a few seconds later. Sometimes though the boot screen comes up as soon as the PC is turned on.

I then noticed that my surge protector is blinking so I switched the power socket and the surge protector I was using and left the PC off for about 20-30 minutes and then started it up and it loaded normally. Maybe it was that surge protector?? (it is pretty old like 10 years or so)

Should I just get one of these PSUs or is something else going on?

---

### Post by hardyn on 2007-02-16
remove the surge protector and start adding components in a "logical order" until it fails again.

it will either work or you will find what isn't working.

but if you really want to buy a new psu i won't stop you.

---

### Post by billdotson on 2007-02-16
what do you mean remove it and plug them in in logical order until it fails?

Should I just leave the computer off for a prolonged period of time like about 8 hours or so with the new surge protector and new power socket and try to turn it on and see if it freezes?

---

### Post by hardyn on 2007-02-16
no i mean add parts back in terms of usefulness and try to find a fault.

start with mobo, vid card an one strip of ram -- and it works, yay
add second ram -- does it work?
add one cd -- does it work
add second cd -- does it work
add card reader -- does it work 
etc. 

see if you can make it fail.

if you get all the parts back in, you know its was a weak surge protector.

if it fails somewhere along the way, it mean either you don't have enough juice, or you have a fault in the part or an incompatibility.

if you really wanted to get nerdy about it... all the devices will have a current draw rating either on them or in the documentation... you could add all these current ratings up and see if you are anywhere near 550 watts?

one thing you may want to check, and i should have mentioned earlier, is your CPU cooling / GPU cooling adequate?  are the fans still spinning? has the heat sink heat pipe fallen off, or become loose?  pulling all the parts and having it work would suggest no, but its worth a check.

---

### Post by hardyn on 2007-02-16
> **hardyn said:**
> no i mean add parts back in terms of usefulness and try to find a fault.

start with mobo, vid card an one strip of ram -- and it works, yay
add second ram -- does it work?
add one cd -- does it work
add second cd -- does it work
add card reader -- does it work 
etc. 

see if you can make it fail.

if you get all the parts back in, you know its was a weak surge protector.

if it fails somewhere along the way, it mean either you don't have enough juice, or you have a fault in the part or an incompatibility.

if you really wanted to get nerdy about it... all the devices will have a current draw rating either on them or in the documentation... you could add all these current ratings up and see if you are anywhere near 550 watts?

one thing you may want to check, and i should have mentioned earlier, is your CPU cooling / GPU cooling adequate?  are the fans still spinning? has the heat sink heat pipe fallen off, or become loose?  pulling all the parts and having it work would suggest no, but its worth a check.

the 20/25 minutes sounds alot like a capacitor effects. which may suggest a weak power supply OR massive inrush current that is making your surge protector freak out.
are you running anything else on your computers circuit? halogen desk lap? toaster? massive set of 7.1 speakers? 

you are getting to a level of current draw with that system, that you are actually starting to tax the circuit a little.

---

### Post by billdotson on 2007-02-16
no I have a set of cheap 5.1 speakers that doesn't even have a power block just a normal plug.  I changed to another surge protector and put it in a different socket and it worked fine after about 30 minutes.

---

