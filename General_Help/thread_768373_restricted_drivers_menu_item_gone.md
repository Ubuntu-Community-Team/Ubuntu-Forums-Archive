---
title: "restricted drivers menu item gone"
date: 2008-04-26
forum: General Help
---

### Post by mephisto56 on 2008-04-26
I just wanted to try my restricted driver again (enabled and disabled once before) and now it's gone from the administration menu.

---

### Post by Qwerty_ on 2008-04-26
Try typing this into the terminal

gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk

that should bring you the restricted drivers menu.

---

### Post by mephisto56 on 2008-04-26
Thanks for the help. I just found out that it doesn't show when you make a second user. So logged out and logged in with primary account and it's there.

---

### Post by Qwerty_ on 2008-04-26
Ahh cool thanks for that.

---

### Post by Blastomorpha on 2008-04-26
What if I have the restricted drivers menu item, but no available driver in it?
I used to have a modem related one in there, in Gutsy...

---

