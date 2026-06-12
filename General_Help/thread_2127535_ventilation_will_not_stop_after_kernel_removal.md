---
title: "ventilation will not stop after kernel removal"
date: 2013-03-20
forum: General Help
---

### Post by thedardanius on 2013-03-20
as the title says, my ventialtion persists to turn 100% power fan, while my processor may even be virtually completely idle!!!
There is something really wrong. From the day I removed some never 3.5.0-generic kernels (they were buggy as hell) with dpkg purge function I experienced this. My father said that apparently something has changed the BIOS rom and the I should flash it.
Is this true? Could this be the reason, and if so, isnt there another way>
Im using asus with interl pentium dual core, BIOS american megatrend.

---

### Post by grahammechanical on 2013-03-20
> [COLOR=#000000]My father said that apparently something has changed the BIOS rom and the I should flash it.[/COLOR]

Please resist doing this. I doubt very much that anything in Ubuntu can change the settings in the BIOS. Removing old kernels will not alter settings in the BIOS. That is not to say that you should not check the BIOS settings and the temperature measurements.

Have you given any thought to the fact that the inside of the machine may be clogged up with fluff and dust? Could any of the fans be broken? From the Ubuntu Software Centre you can install Psensor. It will put an indicator in the top panel which will have a drop down menu which will give information about fans speeds and temperatures. It will measure the temperature of the CPU, Motherboard, GPU, temperatures of each CPU cores, even the hard disk temperature. Find out what it is that is overheating. Are the ventilation inputs and outputs blocked?

Regards.

---

### Post by schragge on 2013-03-20
This also can be matter of older kernels not having / having a buggy hardware monitoring driver for your motherboard.

---

### Post by thedardanius on 2013-03-21
ok, i checked the temps:
hard disk about 50 C
cpu about 40-45 C
Normal?!??

Then, I dint remove older kernels, I removed newer kernels, namely linux-generic 25 en 27. These were buggy as hell.
Please tell me, what is linux-generic? Is this fake linux (kernel made by other team with linux source) or is this the real linux?
Should I have 3.5.0 (my fahter said these generic kernels were experimental and discourages me to use them) or should I get the 3.2.0 (he said these were the "standard" kernels currently in use).

---

### Post by Impavidus on 2013-03-21
For the hard disk that's quite high, for the CPU that sounds more or less OK. It depends on the design of your box, the amount of activity and to some extend ambient temperature. Right now my CPU is 30&#8304;C and my HDD is 25&#8304;C and my laptop is known for running hot easely.

If I'm correct, linux-generic means the linux kernel compiled for generic systems, so it's the real linux kernel. Ubuntu 12.10 needs kernel 3.5, Ubuntu 12.04 can use either 3.2 (Ubuntu 12.04.1) or 3.5 (Ubuntu 12.04.2). It's generally a bad idea to use a different kernel than the one for which your Ubuntu version was designed, as some software can break down. I think you haven't told us yet which Ubuntu version you use.

---

### Post by thedardanius on 2013-03-21
im using 12.10, so 3.5 is good. Ok :D
However, I suspect this has to do with the fact that I refreshed GNU GRUB, maybe that set some settings in the BIOS??

---

### Post by thedardanius on 2013-03-22
Please guys help me!
THe ventilation sound is so hard... ARG!

---

