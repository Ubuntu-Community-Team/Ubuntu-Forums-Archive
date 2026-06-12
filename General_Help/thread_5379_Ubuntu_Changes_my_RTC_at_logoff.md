---
title: "Ubuntu Changes my RTC at logoff"
date: 2004-11-18
forum: General Help
---

### Post by bob k on 2004-11-18
When I log off my real time clock gets set ahead by 6 hours. I am on a duel boot machine with win 2k and 2k has a real problem when the clock gets set froward and then gets set back as the clock gets synced with a time server after login.

Does anybody know what is causing this. When I start Ubuntu the clock is correct, and I know I set the correct timezone at install.

TIA

Bob

---

### Post by ynef on 2004-11-18
Sure. For some reason, the Ubuntu installer assumes that you want your PC's hardware clock to be set to UTC instead of your local time. Windows assumes that your PC is set to your local time instead of UTC. See why you get the wrong time? ;)

What you need to do is edit the /etc/default/rcS file where you have a line that says
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes
```
Simply set UTC to no.

Tadaa! :)

Edit: Oh yeah, you have to have root privileged to do this, of course. So you write:
sudo nano /etc/default/rcS

---

### Post by bob k on 2004-11-18
Thanks Ynef that did the trick. I would never have looked there.

Bob

---

