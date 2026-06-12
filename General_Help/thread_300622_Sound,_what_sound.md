---
title: "Sound, what sound?"
date: 2006-11-15
forum: General Help
---

### Post by Russty of Oz on 2006-11-15
Well, I searched the forum for how to get sound to work, but seeing as no one else has got the right answer yet, I am not getting too optimistic for a fix.

I have just a AC'97 sound card and it was working fine up until last week I think, but now NOTHING!  I thought it may have been muted, but no.  I checked that the plug was in, yep.  I went to the system settings and it looks Ok there but I clicked the reset or default (whichever it is) and then clicked test, but still silence!  I looked on the forum and did the killall esd that someone suggested, but I am still quiet.  This applies to everything.  Startup, music, video, the lot.

So, any clues?

Russty.

---

### Post by computx on 2006-11-16
Open a terminal window and type alsamixer.
You will see several volume controls. Press F5  to see them all. any that are muted will have a MM at the bottom. Arrow left and right to select the control you want and m to unmute/mute them. Up/down to adjust volume.

---

### Post by klokwyze on 2006-11-16
AC'97 audio is garbage in every OS. I remember I had an MSI-6330? or something like that and one day the sound just STOPPED working. Sound is critical for me so I just bought a new mobo after looking EVERYWHERE for a fix.

You probably have 3 options:
1.buy a new soundcard, turn off ac97 in bios.
2.do a fresh OS install
3.get a new mobo

Or you can scour message boards and dig in ubuntu for countless hours and reach the same conclusion. :evil:

---

### Post by calx on 2006-11-16
If you boot with a live cd does sound return?

---

### Post by Russty of Oz on 2006-11-16
> **computx said:**
> Open a terminal window and type alsamixer.
You will see several volume controls. Press F5  to see them all. any that are muted will have a MM at the bottom. Arrow left and right to select the control you want and m to unmute/mute them. Up/down to adjust volume.

Thanks computx!  

I did as you suggested and found that something called PCM was muted and unmuting it has solved the problem.  I thought that having the Master working was all that was needed, so I have learned something.:)  I wonder how it got muted in the first place?  It had been working before, so now I have added PCM to the volume controls in the task bar.

Well, I'm happy now, my problem was solved after all! 

Russty. :D

---

### Post by computx on 2006-11-17
Glad it is working. Possibly a random keystroke in some app muted it, Now you know how to fix it should it happen again.

---

### Post by strabes on 2006-11-17
That has happened to me randomly as well.

---

### Post by Russty of Oz on 2006-11-17
As you say, now we know how to fix it next time.  When I was seaching for an answer yesterday I found someone else asked the same question, so I put a link to this thread on their thread so they can try it too.

:D

---

