---
title: "Keyboard shortcuts on certain boot-ups just... don't respond?"
date: 2015-08-03
forum: General Help
---

### Post by Roasted on 2015-08-03
Hello friends. I'm on 14.04.2 and I'm noticing something on my laptop. I don't suspend my laptop, I always shut it down. Certain times when I power it up, I seemingly have some missing keyboard shortcuts. Things like the super key to activate dash, alt for hud, and my workspace switcher shortcuts all work. But other shortcuts such as CTRL ALT T for terminal, or CTRL ALT 8, CTRL ALT 9, CTRL ALT 0 (custom shortcuts I added) all don't work.

The fix? Log out and back in. Has anybody ever seen this? I'm a little unsure of what is causing it, and I haven't really seen much in my search that's relevant as most results are for older versions of Ubuntu.

That brings up another question. At one point in time, I could just run ALT+F2 and type in "unity --replace" and it would effectively restart Unity right there within my session. If the keyboard shortcuts took a dive, no problem, I could just run that and carry on. *BUT* these days, unity --replace... logs me out entirely. I can log in and get things working again, but uh... what? Really? At some point in time this behavior clearly changed, which was my previous workaround for when this issue came up. But now that I cannot just reboot Unity quick, it's more of a pain to deal with. I've gotten into the habit of logging in and hitting CTRL ALT T to see if my keyboard shortcuts work. If they do, great. If not, log out and back in before I get to any work (which really begs the question on why I even have to do this, at least when I look at this situation from a "what if I was a new user?" standpoint).

Any insight?

Thanks ahead of time!

---

### Post by CantankRus on 2015-08-03
Are you using conky on your desktop?
Conky seems to interfere with with the focusing of the desktop and some 
shortcuts don't work until the desktop is clicked.
If I have no windows open but the words "Ubuntu Desktop" are not displayed on left side of the panel
that's when some shortcuts fail. 
Clicking on the desktop brings up the words and shortcuts work.

I used to use **setsid unity** fequently but get the logout as you do. 
I just use **compiz --replace** now to reload compiz/unity.
Usually just reloads but occasionally still logs me out.

---

### Post by Roasted on 2015-08-03
Thanks for the info. I'm not using conky at all though. :(

---

### Post by CantankRus on 2015-08-03
> **Roasted said:**
> Thanks for the info. I'm not using conky at all though. :(
When shortcuts fail do you see "Ubuntu Desktop" in the panel?

---

### Post by Roasted on 2015-08-03
I haven't taken notice. I'll keep an eye out next time it happens. What's your thinking in regard to seeing that text up top?

---

### Post by CantankRus on 2015-08-03
Seems to be some sort of focus issue.
Doesn't release back to desktop when all windows closed...like being in some limbo state.
If I use ccsm to give conky no focus, problem never occurs.

---

