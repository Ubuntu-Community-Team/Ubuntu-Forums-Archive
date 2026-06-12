---
title: "Crackling Sounds..??"
date: 2007-01-20
forum: General Help
---

### Post by icehammer on 2007-01-20
My MP3s were playing absolutely clearly when i initaially installed GStreamer and a few other things - ogle, gxine, etc. But after i installed w32codecs.. my sounds have started to create a constant crackling sound.. its like my speaker is giving off more than what it should.. but it's absolutely clear in windows.. does w32codecs, or any other package, POSSIBLY spoil up MP3 codecs by any chance??

Any suggestions on what to do?? Thanks in advance.

---

### Post by Tiede on 2007-01-20
Hmmm... I fail to see which package would do that. Here's a thought:
Double-click the volume icon. In the window that pops up, locate the PCM slider. Make sure it is not set all the way to a hundred percent. Personally, I find 75-85% works just swell.

---

### Post by icehammer on 2007-01-20
Nope.. master volume is 85%.. volume in Rhythmbox is also similar.. still crackles..

---

### Post by Tiede on 2007-01-21
NOT the master volume. Check the **PCM** volume. The master being on 100% or not does not influence the crackling. Locate the PCM slider - usually the third one, and slide it down to around 75-85%.

---

### Post by dcstar on 2007-01-21
> **icehammer said:**
> 
........
Any suggestions on what to do?? Thanks in advance.

MP3 decoding uses CPU resources, use System Monitor to make sure some errant process isn't using up your CPU and therefore causing the MP3 process to miss out.

---

### Post by aragorn2909 on 2007-01-21
I don't know if this would help or not, but using some distros, I would get this same problem.  Crystal clear sound in windows and what sounds like interference/crackling in Linux.  Turns out, the distros I was having isues with, the modem speaker was turned on.  Once I turned it off, crystal clear sound.

A.B.

---

### Post by dcstar on 2007-01-21
> **aragorn2909 said:**
> I don't know if this would help or not, but using some distros, I would get this same problem.  Crystal clear sound in windows and what sounds like interference/crackling in Linux.  Turns out, the distros I was having isues with, the modem speaker was turned on.  Once I turned it off, crystal clear sound.

A.B.

The could be a factor if the sound hardware was sharing an interrupt with the modem, and the Linux kernel wasn't managing the situation correctly.

Certainly worth a try.

---

### Post by djemia on 2007-01-22
I'm not sure if this is the same problem--

I can hear what I would call "system sound" -- crackling & clicking that increases in intensity as system load increases -- constantly while running Ubuntu.  Through external speakers it's barely noticeable, but through headphones it's quite loud.
I'm running Edgy, but this problem has existed for me since Breezy.  Using an Acer Aspire 3620 laptop, ersatz intel sound card.

The modem speaker sounds like a possible culprit -- how would one turn that off?

---

### Post by icehammer on 2007-01-23
Well guys.. thanks for the tonnes of possibilties.. but to some extent, decreasing PCM volume decreased the crackling.. There are no errant high-CPU consuming processes going on, so that's not valid here.. 

It still crackles, but its much much better than before..
Thanks..

---

### Post by eggdeng on 2007-03-19
On a fresh install of Edgy, I am getting persistent crackling when I try to play any sound file. My set up is as follows:

lspci output:
VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)

cat /proc/asound/cards
 0 [V8233          ]: VIA8233 - VIA 8233
                      VIA 8233 with VIA1612A at 0x1800, irq 11
 1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                      VIA 82XX modem at 0xe000, irq 11

cat/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1

As the sound card and modem are sharing an IRQ, I would like to follow aragorn's suggestion and disable the modem. Any ideas as to how to go about doing this?

---

### Post by wpshooter on 2007-03-19
> **icehammer said:**
> My MP3s were playing absolutely clearly when i initaially installed GStreamer and a few other things - ogle, gxine, etc. But after i installed w32codecs.. my sounds have started to create a constant crackling sound.. its like my speaker is giving off more than what it should.. but it's absolutely clear in windows.. does w32codecs, or any other package, POSSIBLY spoil up MP3 codecs by any chance??

Any suggestions on what to do?? Thanks in advance.

A question ?

Did you install the w32codesc thru automatix ?

I did and I found that was a mistake.  Messed up my computer.  Had to reinstall.

Thanks.

---

### Post by jackrobinson on 2007-03-19
> **wpshooter said:**
> A question ?

Did you install the w32codesc thru automatix ?

I did and I found that was a mistake.  Messed up my computer.  Had to reinstall.

Thanks.
you installed one package from Automatix which has NO dependencies and could be simply uninstalled as follows:
```
sudo apt-get remove w32codecs
```
and for that you **reinstalled your OS**? 
ROFLMAO

---

### Post by ubunyou on 2008-03-16
I'm haveing the same issue as described above and I'm pretty convinced the crackling is coming from this whole modem speaker business, but I can't find any instructions on how to turn off my modem speaker, does anyone know how to do this?

This is my wireless NIC:
>lspci | grep "802.11"
04:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

Thanks in advance.

How I determined it was the modem interrupt problem:
1) I hear crackling
2) I disable my NIC - sudo ifdown wlan1 (note: I have no wired connection)
3) no crackling
4) I enable my NIC - sudo ifup wlan1
5) I hear crackling

---

### Post by ubunyou on 2008-03-16
turns out my speaker wire was touching the antenna of my wireless NIC.
The internet traffic through the antenna was inducing current through the speaker wire causing crackling.
Bizarre ...

---

