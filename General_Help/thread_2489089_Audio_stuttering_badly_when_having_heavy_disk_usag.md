---
title: "Audio stuttering badly when having heavy disk usage"
date: 2023-07-18
forum: General Help
---

### Post by cristian10abcd on 2023-07-18
I have a poor, very poor, potato laptop. An Hewlett Packard potato. Yeah. And I daily experience the most amazing things in the universe on it. Definetly. 

Especially when I open a game that consumes alooot of mb from my 4gb DDR3L memory :D Minecraft. Yeah. I open the game, it loads (while freezing of course), then if I want to open a google chrome tab or something like that... that plays audio things, or even the in-game audio, it starts stutttering. Badly stuttering. Also, if I pause one of the sound outputs (e.g I pause the youtube video or... yeah you understand), it will sound like a helicopter in the sky. This is what I hear after pausing the video or the audio source and lasts for like 2-3-4 seconds.
I concluded that this is happening because of either high ram usage caused by the apps, either by the high disk usage(HDD which is also, you guessed it, slow:D).
Oh and also the video stutters :D a little bit but still does stutter.

Anybody encounters similar things by any chance? I would be very happy to hear a solution.

---

### Post by DuckHook on 2023-07-19
Welcome to the forums, cristian10abcd

I have no idea what a "potato" laptop is, but my guess is that you mean an old, weak, slow, resource&#8209;limited machine.

Going by your 4 GB of RAM, I might guess that your video subsystem is even more constrained. It might even steal RAM from your main memory to run as video memory. If so, it is no wonder that you are getting both video and audio stuttering, dropouts and freezes. Your machine just doesn't have the power to run a modern operating system. Without knowing your actual HW specs, we can only speculate.

As for solutions, you can try moving to a lightweight flavour or even a different lightweight distro. However, be warned ahead of time that this won't likely help. You are running resource&#8209;heavy apps like Minecraft and Chrome on a machine that just cannot handle it.

The real solution is to buy a more powerful computer.

---

### Post by cristian10abcd on 2023-07-19
Hardware specs:
Intel Pentium n3710 (1.6ghz base clock; 2.56 ghz boost clock, four core CPU);
4 gb DDR3L RAM (1600 mhz);
WEstern Digital something something alot of letters HDD- 512 GB @ 7200 rpm I think;
Intel HD 405 GPU (700mhz boost clock.. 320 mhz base clock);
Missed anything? Idk.

Laptop model: HP 15RA052NQ;

---

### Post by gezzer2 on 2023-07-19
> **cristian10abcd said:**
> Hardware specs:
Intel Pentium n3710 (1.6ghz base clock; 2.56 ghz boost clock, four core CPU);
4 gb DDR3L RAM (1600 mhz);
WEstern Digital something something alot of letters HDD- 512 GB @ 7200 rpm I think;
Intel HD 405 GPU (700mhz boost clock.. 320 mhz base clock);
Missed anything? Idk.

Laptop model: HP 15RA052NQ;
are you willing to do some minor upgrades as that processor supports up to 8GB of DDR3 1600 and a possible upgrade to the HDD to a SSD. 
this may help with some of the problems but the biggest hold back you have is the GPU.
specs for the GPU here ...
[https://www.techpowerup.com/gpu-specs/hd-graphics-405-mobile.c2901](https://www.techpowerup.com/gpu-specs/hd-graphics-405-mobile.c2901)

---

### Post by cristian10abcd on 2023-07-19
I would like to but currently I am not able to. So I am stuck with this :D

---

### Post by gezzer2 on 2023-07-19
> **cristian10abcd said:**
> I would like to but currently I am not able to. So I am stuck with this :D

have a look on line for bargain basement pre loved computers you may find another stick of 4GB of ram for very little. just have a look around you will be surprised at what you can pick up for next too nothing ...

for example ive just picked up a near new 22" AiO ASUS , cpu celeron n4025 (very weak) 4gb of ddr installed for £150 they retail for over 400.
but it has a hidden nvme m2 slot on the backside of the mobo which i will fit a 256 m2 ssd (£15). i already have 16GB of DDR4 3200 for it from my wife's system.
so for next to nothing it will be a half decent system which is a gift to someone just starting college ...

---

### Post by DuckHook on 2023-07-19
> **cristian10abcd said:**
> I would like to but currently I am not able to. So I am stuck with this :D
If you are absolutely stuck from making any upgrades, then you may need to revise your expectations. Linux is not a magic wand. It cannot turn a weakling computer into an Olympic weightlifter.

You will not be able to run Minecraft. That is a resource&#8209;hungry app that requires a better CPU, RAM and GPU than yours.

Chrome is also a resource pig. You would be better off with a lighter browser. Epiphany might work. Midori is also light but still reasonably functional. There are even lighter weight browsers that work with minimalist systems, but I doubt that you would like them. Note, however, that streaming audio/video will tax your system no matter what browser you use.

---

