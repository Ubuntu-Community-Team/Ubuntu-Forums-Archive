---
title: "Prohibited sign meaning?"
date: 2021-08-30
forum: General Help
---

### Post by barry-normal on 2021-08-30
Hello folks, 

I have build my first ever PC, and installed on it Ubuntu 21.04. First ever linux install....

All has gone swimmingly, till this prohibited sign keeps popping up on the desktop. And I can't find any indication what exactly it means. 

Everything 'seems' to be working OK. The sign doesn't stop me doing anything. But, obviously, it's annoying. And worrying.

Whatever it means is probably not good. One thread seemed to suggest it was hardware-related but, I'm not sure how to tell if this is so.

So, does anyone know exactly what the attached image means? 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289081&stc=1[/IMG]

Thanks, and apologies if this is an idiot question.

B

---

### Post by Autodave on 2021-08-30
Certainly is not an idiot question!  Please give us info on your system.

---

### Post by barry-normal on 2021-08-30
Hey Dave, thanks for getting back to me. Let me know if there's anything else you need to know:

AMD Threadripper 32 core
NVIDIA RTX 3090
ASRock Taichi MB
128 GB RAM, Corsair DDR4 3600MHz
Wraith Ripper cooler (Prime suspect)
NZXT Case
Samsung 2TB M2 
Samsung 4TB ssd

---

### Post by QIII on 2021-08-30
Hello!

What keyboard are you using?  Have you recently tried to use the media keys?

---

### Post by barry-normal on 2021-08-30
Hello!
I'm using a Durgod keyboard. Microsoft Optical mouse.

Though I get the same warning pop up with both of these unplugged.

I had to google media keys. Could I have engaged them by accident?

B

---

### Post by HermanAB on 2021-08-30
It could have something to do with your display - some feature such as backlighting on/off is misinterpreted by the system.

---

### Post by barry-normal on 2021-08-30
Hey GernmanAB, it could be. Sadly though I have no other display to connect. 
It's a [SAMSUNG ODYSSEY G5 32]("https://www.amazon.fr/gp/r.html?C=1HW4LFIAG5R5R&K=3680L51M3IRH7&M=urn:rtn:msg:2021072714362259fa02e4f5ab404ba96b9d44d510p0eu&R=BFP9U2ZLZJDL&T=C&U=https%3A%2F%2Fwww.amazon.fr%2Fdp%2FB08C7T1TGL%2Fref%3Dpe_27091421_487030221_TE_3p_dp_1&H=WRV6TUAUCTN4J0PUT3VSBHLOEKQA&ref_=pe_27091421_487030221_TE_3p_dp_1")

I did suspect the display of being the sole problem, given that it's such a nicely formed (but intensely annoying) warning. But if I connect my MacBook, no warning. 

The niceness of the warning symbol makes it odd that it isn't documented anywhere, to me at least. 

Anyway, I've booted into a USB running 20.04, rather than 21.04 and so far, no warning symbol.

This is good, but not conclusive as the first warning didn't appear for maybe 2 days.

---

### Post by GhX6GZMB on 2021-08-30
That symbol is not from Ubuntu, but the screen itself.
Perhaps an unrecognized resolution, frame rate or something like that.

---

### Post by HermanAB on 2021-08-31
I’ve had that kind of thing happen on a Lenovo laptop running Windows.  The symbol just looked different and was easier to relate to the screen.

---

### Post by barry-normal on 2021-08-31
Thanks folks, I'll dig deeper, see if I can get a response from Samsung as it's not in the manual...

---

### Post by Autodave on 2021-08-31
You may also want to try another HDMI cable just to make sure that yours isn't bad.....

---

### Post by barry-normal on 2021-09-03
That's an excellent idea, thanks AutoDave. I've spoken with Samsung and they assured me it's not the display...

So, it has to be Ubuntu, right? 

B

---

### Post by Autodave on 2021-09-03
I believe that to be a warning coming from the PC itself: not from Ubuntu.  Like said before, more than likely a mis-match of resolution and/or frequency.  I would definitely try another cable first and then I would look to see what the supported resolutions are for the monitor along with the monitor's frequency.  Then compare that to what Ubuntu is telling you that it is using for resolution and frequency.  But try a cable first.

