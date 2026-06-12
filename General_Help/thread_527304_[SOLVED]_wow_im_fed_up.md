---
title: "[SOLVED] wow im fed up"
date: 2007-08-16
forum: General Help
---

### Post by Aesir09 on 2007-08-16
um so every time i want to hear sound through my headphones, i have to get up move my whole desk, and switch my speaker with my headphones?

cmon..... help?

---

### Post by Vince4Amy on 2007-08-16
So you're saying that the speakers are not working or the headphone jack in the speakers are not working?

This sounds to me more like a speaker malfunction if you can get sound output from the soundcard. Make sure that your speakers are connected correctly.

---

### Post by Aesir09 on 2007-08-16
they are dude, what im saying is the (black Jack[headphone jack] doesnt work, right now i have my headphones plugged into where my speakers should be, just so i can use them, so i can only use one

i cant use both speakers and headphones like in windows :(

---

### Post by Vince4Amy on 2007-08-16
Well I put this down to a speaker fault to be honest. Maybe just coincidence. I Don't think headphone jacks on the speakers themselves have anything to do with the soundcard or Sound settings on the computers. These aren't USB speakers are they by any chance?

---

### Post by Aesir09 on 2007-08-16
ok they are not usb, and i have seen posts about people having this problem maybe this will help:

```
dom@ubuntu:~$ sudo lshw -C sound
Password:
  *-multimedia            
       description: Multimedia audio controller
       product: [SB Live! Value] EMU10k1X
       vendor: Creative Labs
       physical id: 9
       bus info: pci@02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1X latency=64 maxlatency=20 mingnt=2
       resources: ioport:ec40-ec5f irq:18

```


```
dom@ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: [SB Live! Value] EMU10k1X
       vendor: Creative Labs
       physical id: 9
       bus info: pci@02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1X latency=64 maxlatency=20 mingnt=2
       resources: ioport:ec40-ec5f irq:18

```

---

### Post by igknighted on 2007-08-16
You really need to be more specific.  Is the "black jack" on your computer case or the speakers?  If it is on your case, there might be a software issue.  If this is the case we will need to know how it is connected inside (to the motherboard or the creative soundcard for example).  If it is on the speakers, then the issue is with your speakers.  Thats all handled by the hardware, the OS has nothing to do with it.

---

### Post by Aesir09 on 2007-08-16
ok then, well the green(for speakers) as well as the black jack(for headphones are both on my box

---

### Post by UK-Wobbie on 2007-08-16
> **Aesir09 said:**
> ok then, well the green(for speakers) as well as the black jack(for headphones are both on my box

Get your self a Audio splitter! 2 out ,1 in :)
So you can plug up your speakers and headphones

[IMG]http://image.ebuyer.com/UK/P0117643_C0000024_P0000000.jpg[/IMG]

Site [http://www.ebuyer.com/UK/product/117643](http://www.ebuyer.com/UK/product/117643)

:)

---

### Post by Aesir09 on 2007-08-16
looks like ill have to do that since ubuntu sucks

---

### Post by UK-Wobbie on 2007-08-16
> **Aesir09 said:**
> looks like ill have to do that since ubuntu sucks

:lolflag: It's the easy way lol

---

### Post by bapoumba on 2007-08-16
I'll suppose you are having a bad day, Aesir09 ;)

---

### Post by diatribe on 2007-08-16
I fail to see why you would utilise the speakers and headphones at the same time anyway

---

### Post by ugm6hr on 2007-08-16
Have you tried adjusting the settings in alsamixer - use "M" to mute/unmute, and left/right/up/down arrows and Tab to edit various settings.

If you maximise and unmute everything, you might find it works:
```
alsamixer
```

---

### Post by Lord Illidan on 2007-08-16
It could also be that your alsa version is out of date, perhaps? Had a similar problem on a Sony Vaio with Edgy, had to compile new alsa drivers, which are now in Feisty, luckily.

---

### Post by Lord Illidan on 2007-08-16
> **diatribe said:**
> I fail to see why you would utilise the speakers and headphones at the same time anyway

DJing perhaps..but true, it is kinda strange.

---

### Post by caro on 2007-08-16
> **diatribe said:**
> I fail to see why you would utilise the speakers and headphones at the same time anyway

Beat me to it.  I was thinking the same thing.

---

### Post by Aesir09 on 2007-08-16
well ubuntu keeps freezing during boot and ctrl+alt+F1 doesnt work some loading error so im kwitching to kubuntu anyways, thanks anyways guys

PS im having a bad day, mom took cell phone and xbox controllers and i couldnt see the girl i wanted too. :(

---

