---
title: "Bottom panel vanished!"
date: 2007-07-18
forum: General Help
---

### Post by kvonb on 2007-07-18
This has been happening for a few days now, when I boot up, or logout of X (Gnome), the bottom panel is not loaded.

Luckily the top panel is there and I issue the command "killall gnome-panel" and it comes back.

Anyone else having this problem, or has any idea what I can check?

Thanks, Kev :)

Some more info:

Feisty, clean install a few weeks ago, all latest updates except openoffice.  Gnome desktop, not running Beryl or Compiz, using Ubuntu restricted nvidia drivers (Nvidia 6600GT), GKrellm and sensors applett run on boot, nothing else.

---

### Post by Mongoose.wa on 2007-07-18
You can always just create a new panel and rebuild the default bottom one.

---

### Post by ibanez88 on 2007-07-18
I recall having a similar problem where the session that was being recalled on every login happened to be in the broken state.  Maybe try issuing killall gnome-panel and then saving the session.

---

### Post by Anzan on 2007-07-18
I've had this happen as well as losing the four workspaces in Desktop Effects. No idea why. 

The thing is, though, that it comes back.

I'd certainly like to know why things like this occur. But on the other hand the system seems to correct itself after a while. So I have a basic trust in it yet know that I could break it if I don't know how it works.

I hope someone who knows more about this will comment.

---

### Post by kvonb on 2007-07-19
It's very odd, this is only happening on my main workstation system, no other system does it, and I have Feisty on 3 other computers including my server.

I do recall that I was messing around in "sessions", and I disabled the following items:

1. Evolution Alarm notifier
2. Power management
3. Network manager
4. Restricted drivers manager

So I re-enabled those and I haven't had the problem since (touch wood!).

Come to think of it the screen would go into power-down mode while watching a video as well.

Seems like it was my disabling power management that did it, although I can't see why that would stop the bottom panel loading (raises one eyebrow O_o ).

So thanks for the replies, seems like it was my own stupidity after all :D.

Regards, Kev :).

---

### Post by kvonb on 2007-07-19
Nope, seems like I spoke too soon!

This morning both panels loaded, but no icons whatsoever!

So I'm still looking for ideas.

---

