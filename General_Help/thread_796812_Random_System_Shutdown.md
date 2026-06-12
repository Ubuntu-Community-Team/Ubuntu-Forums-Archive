---
title: "Random System Shutdown"
date: 2008-05-16
forum: General Help
---

### Post by jpoRS on 2008-05-16
I am running Hardy on my hp Laptop with next to no problem.  BUT right before I upgraded from Gutsy, my computer started turning itself off.  No rhyme or reason to it, sometimes I would be writting in OO, sometimes working in FF, sometimes relaxing on my bed watching a DVD with VXL, sometimes I wasn't even in the room when it happened, and the only programs running were T-bird and Pidgin.

I hoped that upgrading to Hardy would help, but it still is happening, and just as unpredictably.  If anyone knows how I can diagnose this, it would be greatly appreciated.

Thanks,
jim

---

### Post by phidia on 2008-05-16
Check /var/log/messages and perhaps other log files there. 
Hopefully something there will tell why this is happening.

---

### Post by jpoRS on 2008-05-19
Ok, so I waited until it happened again so I wouldn't have to rifle through tons of information, and here is what I found.

May 19 10:32:07 Alfred syslogd 1.5.0#1ubuntu1: restart.

There is probably some more relevant stuff after that, there looks to be about two typed pages of messages after that, but as far as I can tell it is mostly just the normal system restart stuff.

What should I be looking for?

Also, it says restart, but the computer shuts down.  I don't know if that is relevant.

jim

---

