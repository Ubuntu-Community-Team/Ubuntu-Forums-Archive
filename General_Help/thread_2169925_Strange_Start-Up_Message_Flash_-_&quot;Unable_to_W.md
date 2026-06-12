---
title: "Strange Start-Up Message Flash - &quot;Unable to Write Bytes: Broken Pipe&quot;"
date: 2013-08-24
forum: General Help
---

### Post by pstefanini on 2013-08-24
I've been running Ubuntu 12.04 but recently just after start-up, the follow message flashes onto the screen.  It seems to delay the boot time but does not seem to effect performance otherwise.  I'm not sure how serious this is, if I should try to fix or if I should leave well enouph alone.  Any advice appreciated. Phil

---

### Post by Dennis N on 2013-08-24
broken pipe: basically, as I understand it:

process A sends (pipes) its output as input to process B.
Now suppose process B closes (shuts off) before process A has sent everything.The pipe (connection) is "broken".

I don't worry about it when it appears, as I never see adverse effects.  I used to see this message sometimes during  the shutdown.

You can google "broken pipe linux" and get lots of hits.

---

### Post by Buntu Bunny on 2013-08-24
> **Dennis N said:**
> I don't worry about it when it appears, as I never see adverse effects.  I used to see this message sometimes during  the shutdown.

Ditto for me. I get it sometimes at shutdown, especially if I shutdown immediately after closing some programs. Apparently I'm "rushing" the process. Do google it. It mostly seems to happen at startup, but no one seems to be terribly bothered about it.

---

### Post by pstefanini on 2013-08-25
Thank you Buntu Bunny and Dennis N.... I greatly appreciate your response, explanation and reassurance.  I just started and no message appeared, first time in a week... so Thank you Both

---

### Post by Dennis N on 2013-08-25
Weird - just tried booting into my Xubuntu 12.04, and got the message "cound not write bytes: broken pipe" during boot up. This hung the boot process this time. Went to terminal, ordered a reboot, and she then booted ok. First time I have seen this broken pipe message disrupt something. Must be very rare.

---

### Post by Mephisto Pheles on 2013-09-12
I keep getting this on and off, on both xubuntu and Mint, it goes away again.. and comes back again... after a while.
Seems connected to some updates and probably even using bleachbit.
Everything running fine despite it.
Looks like somebody wants some attention every now and then :P
It's all just a pipe dream #-o

---

