---
title: "Ubuntu feisty machine can't be left on."
date: 2007-05-16
forum: General Help
---

### Post by chaskins on 2007-05-16
Hi,

I have a strange issue with my feisty install. Everything works fine whilst I am working on the machine but if left for a period of time the monitor goes blanks and the caps-lock & scroll-lock leds flash on the keyboard. Whatever I do does not seem to get it back.

I have turned of power saving as I though that might be the issue.

Last night I installed the Nvidia driver thinking that may help. I left it running this morning when I went to work. I could access it via ssh for about 2 hours and now it's gone again.

Could this be down to an over-heating problem. 

Thanks for any help.

regards,

Chris

---

### Post by vtel57 on 2007-05-16
> Could this be down to an over-heating problem. 

That's very possible.

---

### Post by srt4play on 2007-05-16
> **chaskins said:**
> I have turned of power saving as I though that might be the issue.

Check in the BIOS for monitor power saving settings to turn off also.

Blinking caps and num = kernel panic (crash) which are never recoverable.

---

### Post by Soybean on 2007-05-16
It's probably something more serious than this, but have you tried switching your screensaver to "Blank Screen"? It sounds like you're only having problems when your computer is unattended for a while, and that makes me think "screensaver." Some of those built-in screensavers can be surprisingly hard on some computers.

---

### Post by loathsome on 2007-05-16
Whats your CPU temperatures? If you don't know, get [http://cpuspeedy.sourceforge.net/](http://cpuspeedy.sourceforge.net/) and do a ```
sudo cpuspeedy -s
```

---

