---
title: "keyboard driver continuisly prints '6'"
date: 2008-01-12
forum: General Help
---

### Post by jonasmattsson on 2008-01-12
Hello,

I've just installed gutsy gibbon on a new PC, most things works like a charm of course :)
But every ten second it act as if I had pressed the button '6'. 
This happened already when I booted from the live CD, but I was then hooping that it would go away on the real deal, but it didn't.  I've tried to unplug the USB cable for the keyboard , but that didn't help either. I switched to TTY1 to see if it was Just in X, but it kept printing 6:es to the login prompt.
I'm kind of out of idea's by now, can anybody help? is there some kind of malfunctioning background processes that prints 6:es to the keyboard buffer or what is going on?

[Edit]
I've just tried to start it in recovery mode as well, but the same problem occurs.

---

### Post by p_quarles on 2008-01-12
That sounds terribly annoying.

This really sounds like a hardware problem, though. Have you used this same keyboard with any other operating systems? If you had/have Windows on this machine, do you get anything similar with the command prompt or text editor?

---

### Post by jonasmattsson on 2008-01-12
> **p_quarles said:**
> That sounds terribly annoying.

This really sounds like a hardware problem, though. Have you used this same keyboard with any other operating systems? If you had/have Windows on this machine, do you get anything similar with the command prompt or text editor?

I've tried it with ubuntu 7.04 on the same machine, and 7.04 on another machine, both earlier today. I've been using it with windows to, but that is a long time ago.

And I have tried rebooting without a keayboard, and the probem remains.

---

### Post by p_quarles on 2008-01-12
Well, that rules out the keyboard, then. 

You didn't say whether you had the same problem with 7.04 or Windows . . .

---

### Post by jonasmattsson on 2008-01-12
> **p_quarles said:**
> Well, that rules out the keyboard, then. 

You didn't say whether you had the same problem with 7.04 or Windows . . .

Sorry, I was a little unclear about that. No the problem did not occur earlier. It's my favorite keyboard.

---

### Post by p_quarles on 2008-01-12
So it's just happening with Ubuntu 7.10, and not with other versions of Ubuntu or Linux? 

If that's the case, then I'd guess some part of the CD was corrupted.

---

### Post by jonasmattsson on 2008-01-12
After booting from a kubuntu 7.04 cd it's suddenly the mute button that is going berseek, I'm guessing that this does not have anything to do with the keyboard or kbd drivers but actually the cpu, I think there is some kind of timer interrupt that is misinterpreted as a scancode interrupt. I ave a dual core 64 bit celeron cpu and are running a 32 bit kernel. Can this be a problem? Anyone?

---

### Post by p_quarles on 2008-01-12
I doubt that's the problem, but there's a relatively easy way to find out: download the 64-bit version of Ubuntu, burn a disk, and see what happens when you boot from that. If you still have the problem, then it's going to be something at a lower level than the kernel.

---

### Post by jonasmattsson on 2008-01-13
Hmm, well i don't think I will solve this poblem, since it's not my computer anyway, I'll go ahead and blame the cpu.
but for now, do you know if I can block the scancode, preferably at as low level as possible? 
I would like to simply tell the kernel not to bother about those mute button presses.

---

