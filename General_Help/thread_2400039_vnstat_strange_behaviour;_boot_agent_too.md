---
title: "vnstat strange behaviour; boot agent too"
date: 2018-09-01
forum: General Help
---

### Post by col48 on 2018-09-01
I don't run vnstat very often so this may have been happening for a little while:

```
vnstat -d -i lo
``` reports no data available but ```
vnstat -i lo
``` returns plausible data for "yesterday" and "today" - without quoting the actual dates.  Same goes for the external interface.

I am able to access the internet with no problem and also the printer - the only other device on the LAN.

What's going on?

ALSO - and I have included this here because it may be connected - if not, there is a coincidence at play:

For the last few days, when I power up the computer I get a message on screen (a Terminal-like screen) "Initialising Boot Agent" and offering up options, one of which is F1 - continue.  On pressing F1 it proceeds after a short delay to go to the usual dual-boot screen with the list of OS.  So this is not an Ubuntu problem.  This happens if at the previous shutdown I turned off the power at the socket after powering down the machine.  It seems that if I leave the power on at the socket I don't get the Boot Agent screen.  Probably started around 23 August.  Any ideas?

If the experts among you reckon the two issues are unrelated, I can could start a new thread.

---

