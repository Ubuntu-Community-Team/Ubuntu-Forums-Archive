---
title: "Ubuntu crashes more times than Windows does"
date: 2006-11-22
forum: General Help
---

### Post by brottman on 2006-11-22
Running Edgy 6.10 (can't vouch for Dapper, I started on Edgy).

I started using Ubuntu during the beta stages of Edgy and absolutely LOVE it to death. I cannot see myself going back to Windows. Ever.

However, it does seem to crash more often than Windows ever did. I'll be working on homework in OpenOffice Word processor, and suddenly it won't let me type any more, and I can't select windows from the panel. In fact I can't seem to click on anything

At first I always had to hit the reset button and pray that OpenOffice would recover the document I was working on. I've figure out that I can do a CTRL-ALT-F1 to switch to a terminal, then come back with F7 and it seemed to fix the problem, until it happened the next time.

It doesn't always happen in OpenOffice either. That just happens to be the app I have been working in the most lately.

---

### Post by aysiu on 2006-11-22
Maybe you need to install the drivers for your video card.

What do you have--Nvidia? ATI?

---

### Post by hardyn on 2006-11-22
google around, and see how compatible your hardware has been with linux in general.  perhaps there is quirks with chipsets, or configurations...

but... random lockups and reboots is often a ram or motherboard problem.

---

### Post by Mirky on 2006-11-22
Did the same thing happen in windows?

If so you may have a different issue then the OS.
Over heating, memory, drivers, etc... can all cause a system to lock-up.

---

### Post by CatKiller on 2006-11-22
I managed to get that from time-to-time in Dapper when I had the experimental AllowGLXWithComposite option turned on in my xorg.conf, so it was my own fault really. Both Windows and Linux can be unstable if configured poorly, or if you're using bad drivers or what-have-you. It's just that it's easier to make Windows crash, since an application error can bring down the whole system and with Linux that rarely happens.

---

### Post by brottman on 2006-11-22
I had been testing Beryl on this copmputer for a while so I had this line in my xorg.conf:

   Option "AddARGBGLXVisuals" "True"

I just removed it, so I'll see if it helps things with that gone.

---

### Post by Ramses de Norre on 2006-11-22
The generic kernel was pretty buggy for me, the i386 is fairly stable here. You might consider a change of kernel if the issue persists.

---

### Post by blackmh on 2006-11-22
It's definitely berly issue. I had same problem myself. Although beryl worked excelent, sometimes same thing happened here so I disabled beryl-manager autostart and it didn't happend again.

---