---

### Post by HermanAB on 2021-09-04
Btw, try booting from the install media and go to the desktop, but don’t do anything - just let it sit and see whether the sign pops up again.  That may tell you something.

---

### Post by ActionParsnip on 2021-09-04
When it pops up, press CTRL + ALT + T to run a terminal and run:
```

dmesg | tail

```
What is the output please?

---

### Post by steve234 on 2021-09-04
> **barry-normal said:**
> 

AMD Threadripper 32 core
NVIDIA RTX 3090
ASRock Taichi MB
128 GB RAM, Corsair DDR4 3600MHz
Wraith Ripper cooler (Prime suspect)
NZXT Case
Samsung 2TB M2 
Samsung 4TB ssd

Just popped in to say, perhaps I'm speaking for myself, but that's not the kind of spec I'm used to seeing around here (or at all). Nice build.

If you want a laugh I'll tell you what my latest linux box is

---

### Post by barry-normal on 2021-09-05
Firstly, thanks everyone for applying your collective wisdom to this problem. It's sending me a bit mad trying to work it out. 

1. I've now tried all cables and am certain this isn't the problem. 
2. Booting into a USB with Ubuntu 20.04 with the system just idling the 'forbidden' symbol is on and off constantly. 

3. ActionParsnip, that command is exactly what I was looking for, thanks so much. I've attached the output of the dmesg command. It didn't enlighten me, if you have any insight, I'd love to hear.

I also used 'dmesg --follow' and when the 'forbidden' image pops up NOTHING HAPPENS!

So, I'm back to suspecting the Samsung display. 

Unfortunately, the only other display I have is an old Apple one, which doesn't have an HDMI port. I have ordered an adapter. So watch this space!

steve234 I'm blushing. And would be interested to know your latest build spec.

Thanks!

B

---

### Post by steve234 on 2021-09-06
Lol, its a laptop I got cheap on ebay. Has a mighty 2nd gen i3 with HD3000 integrated graphics. Came with 3GB ram, but now has a huge 8GB thanks to my local freecycle groups.

Apologies for getting off topic, good luck with troubleshooting the display once the adapter arrives

---

### Post by steve234 on 2021-09-06
Back on topic. I've had a quick look at theSAMSUNG ODYSSEY G5 32 user manual and noticed a couple of things

Have you been able to verify what resolution, refresh rate etc both 20.04 and 21.04. are using. Particulrly whether that is within the specs listed at pages 36 / 37 of the manual?

E.g. what does ```
xrandr
``` say about the resolution being put out by 20.04 and 21.04.

What does the monitor's self diagnosis tool report (page 29 of the manual), if anything, while the sign is showing?

---

### Post by barry-normal on 2021-09-06
Steve234, thanks so much for taking the time to read the manual! 

The self diagnosis displays a test screen so I think that's more for catastrophic failures than unspecified prohibitions... All the resolutions look legit. I've tried running at each setting. Same, unpredictable outcome.

The warning is only ever on screen for about one or two seconds at a time. It can flash up maybe a dozen times, then stop for a bit. Then pop up once an hour later. Or not for a day. I'm genuinely at a loss.

So, I took the step of wiping the system and re-installing 21.04 last night.

No prohibited sign yet. If nothing appears by end of the day I'll start re-installing stuff. But slowly. I'll post here if/when the sign makes a re-appearance.

Off topic. I really like the idea of building smart 'stuff' using scavenged, and low power components. I have a box full of bits from the last occasion I had time to daydream about creating robot nicknacks. One day! 

Thanks 

B

---

### Post by steve234 on 2021-09-06
No worries at all. Hopefully your systematic approach will pay off. I have my fingers crossed for you. 

> I have a box full of bits from the last occasion I had time to daydream about creating robot nicknacks. One day!  I know the feeling! Not long ago I set up a (currently tiny - line <20 subscribers) YouTube channel as a way to prompt myself to finish projects. Rather than get further off topic, PM me if you want more info / feel like collaborating would help you get through that bits box!

---

