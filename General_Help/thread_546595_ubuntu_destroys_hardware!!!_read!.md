---
title: "ubuntu destroys hardware!!! read!"
date: 2007-09-09
forum: General Help
---

### Post by bam1234567 on 2007-09-09
After about 4 wireless cards breaking in my ubuntu computer i have finally figured out the culprit. It is the sleep function. I have a PCI to PCMCIA adapter that i use for my wireless card, but every time i bought a new one, it broke. Thinking "Oh it's only a dud" I went and returned them, but now i finally know that it is ubuntu's sleep function that is doing it. You see i have found out that when it sleep's it delivers a little spike to all the hardware that its connected to. (That's why you hear your hard drive go TINK! when it sleep or sometimes shuts down) Now, this is not a big spike, but to devices like, oh, say 5 volt PCMCIA, it will destroy them. So, remember, UNPLUG you PCMCIA cards before you shut off, hibernate, or even sleep! but tell me if this dosent happen to you because i have tried it on 2 different comps and both outcomes were the same.
And if you think the OS can't do anything to your hardware, read this:
[http://ubuntuforums.org/showthread.php?t=508576]("http://ubuntuforums.org/showthread.php?t=508576")

---

### Post by dcstar on 2007-09-09
> **bam1234567 said:**
> After about 4 wireless cards breaking in my ubuntu computer i have finally figured out the culprit. It is the sleep function. I have a PCI to PCMCIA adapter that i use for my wireless card, but every time i bought a new one, it broke. Thinking "Oh it's only a dud" I went and returned them, but now i finally know that it is ubuntu's sleep function that is doing it. You see i have found out that when it sleep's it delivers a little spike to all the hardware that its connected to. (That's why you hear your hard drive go TINK! when it sleep or sometimes shuts down) Now, this is not a big spike, but to devices like, oh, say 5 volt PCMCIA, it will destroy them. So, remember, UNPLUG you PCMCIA cards before you shut off, hibernate, or even sleep! but tell me if this dosent happen to you because i have tried it on 2 different comps and both outcomes were the same.

I recall recently reading about a kernel issue where a particular command wasn't being sent to hard drives when going into sleep/shutdown mode, so this may be related as people reported various hard drive noise issues.

I seem to remember that the fix was in one of the newer kernel versions (that haven't yet been distributed in Ubuntu).

---

### Post by Martje_001 on 2007-09-09
Isn't this is a hardware (motherboard) problem?

---

### Post by bigbrovar on 2007-09-09
Damn! is there anything one can do to prevent this? i mean the PCMCIA, is small compared to what could  happen to my hard drive ohhhh:confused:

---

### Post by afonic on 2007-09-09
I use Ubuntu with a PCMCIA card for 2 years now on my laptop and never had a problem.

Maybe something with a specific driver?

---

### Post by bigbrovar on 2007-09-09
> afonic  	
Re: ubuntu destroys hardware!!! read!
I use Ubuntu with a PCMCIA card for 2 years now on my laptop and never had a problem.

Maybe something with a specific driver? 

well i quite agree cus i use a PCMCIA card and i dont take it out of my lappy..when am thru with my lappy i just shut down.and i have never had any probs with it going hacko...

---

### Post by gary0 on 2007-09-09
Well that's answered a small annoyance for me... My hard drives sometimes go 'clink' when I shut down (it's a desktop), and they are both brand new < 1 month old. There was me thinking I bought a dud!

Gary.

---

### Post by AlexenderReez on 2007-09-09
i use nvidia PCI card....until now...i got error while booting kernel about PCi....i don't sure what it is as it display error very fast.....but it doesn't seems to any problem to my system....should i worry about it?

---

### Post by doublearon on 2007-09-09
Listen, I have Ubuntu on my laptops and I have no problem at all. I also have no problem with hardware on my desktop. Maybe you shouldn't buy junk...

---

### Post by por100pre1 on 2007-09-09
Solution: [upgrade the kernel]("http://ubuntuforums.org/showthread.php?t=511974").

---

### Post by kerry_s on 2007-09-09
no problems here. the only way i could get on the net is with a pcmcia card and i'm still using the same one.

---

### Post by Steve1961 on 2007-09-09
I have two laptops with pcmcia cards and I've never experienced this problem.  maybe its hardware specific - one of my cards is an asus and the other is a belkin.

---

### Post by prodigal on 2007-09-09
I use a Zyxel PCMCIA card in my Kubuntu laptop and it has never done any such thing. I find it hard to believe that linux is capable of accidentally destroying hardware by a power spike. For one thing the power comes directly from the power supply and the flow to each periferal isn't controlled by the motherboard or the software installed on the hard drive. It's independent and not intelligent. I would suggest your power supply is the culprit instead and that it is most likely not earthed properly or that your entire laptop isn't earthed properly causing spikes when fluctuations in power occur through the motherboard dropping it's power levels and the power supply then starts to put that un-needed flow into another component.

---

### Post by bam1234567 on 2007-09-09
> **doublearon said:**
> Listen, I have Ubuntu on my laptops and I have no problem at all. I also have no problem with hardware on my desktop. Maybe you shouldn't buy junk...

Umm lets not be stupid here i buy nice equpment. You can even see in my sig that it not junk.

---

### Post by bam1234567 on 2007-09-09
and if you think the OS can't do anything, read this:
[http://ubuntuforums.org/showthread.php?t=508576]("http://ubuntuforums.org/showthread.php?t=508576")

---

### Post by bam1234567 on 2007-09-09
> **prodigal said:**
> I use a Zyxel PCMCIA card in my Kubuntu laptop and it has never done any such thing. I find it hard to believe that linux is capable of accidentally destroying hardware by a power spike. For one thing the power comes directly from the power supply and the flow to each periferal isn't controlled by the motherboard or the software installed on the hard drive. It's independent and not intelligent. I would suggest your power supply is the culprit instead and that it is most likely not earthed properly or that your entire laptop isn't earthed properly causing spikes when fluctuations in power occur through the motherboard dropping it's power levels and the power supply then starts to put that un-needed flow into another component.

Oh by the way it's a desktop that fried them. I have done more research and it appears to be the OS is somehow telling the capacitors in on the mother board or the power supply to drain, which releases the spike. so i am definitely going to upgrade my kernel.
but read this and youll find the OS can do corruptive things to your hardware
[http://ubuntuforums.org/showthread.php?t=508576]("http://ubuntuforums.org/showthread.php?t=508576")

---

### Post by bam1234567 on 2007-09-09
and when you really think about it. This can't be that much of a suprise since hibernate and suspend on some computer aren't even close to working, so i can't say this is a shocker.

---

