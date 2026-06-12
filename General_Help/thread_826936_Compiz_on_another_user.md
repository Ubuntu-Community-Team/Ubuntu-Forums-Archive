---
title: "Compiz on another user"
date: 2008-06-12
forum: General Help
---

### Post by Damanther on 2008-06-12
OK, I've set up compiz on my account. It all works great.

My wife also has a login, but it is still set to use the default kde window manager. I can start the fusion-icon and set it to compiz, but when she logs out and back in, it is back to the kde default.

How do I get her account to keep those settings? I guess I could put the fusion-icon in her startup, but I don't have to do that for my account. I knew how to set the default window manager gconf/gnome, I'm just not sure how do do the same thing for kde.

---

### Post by Forlong on 2008-06-14
What graphics card & driver are you using?

---

### Post by Damanther on 2008-06-29
Its a Nvidia 6200.

On an AMD 64 bit.

Mike

---

### Post by Forlong on 2008-06-29
Alright, then you should be capable of loading Compiz by default on a secondary user.

Just when your wife is about to log out (no running applications, just plain KDE plus Compiz) let her save the current session.

Next time, Compiz should be the default window manager.

---

