---
title: "Thinkpad t42 wifi"
date: 2008-04-04
forum: General Help
---

### Post by mbp84 on 2008-04-04
Ok so i recently installed 7.10 and I had my wifi working great with madwifi-ng driver r3434.  Now this was fine but aircrack didnt seem to work well.  It only worked using a backtrack cd and madwifi-ng driver r2834.  So I was able to switch to r2834 and have great success with aircrack but when connected to my wireless network it would disconnect every 5 min or less.  So I figure I will switch back to r3434.  When I did that now I cannot connect to wireless networks,  I see them in the wireless manager but it will not connect to anything.  Any ideas what happened?

---

### Post by mbp84 on 2008-04-05
bump.  Is there anyway to just dump any drivers at all that my be installed?  And start from scratch.

---

### Post by mbp84 on 2008-04-07
Bump

---

### Post by tgalati4 on 2008-05-13
I'm not familiar with aircrack but I have used kismet sniffer.  The special wireless driver puts the card into a "listen-only" mode.  So it may be working correctly.  You have to unload the wireless driver and reload the correct driver to resume normal wireless access.

A work-around is to use a second wireless card (in the pcmcia slot) and use that for sniffing and the built-in one to maintain wireless access.  It's not trivial to set up two wireless cards, but it's doable.

---

