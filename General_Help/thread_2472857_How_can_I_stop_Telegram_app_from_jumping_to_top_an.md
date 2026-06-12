---
title: "How can I stop Telegram app from jumping to top and grabbing cursor?"
date: 2022-03-15
forum: General Help
---

### Post by AR_Kozz on 2022-03-15
Telegram's desktop app seizes top-window status and grabs the cursor every time something new comes up in whatever channel it's on. 

There seems to be no setting within Telegram to stop this misbehavior, and I can't seem to find a way to block it in settings, dconf or tweaks.

---

### Post by guiverc on 2022-03-15
Providing your release details & desktop may help; along with how you've installed the app (ie. is the a *deb* package, *snap* package etc), as I've not experienced the behavior you're talking about.

---

### Post by AR_Kozz on 2022-03-16
20.04 Gnome, Snap

I think a notification setting within the app called "draw attention to the window" was the culprit. 

But I'd still like to know how to make gnome override this so I'll wait a bit before marking it solved.

---

### Post by AR_Kozz on 2022-03-17
wait, cancel that, it still tops itself and grabs the cursor even with "draw attention to the window" unchecked. Unsolved. 

I've gone through every setting within the app and nothing stops it from doing this whenever something new comes up in the selected channel. Only workaround is to park it on a slow channel that rarely has anything new.

---

### Post by dragonfly41 on 2022-03-17
For desktop orchestration I use devilspie2.

You could write a devilspie2 script to move unwanted Telegram screen to another virtual workspace.
That is, push it off stage.

It is a workaround rather than a solution.

---

### Post by ActionParsnip on 2022-03-17
Is there an option in the application to run it minimised without devilspie? Worth investigating

---

