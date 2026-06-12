---
title: "Assistance converting DVD (vob) files please"
date: 2007-02-20
forum: General Help
---

### Post by billdotson on 2007-02-20
For 2 weeks until I get my replacement WinTV-PVR-150 I am using the DVD player/recorder that is hooked up to the TV to record my shows.

I downloaded and installed acidrip and ripped it as an .avi The video was in .avi but the sound was off from the video either a second behind or ahead I coudn't really tell. How do I fix this issue?

Also now that I am trying to use acidrip again it isn't recognizing my DVD half of the time

I also tried vob copy but that didn't even get the vob file at all and I also tried to get the vob files into K3B and burn them as an iso and then burn that to a disc and acidrip it but I couldn't find how to burn as an image

I posted this in multimedia but I am not getting help there.

---

### Post by jethro10 on 2007-02-21
Right, this may help.

Sound out of sync. I process my avi's thru Avidemux which has an option to alter the timing of sound. You could do this but it will mean recoding and a potential loss of quality. Avidemux can play the modified stream BEFORE recording so you can check its lined up.

vob files are basically just MPEG2 files and i'm almost sure avidemux can read these also, So you can load in vob1, merge in vob2, vob3, etc and save out as an mpeg. Then use DVDStyler to make a DVD with a menu.

It may be possible just join the vobs with the 'cat' command from the terminal, saving it as an mpeg. If so it may load into DVDstyler to make a DVD as normal.

When I use DVDStyler, i just let it make an iso. then afterwards I right click it and choose the option to burn it.

---

### Post by billdotson on 2007-02-22
I have gotten vobcopy to work once and it got the video out and the audio was synced fine.  I just don't know how to go through and cut out sections (commercials) with Cinelerra)

Weird thing is though I can only get vobcopy to work half of the time.

---

### Post by jethro10 on 2007-02-23
> **billdotson said:**
> I have gotten vobcopy to work once and it got the video out and the audio was synced fine.  I just don't know how to go through and cut out sections (commercials) with Cinelerra)

Weird thing is though I can only get vobcopy to work half of the time.

Avidemux can cut sections easily. Just set an A and B marker ten Edit-->Cut

J

---

### Post by billdotson on 2007-02-23
avidemux seems like it makes the mpeg video really jerky.. why does it do this and why do I have to index it?  should I just get all my files in avi format?

---

