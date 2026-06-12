---
title: "Help removing the Korganizer reminder daemon"
date: 2006-08-08
forum: General Help
---

### Post by Bigglez on 2006-08-08
Hello.
Kubuntu 6.06
I don't want the korgac process to run at start-up. Is there some way to prevent it from running?

I thought of putting a "killall korgac" into a script in Autostart... Seems crude.

Any ideas?

D.

---

### Post by Jucato on 2006-08-08
Go to /usr/share/autostart and more korgac.desktop somewhere else. I suggest moving it rather than deleting it, as you might someday want to bring it back and not write/make another .desktop file from scratch.

---

### Post by Bigglez on 2006-08-08
Ah, thanks for that. I had no idea about that path.

:D

---

