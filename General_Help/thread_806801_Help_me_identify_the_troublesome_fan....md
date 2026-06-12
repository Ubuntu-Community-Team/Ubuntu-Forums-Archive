---
title: "Help me identify the troublesome fan..."
date: 2008-05-25
forum: General Help
---

### Post by asintu on 2008-05-25
Here's the problem:
I have XP and Ubuntu on my computer.
When I boot up system sounds the same. Midway through the XP loading screen one of the higher pitched fans goes to a lower and much more acceptable noise level. Loading Ubuntu doesn't change a thing in noise level.
I have already identified that the cpu fan is not the problem after disconnecting it and testing noise level again.
That leaves me with 4 choices:

1. Big case fan (but it's 3 speed manually configured so I doubt its that)
2. Power supply fan (don't see how software would have an impact on that)
3. Video card fan (maybe better drivers for card in windows than ubuntu?)
4. HDD (but it's not a fan!)

What's your opinion on this?

---

### Post by Sarah L on 2008-05-25
You've pretty much narrowed it down to the video card fan. Ubuntu tries to make use of free, open-source drivers whenever possible, but unfortunately many of them are generic and don't let you get the most out of your hardware. You should check to see if your video card manufacturer has produced a driver for Linux - one that is more likely to be fully compatable with your hardware. Sadly, many manufacturers don't seem to be very interested in providing Linux support.

Good luck on your quest for noise-reduction! :)
-Sarah

---

### Post by danwood76 on 2008-05-25
What motherboard do you have?

You might have a North Bridge fan aswell depending on your motherboard.
Generally Graphics cards manage their fan internally, I would be looking at the CPU or NB fans as the culprits.

---

### Post by danwood76 on 2008-05-25
Also to test which fan it is just stop the fans with your fingers, it wont damage the fan and it will tell you instantly whcih fan it is. (Of course dont just dive your fingers in or it might hurt)

---

### Post by asintu on 2008-05-25
> **danwood76 said:**
> What motherboard do you have?

You might have a North Bridge fan aswell depending on your motherboard.
Generally Graphics cards manage their fan internally, I would be looking at the CPU or NB fans as the culprits.

no NB fan here.

---

### Post by asintu on 2008-05-25
> **Sarah L said:**
> You've pretty much narrowed it down to the video card fan. Ubuntu tries to make use of free, open-source drivers whenever possible, but unfortunately many of them are generic and don't let you get the most out of your hardware. You should check to see if your video card manufacturer has produced a driver for Linux - one that is more likely to be fully compatable with your hardware. Sadly, many manufacturers don't seem to be very interested in providing Linux support.

Good luck on your quest for noise-reduction! :)
-Sarah

yup, it is the video card. Is there any way to install the windows drivers into ubuntu? or a way to take control of the fan? btw the fan is attached to the video card, not the motherboard. Or should i start looking for a fanless card right away? :)

---

### Post by danwood76 on 2008-05-25
What video card is it?

---

### Post by Macintosh SE on 2008-05-25
Depending on what type of power connector it uses, you may be able to control its speed (or turn it completely off, if necessary) with a fan controller for your 3.5 inch bay.

---

### Post by asintu on 2008-05-25
> **danwood76 said:**
> What video card is it?

it's this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121094](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121094)

---

### Post by danwood76 on 2008-05-25
Are you running the restricted graphics drivers for your nvidia card? (installed through Hardware Drivers contgrol panel)

Ive done a bit of digging and a lot of people are saying that it does control fan speed.

-- edit --

It looks like NvClock can adjust fan speeds:
[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

---

### Post by asintu on 2008-05-25
> **danwood76 said:**
> Are you running the restricted graphics drivers for your nvidia card? (installed through Hardware Drivers contgrol panel)

Ive done a bit of digging and a lot of people are saying that it does control fan speed.

-- edit --

It looks like NvClock can adjust fan speeds:
[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

yes, it's the restricted one. so how can i control fan speed then?

---

### Post by asintu on 2008-05-25
what's the steps of installing nvclock?

---

### Post by asintu on 2008-05-25
> **asintu said:**
> what's the steps of installing nvclock?

nevermind.
i've installed nvclock but when i try to change fanspeed it says:
"adjustment of the fanspeed isn't supported on your type of video card".
What to do now? Is there really no way of changing the speed of the fan in ubuntu? There's clearly a way since the nvidia windows driver adjusts the speed properly. Can I somehow "translate" the windows driver into ubuntu?

So...where do I go from here? To the store to get a fanless card?

---

### Post by danwood76 on 2008-05-26
I have no experiance with nvidia cards, most graphics card control fan speed through their BIOS, yours shouldnt be different.
Maybe its just hot? Is the heatsink on the card warm to touch?

On my ATI card I installed a Zalman flower which comes with a speed controller, but its silent even at full speed so I chucked the speed controller in a box. but is way better at cooling than my stock cooler.

---

### Post by asintu on 2008-05-26
> **danwood76 said:**
> I have no experiance with nvidia cards, most graphics card control fan speed through their BIOS, yours shouldnt be different.
Maybe its just hot? Is the heatsink on the card warm to touch?

On my ATI card I installed a Zalman flower which comes with a speed controller, but its silent even at full speed so I chucked the speed controller in a box. but is way better at cooling than my stock cooler.

i'll try to return it. if not ill get a different cooler

---

### Post by geoff123 on 2008-05-26
Try installing nvclock from synaptic.
From a terminal try this command:
nvclock -f -F 95

On my system this sets the fan to 95% which is much quieter. Actually anything less than 98% on my system is much quieter.

---

### Post by asintu on 2008-05-26
> **geoff123 said:**
> Try installing nvclock from synaptic.
From a terminal try this command:
nvclock -f -F 95

On my system this sets the fan to 95% which is much quieter. Actually anything less than 98% on my system is much quieter.

its fine i got a silent one

---

