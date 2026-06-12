---
title: "Computer making weird noise when running Ubuntu"
date: 2013-01-03
forum: General Help
---

### Post by WuPtI on 2013-01-03
Hello. I have quite a bit of experience with Linux, and have used Ubuntu as one of my favourite distros in quite a while (since 6.10 or around there) but I have a very weird issue with Ubuntu and my desktop. When ever I boot up Ubuntu my computer hardware, not the speakers, start making a very annoying, high pitched noise. The only operating system I have experienced it in is Ubuntu. It isn't around in any version of Windows from XP to 8, and it also isn't there in other distros like Arch Linux. I have no idea why it happens in Ubuntu, or even which piece of hardware is making this noise, so I'm posting to this forum in the hope that some of you may know :) My hardware specs are as follows (the model numbers are from the Windows Device Manager):

Maxtor STM3160215AS HDD
ST9500420AS HDD 
WDC WD1500HLFS-01G6U1 HDD
AMD Radeon HD 6950
AMD Phenom II x4 940
ASUS M3A78-VM Motherboard

I really hope that some of you know what this might be, and even better, how to fix it, so that I can again return to Ubuntu :)

---

### Post by conradin on 2013-01-03
any chance you can post the sound and or make a video of your computer with the case cover off?

moving parts is my guess, fans, HD, CD-rom thrashing. Sometimes inductors poorly wrapped start harmonic oscilations. No idea for ubuntu specific reasons for that. 

If you disable APCI and APIC do you still get this?

Thermal issues I guess could cuase vibrations too. 

I would try to bechmark the PC in Windows to see if any amount of driving the PC could replicate the problem, because it seems like a hardware problem of some sort. 

is the sound consistent? or are there highs and lows, pitch changes, pauses..?

---

### Post by WuPtI on 2013-01-03
Hey conradin thanks for the quick reply!
I'll see if I can make a video recording of it at some point, both when running Windows without the noise and when running Ubuntu. My first guess would also be moving mechannical parts, however I can find absolutely no reason why this should happen only in Ubuntu and not at least in other Linux distros too (as I've said, there is no strange noise in e.g. Arch Linux). What exactly are ACPI and APIC? The abreviations ring a bell, but I can't really place it. I frequently run intenssive games on my computer, and occassionally benchmarks too, under Windows. None of this causes the weird noise. 
It isn't completely consistent, it sort of comes on and off during boot, but by the time the Ubuntu login screen has appeared, the sound is constant.

(Apologies for any spelling errors, English is not my first language)

---

### Post by habana on 2013-01-03
I think you need to establish whether this is a fan making the noise or something else. It should be fairly obvious if you take the covers off

---

### Post by WuPtI on 2013-01-03
Hi habana thanks for the reply. I'm 90 % sure that it is not a fan making this noise, for one it would be odd for something as relatively constant as a fan making different noises based on which operating system the machine is running, and secondly because it doesn't really sound like a fan, the sound is much higher in pitch. I'll try to upload a video of the noise some time tomorrow. If I do this, what would be best, to attach the video to a message on the board, or to upload it to youtube and give a link? I'm asking because I'm very new to this forum, and so does not know what is the norm :D

---

### Post by conradin on 2013-01-04
The logic here is that if you take the cover off, perhaps you can identify the squeeling component. Power management, the token functions of APCI, and Device IO control APIC, disabling those, is to attempt to figure out if either functions effect the presence of this sound. 

in MS Windows, its pretty much impossible to fully disable APIC and ACPI, and still have a functional computer. In linux, we have the ability to control them better. 

If as OP suggests, the squeeling device, isnt a fan, then it may be an inductor, or a failing capacitor, or some other device. 

For troubleshooting, I would remove as many points of confussion as possible. That is to say, I would unplug the HD, the CD-Rom, and superfilous fans, GPU etc... and boot from a live USB running ubuntu. 

I would also suggest booting an alternate version of Ubuntu, like an old stable, like Lucid lynx. What I assume we are all thinking, is that some software is causing hardware malfunctions. But we have no idea where. So we need to isolate that issue first.

The ubuntu kernel isnt like an exact clone of the arch kernel, there are differences, evidently one of those differences makes an obnoxious noise.
lol

Another thought would be to review the Ubuntu dmesg logs, and look for signs of hardware malfunctions, IO errors, etc. perhaps the kernel knows something is wrong?

I am interested in learning the source of this problem.
The english is probably as good as mine, English is my first language. 



