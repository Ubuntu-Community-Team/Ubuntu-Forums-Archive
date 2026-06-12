---
title: "[Solved]14.04 SB Audigy SE bug"
date: 2014-04-18
forum: General Help
---

### Post by HierisIngo on 2014-04-18
Hello,

When I play sound with my SB Audigy SE audio hardware I only hear sound from the left speaker. I've just got a fresh clean install of Ubuntu 14.04, I've set my audio balance at the middle. Other OSes are functioning correctly with this audio hardware including Ubuntu 13.10.

Is there anyway I can fix this, or do I have to wait until Ubuntu fixes this into an update?

Thanks!

---

### Post by francoj11 on 2014-04-19
Hi, I have the exact same problem. Ubuntu 14.04 64bits fresh install, SB Audigy SE card and 2.1 speakrs. Is there any workarround?

---

### Post by noe-saliege on 2014-04-20
Same problem with 14.04 64bits (tried the gnome and standard version), sound is mono with my sound blaster audigy, working fine in Win7 64bits and all distro based on Ubuntu 13.10, like Mint 16 etc ...

---

### Post by QDR06VV9 on 2014-04-20
I also have Audigy2 [SB Audigy 2 ZS [SB0353]]
Had to fiddle with it constantly.
My fix was to compile pulse audio by hand.
From [URL="http://ubuntuforums.org/showthread.php?t=2210602&p=12954078#post12954078"]HERE

[/URL]

---

### Post by francoj11 on 2014-04-21
Well this was strange. In my case, when I opened alsamixer in the console, all the volumes were at 63 left and 0 right. If you turn up the volume, the volume goes +1 on left and +1 on right, so I needed to turn all the way up to get 100 left and 100 right, and then I could turn down the volume in an even way.

---

### Post by Clockmender on 2014-04-21
Me thinks this is a bug - I used QasHctl to set everything correctly on my test machine - all is well but I am staying with 12.04LTS until audio is sorted on 14.04 Alsamixer does not set the enumerators and volumes levels correctly and consistently for my E-MU 0404 PCI on my test system or the 0404 PCIe card on my production system, QasHctl does on both. Get QasHctl from Synaptic BTW

---

### Post by agemini68 on 2014-04-23
Try this: 

1. In the terminal, type in alsamixer
2. Select your soundcard (press F6), mine was CA0106.
3. Look for stereo items, Bars with one channel muted (text beneath bars looks like "63<>0").
4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C). Or use arrow keys
5. Exit (ESC), no need to save manually.

---

### Post by Clockmender on 2014-04-24
I agree with agemini68, this is the route with alsamixer, however, QasHctl has a much better interface and tends to set the more complex stuff, such as which capture channels are active and where they are pointed. Alsamixer does the basics right, QasHctl does it **_all_** right and no I did not develop it! QasHctl also lets you control the channel lock on stereo channels as an option, I believe with Alsamixer you must get both left and right channels equal before they lock, but I may be wrong - I haven't used it for some time now, and I usually am wrong!!!!!!

---

### Post by agemini68 on 2014-04-25
I also found for some reason in the sound settings, you have to go into the input tab and select the right microphone even if you aren't using it. For me it was the one at the bottom, Microphone, SB0570 Audigy SE

---

### Post by Veliremus on 2014-05-05
I can confirm this issue for the Sound Blaster 5.1 VX, which also uses the dreaded (at least by me) CA0106 chip. Thank you guys so much for the tips about the levels in alsamixer/QasHctl. I had been looking for a solution for long... This worked for restoring my surround sound. Should this issue be reported as a bug, if it hasn't been already? It seems like a bug in alsa, right?

Incidentally, I also have to set the microphone to make it work. And I have to do it each time I boot into Ubuntu. It's quite annoying -- is there a way to make this setting stick?

---

### Post by mcsaba on 2014-06-03
Thank You [**[COLOR=#000000]agemini68[/COLOR]**]("http://ubuntuforums.org/member.php?u=1192924"), it works! (Audigy SE)

---

### Post by george53 on 2014-06-25
Soundblaster Audigy in P2. Left channel only. Alsamixer worked for me.
Thanks.

---

### Post by digees on 2014-07-15
Hi i have a SB0570  in Ubuntu Studio 14.04 64 Bits. Left channel only me to. Alsamixer fix work for me . Thank you.

---

### Post by alcides2 on 2014-09-25
> **agemini68 said:**
> Try this: 

1. In the terminal, type in alsamixer
2. Select your soundcard (press F6), mine was CA0106.
3. Look for stereo items, Bars with one channel muted (text beneath bars looks like "63<>0").
4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C). Or use arrow keys
5. Exit (ESC), no need to save manually.

If you are reading this give it a try. After days of searching how to fix the problem those five lines worked for me in Ubuntu 14.04 with a Sound Blaster SE of 24bits. Thanks, agemini68

---

### Post by jesselashcraft on 2014-11-17
> **runrickus said:**
> I also have Audigy2...My fix was to compile pulse audio by hand.

Everything seemed to be going fine until I got to step 5: make -jX[INDENT]
"Clarification: The X in "-jX" is a number of CPU cores your computer has +1. So if you have 4 cores CPU you use -j5, and if that CPU has Hyperthreading, then it would be -j9. "
[/INDENT]

Under "About This Computer", the processor is listed as: Intel® Core&#8482;2 CPU 6420 @ 2.13GHz × 2
so I guess I would use the value 3 (Core 2 + 1) as is "make -j3", correct? 

 How would I know if my computer CPU has Hyperthreading and if so, what should my input be? 
[COLOR=#DFE9F1][FONT=Verdana]


[/FONT][/COLOR]

---

### Post by HierisIngo on 2015-03-20
> **agemini68 said:**
> Try this: 

1. In the terminal, type in alsamixer
2. Select your soundcard (press F6), mine was CA0106.
3. Look for stereo items, Bars with one channel muted (text beneath bars looks like "63<>0").
4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C). Or use arrow keys
5. Exit (ESC), no need to save manually.
Thanks! This fixed it for me! ^_^


(Sorry for my super late reply, I got distracted the days after I made this topic and totally forgot about it...)

---

### Post by alejandro-coca-galviz on 2015-05-28
Thank you so much, you really help me, well it work for me, I have the same soundcard. now I have 5.1 sound channels.

---

