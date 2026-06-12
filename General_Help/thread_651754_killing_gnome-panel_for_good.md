---
title: "killing gnome-panel for good?"
date: 2007-12-27
forum: General Help
---

### Post by vexorian on 2007-12-27
So, here's the deal:

I recently got addicted to GTA:SA , a game which actually runs well enough on WINE to be playable, the biggest issue so far is that it does not restore the resolution once the game ends.

I made myself an script to restore the resolution for me, and everything is fine... except for the fact my buttons and menus on the top gnome panel get scrambled up after the resolution change, I tried locking them, no dice. And I always have to re order them, it is quite time consuming.

So, my current approach to this problem is closing the session and running the game on a "fail safe terminal" session. But this is time-consuming.

I recently thought of closing gnome-panel temporarily while the game is up and then calling it again. The problem is that I noticed that no matter how many times you kill gnome-panel it will always come back, hence the reason I am asking, how can you kill gnome-panel in a way that it won't come back until you manually call gnome-panel &
 ?

---

### Post by dlegend on 2007-12-27
Try the following:

1. Restart your computer or make it so only the default startup applications are running.
2. Go to the Menu > System > Sessions.
3. Click the "Current Session" tab. Find "gnome-panel" and highlight it.
4. Select Style "Normal".
5. Go to "Session Options" and click "Remember currently running applications".

Now try killing the panel.

I'm pretty sure this will work. The reason why it starts up again is because gnome-panel has the style of "restart".

---

