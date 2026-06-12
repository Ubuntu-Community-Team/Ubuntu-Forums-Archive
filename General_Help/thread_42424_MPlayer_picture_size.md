---
title: "MPlayer picture size"
date: 2005-06-17
forum: General Help
---

### Post by foxy123 on 2005-06-17
The problem is that if I play a movie or dvd the resolution on the screen quite strange. I mean I've got a small picture which does not resize in full-screen mode, while on kaffeine it's fine. I used MPlayer before and it was ok.

---

### Post by clb137 on 2005-06-17
[QUOTE=foxy123]The problem is that if I play a movie or dvd the resolution on the screen quite strange. I mean I've got a small picture which does not resize in full-screen mode, while on kaffeine it's fine. I used MPlayer before and it was ok.[/QUOTE]


Why are u using mplayer???? 

have you installed ALL the codecs?

xine is much better faster and a better set of controls, it also handels more file formats (please correct me if i am not correct)

clinton

---

### Post by not_yet on 2005-06-17
right click on the mplayer screen for preferences / you can adjust scren size from there

---

### Post by ow50 on 2005-06-17
You are probably using a wrong video driver. You can change it in GMPlayer's preferences dialog, or if using MPlayer, type "mplayer -vo help" for a list. Start MPlayer with "mplayer -vo <driver>" or put line "vo=<driver>" in your ~/.mplayer/config file. I use "xv" as my video driver. That should be fairly common. Some of the video drivers don't work well or require lots of CPU power, so choose wisely.

[QUOTE=clb137]Why are u using mplayer????[/QUOTE]
- Support for lots of formats (I find it hard to believe xine would be ahead on this)
- Everything is configurable (just read the man pages).
- Very good subtitle quality (font anti-aliasing and all that)

If you run into problems with xine or totem, you're just stuck with them. If you have problems with mplayer, you just read the man pages and change something in config file or start mplayer with different options and all works again.

---

### Post by clb137 on 2005-06-18
[QUOTE=ow50]You are probably using a wrong video driver. You can change it in GMPlayer's preferences dialog, or if using MPlayer, type "mplayer -vo help" for a list. Start MPlayer with "mplayer -vo <driver>" or put line "vo=<driver>" in your ~/.mplayer/config file. I use "xv" as my video driver. That should be fairly common. Some of the video drivers don't work well or require lots of CPU power, so choose wisely.


- Support for lots of formats (I find it hard to believe xine would be ahead on this)
- Everything is configurable (just read the man pages).
- Very good subtitle quality (font anti-aliasing and all that)

If you run into problems with xine or totem, you're just stuck with them. If you have problems with mplayer, you just read the man pages and change something in config file or start mplayer with different options and all works again.[/QUOTE]


never had any problems with xine?????

---

### Post by foxy123 on 2005-06-18
[QUOTE=ow50]You are probably using a wrong video driver. [/QUOTE]

That was it... Got X11 instead XV... However, now I've got another problem. DVDs play with pauses and lags and sound (video) is delayed. 've checked dma and it's on:

```
/dev/hdc:
 using_dma    =  1 (on)

ATAPI CD-ROM, with removable media
        Model Number:       _NEC DVD_RW ND-3500AG
        Serial Number:
        Firmware Revision:  2.C8
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 3ms.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
``` 

why is that?

---

### Post by ow50 on 2005-06-18
[QUOTE=foxy123]DVDs play with pauses and lags and sound (video) is delayed.[/QUOTE]
In addition to DVD drive performance, check the CPU usage while playing. Either one could be the problem. Also, start mplayer from command line and see if the output has anything useful.

---

