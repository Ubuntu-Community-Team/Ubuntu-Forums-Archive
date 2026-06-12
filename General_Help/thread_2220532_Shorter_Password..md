---
title: "Shorter Password."
date: 2014-04-28
forum: General Help
---

### Post by findingthebalance on 2014-04-28
[COLOR=#000000][FONT=Verdana]Hello, [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]When I log into my desktop account my password is quite long and every time I need to do something that requires root access I need to type in my password. Question; is there an option to set a shorter password just for the duration I am logged in and possibly have it expire after a certain time of inactivity?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thank you[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Also thank you for a terrific OS, I use Ubuntu, Mac, Windows and Ubuntu is my favorite by far[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-04-28
> **findingthebalance said:**
> [COLOR=#000000][FONT=Verdana]Question; is there an option to set a shorter password just for the duration I am logged in and possibly have it expire after a certain time of inactivity?[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

No. One password per account. If you organization's password requirements are onerous, then perhaps it's time to revisit how they are implementing that policy. PAM includes ways to login or authenticate that don't require long passwords at all: Fingerprints or hardware tokens (USB key, bluetooth device, card) etc.

There are also various workarounds you can try: Lengthen the sudo timeout, Open a root window, etc. I generally don't recommend those to most users. Most old-timers have at least one story of accidentally doing something very...unfortunate...when they forgot they were using a root window.

---