> **WuPtI said:**
> Hey conradin thanks for the quick reply!
I'll see if I can make a video recording of it at some point, both when running Windows without the noise and when running Ubuntu. My first guess would also be moving mechannical parts, however I can find absolutely no reason why this should happen only in Ubuntu and not at least in other Linux distros too (as I've said, there is no strange noise in e.g. Arch Linux). What exactly are ACPI and APIC? The abreviations ring a bell, but I can't really place it. I frequently run intenssive games on my computer, and occassionally benchmarks too, under Windows. None of this causes the weird noise. 
It isn't completely consistent, it sort of comes on and off during boot, but by the time the Ubuntu login screen has appeared, the sound is constant.

(Apologies for any spelling errors, English is not my first language)

---

### Post by houseworkshy on 2013-01-04
It's possible that it *is* fans trying to keep things cool because some process is making things hot.  Java and flash gone wrong often cause this sort of thing.  To test it you could try installing "lm-sensors" which is in the default repositories so use any of the usual installation methods.  Once that's done entering "sensors" in a terminal will give you the temperature.  Maybe try it several times at a few minet intervals, and ( if you duel boot ) try similar tests in other operating systems.  
You could also try "top" or , if you install it, "htop" in a terminal to see if any process is using an unusually big amount of processing capacity.

---

### Post by jvano on 2013-01-04
> **conradin said:**
> The logic here is that if you take the cover off, perhaps you can identify the squeeling component. Power management, the token functions of APCI, and Device IO control APIC, disabling those, is to attempt to figure out if either functions effect the presence of this sound. 

in MS Windows, its pretty much impossible to fully disable APIC and ACPI, and still have a functional computer. In linux, we have the ability to control them better. 

If as OP suggests, the squeeling device, isnt a fan, then it may be an inductor, or a failing capacitor, or some other device. 

For troubleshooting, I would remove as many points of confussion as possible. That is to say, I would unplug the HD, the CD-Rom, and superfilous fans, GPU etc... and boot from a live USB running ubuntu. 

I would also suggest booting an alternate version of Ubuntu, like an old stable, like Lucid lynx. What I assume we are all thinking, is that some software is causing hardware malfunctions. But we have no idea where. So we need to isolate that issue first.

The ubuntu kernel isnt like an exact clone of the arch kernel, there are differences, evidently one of those differences makes an obnoxious noise.
lol

Another thought would be to review the Ubuntu dmesg logs, and look for signs of hardware malfunctions, IO errors, etc. perhaps the kernel knows something is wrong?

I am interested in learning the source of this problem.
The english is probably as good as mine, English is my first language.
Some old CRT (catode ray tube) monitor make this kind of noise when the resolution is to high.

Are you using old TRC monitor ??

This kind of sound can also be produced for the power supply, not the fan, the internal HF transformer.

---

### Post by takuie on 2013-01-04
I'm with conradin, pop the top on your box.  Listen and see where the noise is coming from.  Start unplugging things and boot to livecd and plugging back in one at a time until you find where the sound is coming from.  

Unplug everything you can at first, like hdd, optical drives, etc. that would help narrow it down to either a connected device or your mobo.  

I've learned over the years, sometimes the strangest of things can effect the electronics of computer systems in strange ways.

---

### Post by remarks999 on 2013-01-04
I'd also suggest possibly leaving the other drives disconnected if possible (assuming they're spare drives and not part of a RAID). Fans and drives are the main sources of noise in any of my machines. Good luck!

---

### Post by etaeniura on 2013-01-04
I am not a computer expert by any stretch of the imagination, but I had the same problem on an old P3 Dell laptop. It almost sounded like when you run a wet finger over the lip of a glass-high pitched whiny noise? A few weeks later, the hard drive died. It only made the noise when I was in my XP partition, not in the linux one. I would use the test in "disk utility" to see if your HD is dying. Mine told me that hard drive failure was imminent.

---

### Post by houseworkshy on 2013-01-04
If you don't have a wild hot process getting the fans going ( which wouldn't be a cross operating system problem....which is why my first guess would be a software culprit, hardware would affect any OS )  and do have to open it up then a couple of feet of tubing would be a very helpful listening aid when trying to locate the source of the noise in your hardware.

---

### Post by WuPtI on 2013-01-04
Wow, thanks for the massive amount of replies, I didn't think this would get nearly as much attention. Guess I chose the right forum :) I'm studying for some exams at this time, which is why I haven't been able to upload a video or anything similar. I'll try to see if I can't find the time tomorrow to open up the computer and try to find the noise. If I'm unsuccesfull, I'll probably try recording the noise, see if any of you can come up with something based on that :)

---

