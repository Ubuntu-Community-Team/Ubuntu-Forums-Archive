---
title: "Playing several videos with mplayer"
date: 2006-10-26
forum: General Help
---

### Post by Dearhell on 2006-10-26
I could play several videos on Breezy without any problem, on my laptop and on my Desktop computer, but since Dapper, I couldn't do it anymore.

I was in hope that it would be fixed on Edgy Eft, but still doesn't work.

I get this message when I try to play a second video with mplayer:

> Error opening/initializing the selected video_out (-vo) device

Any idea about this?

---

### Post by tommcd on 2006-10-27
I had the same problem. Open mplayer, right-click on the little pin and choose preferences. Click on the video tab. Select xv X11/Xv as video output, restart mplayer. It should work now.

---

### Post by Dearhell on 2006-10-27
Well, that was the option that I had selected by default and it doesn't work for me (I can't view several videos with it)

But getting your idea, I have tried x11 X11(XImage/Shm) as video output, and now I can play several videos at time. 

But I have notice that the reproduction's quality it's worse in x11 X11(XImage/Shm) mode

I don't understand why people can reproduce several videos with xv mode, and I can't in the two computers I have tried :-k

---

