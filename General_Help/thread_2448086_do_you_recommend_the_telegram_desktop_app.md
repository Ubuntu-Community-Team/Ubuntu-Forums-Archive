---
title: "do you recommend the telegram desktop app?"
date: 2020-08-01
forum: General Help
---

### Post by ronjjjg8885 on 2020-08-01
[https://desktop.telegram.org/](https://desktop.telegram.org/)
currently i'm using the web version.
i don't like security and privacy problems so that is why i'm asking

i would appriciate a simple answer much more because i'm not a linux savvy

thank you!

---

### Post by deadflowr on 2020-08-01
Sure.
Telegram has both a snap and flatpak version you can install on Ubuntu
Snap: [https://snapcraft.io/telegram-desktop]("https://snapcraft.io/telegram-desktop")
Flatpak: [https://flathub.org/apps/details/org.telegram.desktop]("https://flathub.org/apps/details/org.telegram.desktop")
Both are the same desktop app, choice is your as to which is preferable.

---

### Post by ronjjjg8885 on 2020-08-02
thanks!
can i also choose which permissions i give it like on android?

---

### Post by deadflowr on 2020-08-02
> **ronjjjg8885 said:**
> thanks!
can i also choose which permissions i give it like on android?

Flatpak permissions can be be easily set for flatpaks with another flatpak packages called flatseal:
[https://flathub.org/apps/details/com.github.tchx84.Flatseal]("https://flathub.org/apps/details/com.github.tchx84.Flatseal")

Snaps permissions are fairly strict.
When a snap is installed you can use the Software store to check which permissions are changeable.
(In Software you can look at Installed packages, then find the package and in it's home page it'll show a permission tab up top.)

Both also have in-depth command line options to set various controls too.
```
snap help
flatpak help
```
will give a quick overview of some functions for each.

---

### Post by ronjjjg8885 on 2020-08-03
interesting!

---

