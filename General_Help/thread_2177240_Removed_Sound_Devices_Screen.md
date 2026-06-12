---
title: "Removed Sound Devices Screen"
date: 2013-09-27
forum: General Help
---

### Post by SantaFe on 2013-09-27
Last week I went ahead and added KDE to my Dell Studio 1745 laptop, joining Xfce & LXDE.  Haven't had any problems per say, but have had the following screen pop up yesterday & today (see picture below).  The problem started yesterday, when I switched external monitors on the laptop.  Need an external one, because a "friend" of mine cracked the laptop screen and hasn't had it fixed yet, so I've been using my 32" Westinghouse LED tv via HDMI.

Anyway, yesterday I borrowed a Gateway 24" LED monitor (without speakers) to see if I liked it better, but went back to the one I'm using now.  That's when I got these pop-ups.  Now I KNOW I haven't removed anything in my laptop, so my question is, is this really anything to be worried about, as everything still works, and Xfce & LXDE don't give me any errors like that, either pop-up or in the error logs.

Now I, not knowing any better, forgot & clicked on Do Not Ask Again For These Devices & clicked on the NO button.  Is this anything to worry about?  Is there a way to change my mind if I was Supposed to remove those devices?  Will this long post be optioned into a Mini Series? :D :D

Ah well, everything works, I can still capture/play audio, so hopefully everything's OK.  THANKS for reading this! ;)

---

### Post by DuckHook on 2013-09-27
The pop up is saying that it no longer detects certain HW that it detected in the past. This probably has to do with switching from your TV to a monitor. Since your TV has audio HW, the HDMI interface likely initially detected (and made allowance for) audio output to the TV. When you switched the output to a monitor, the HDMI interface no longer detected audio, so the pop up was alerting you to this. Even if you had told the system to forget about such devices, it would likely have reinstalled them anyway once you hooked your TV back up. But since you told the system to *not* forget its prior HW config, then you should be working just as before with your TV, as if nothing had changed. Can you direct sound to output through your TV? If so, then you have full functionality and really have nothing further to worry about. And if your sound is output through dedicated speakers, then the TV sound option is superfluous anyway and you won't be missing it. You've already mentioned that the rest of your audio functions work properly, so if I were you, I wouldn't pay this matter any further attention.

---

### Post by SantaFe on 2013-09-28
Thanks, that's what I thought, but wanted to make sure about.  :lolflag:

---

