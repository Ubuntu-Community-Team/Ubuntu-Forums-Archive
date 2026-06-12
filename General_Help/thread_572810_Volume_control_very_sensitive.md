---
title: "Volume control very sensitive"
date: 2007-10-10
forum: General Help
---

### Post by amicitas on 2007-10-10
The volume control on my computer is very sensitive.  By the time i turn the volume to %50 I can barely hear the output.  Is there any way I can change this?  At this point I can effectively only use half the range on the volume sliders.

I am using ubuntu 7.10, though I have had this problem with 7.04 as well.

-amicitas

---

### Post by cudjoe on 2008-01-17
I have exactly the same issue.

The first half almost doesn't change anything, and the last 20% are very sensitive !

Did you find out a way to fix it ?
Thanks.

---

### Post by chaosrl on 2008-01-17
And here I thought I was the only one with this problem.

I've tweaked it to be a little better than before using the second slider in the volume mixer (I'm using ALSA, I'm not at my machine right now but I believe it was the PCM slider or something similar), but it's still not as nice as I'd like it to be.

---

### Post by cudjoe on 2008-01-18
Hi !

Thank you for the trick ! I put Master to 90%, and set PCM for the Volume applet : You're right, it's smoother, but not perfect.

The funny thing with using PCM, is that you can still hear something in the speakers when you put it to 0% :)

I now have an Intel integrated sound card, but I remember having the same problems with my Creative SB Live (could never adjust rear speakers volume properly). 
We might not be the only two people having this problem... I guess others just get used to it !

---

### Post by tmuka on 2008-02-18
I found this thread while searching for a solution to this annoyance... i'm still looking :)

---

### Post by amicitas on 2008-02-18
I never found a solution.  Trying to use the PCM slider did not help for me.

It looks as though they are changing the sound server in 8.04 so I am hoping things will work better once that comes out. 

I have to say this sound problem (along with the black windows) is the reason that I still primarily use XP. 

I have ubuntu running on my laptop as well and this problem does not exist.  On my computer I have an integrated sound card (Nforce 2).  I wonder how widespread this issue is.

---

### Post by geo909 on 2008-02-18
Same problem for me!
BTW, I think this called a "linear rate change" of the volume.
Every potentiometer or slider that controls volume, should change the rate logarithmically.

But, whatever it is called, it is a problem and in my opinion it is significant..
In general, ubuntu sucks when it comes to audio. I haven't managed to configure my soundcard properly, can't write through a mic etc..

---

### Post by rubin85 on 2008-06-30
bump..

I have this problem too, someone must know how to fix this

---

### Post by rubin85 on 2008-07-02
I SOLVED IT!!! kinda

go to preferences/keyboard shortcuts and disable volume down shortcut. On my computer (Thinkpad R60) it still controls the sound but not the master volume. Its as though when enabled, the volume down is multiplied, once by the comp and another time by ubuntu through the master volume. So now it doesn't show an image of the volume being lowered but it does anyways. Whereas it would take 5 clicks until I couldn't hear anymore before, it now takes about 12. 

I hope this bug gets fixed eventually, this quick fix will do for now. Hope this helps others out

---

