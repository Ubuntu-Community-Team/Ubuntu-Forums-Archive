---
title: "Ubuntu doesn't play DVD good"
date: 2005-08-13
forum: General Help
---

### Post by diffuser78 on 2005-08-13
Hello,

I found that Ubuntu didnt play my DVDs clearly. There were jitters and picture was breaking in between. 

I used xine, gxine and totem. All of them dropped lots of frames.

Can sombody suggest some solution ?

Thanks

---

### Post by enquiry on 2005-08-13
First and foremost, turn on DMA by adding the following lines to /etc/hdparm.conf (then reboot):
```
/dev/dvd {
dma = on
}
```
You may get even better results by also adding these lines to /etc/X11/xorg.conf under Section "Device":
```
Option		"VideoOverlay"		"on"
Option		"RenderAccel" 		"true"
```

---

### Post by kitten on 2005-12-18
still fails for me, typical rubbish is:

[img]http://webspinning.org/dl/YesPM.png[/img]

*(then it gets much worse to the point of total gibberish)*

the video overlay and render stuff is a different format to the Section "Device", but looks similar to Section "Input Device", and in any case has no effect.

switching on the dma made no difference, either.

and this only works this far if i trigger the VOB directly ... firing up the DVD so that totem-xine catches it causes it to claim that i must be using a dvd encoded with libdvdcss ... i mean, so what?  i've already set up libdvdcss2 and it looks ok, but nothing good is happening for me.

i am coming to the conclusion that libdvdcss2 just doesn't work ](*,)

---

### Post by kitten on 2005-12-19
ok, forget it ... i got it figured, my DVD player is -too-old-, can't handle the high density recordings.  sigh, gotta get another one

---

### Post by earobinson on 2005-12-19
question, how did you figure otu that your dvd player was too old?

---

### Post by jbmalone on 2005-12-20
Windows used to do that for me, but for some reason when I switched over to Linux everything was fine.

---

