---
title: "User Switch Broke Resolution"
date: 2007-01-08
forum: General Help
---

### Post by justin on 2007-01-08
Recently, when I chose to switch users through gnome, the screen resolution dropped to 640x480, entirely by itself. When the new user logged in, their resolution had become 640x480. Now, when I switched back to my user, already logged in, the resolution remained at 1280x1024. It dropped to 640x480 upon logging out/in. When I tried switching back to 1280 x 1024 via System >> Preferences >> Screen Resolution, my only option obviously was 640x480. I tried running sudo dpkg-reconfigure xserver-xorg, which was able to get my resolution back to looking good, but now everything is very sluggish. Moving windows around is extremely slow, and scrolling through websites is also very sluggish. What might have caused this, and how can I get back to the way it was upon install?

Monitor: Acer AL1715 17" LCD
GFX: Intel Integrated Extreme Graphics 2 (Dell Dimension 3000)

---

### Post by Crooksey on 2007-01-08
Delete all resolutions in xorg.conf apart from the one you want to use.

---

### Post by justin on 2007-01-08
Tried that, still very sluggish. Why would it just break like this?

---

### Post by C-A on 2007-01-24
I am having the same problem. "Logging out" works fine but "switching users" changes my resolution until I log back in as the original user and log out.

Any known fix?

---

