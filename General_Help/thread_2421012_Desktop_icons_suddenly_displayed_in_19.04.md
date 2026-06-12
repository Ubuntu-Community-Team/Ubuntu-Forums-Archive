---
title: "Desktop icons suddenly displayed in 19.04"
date: 2019-06-14
forum: General Help
---

### Post by r-a-mercer on 2019-06-14
This afternoon I rebooted my Ubuntu 19.04 system and when logging back in all my home directory files where displayed on the Desktop:

[https://imgur.com/a/zVYt69A](https://imgur.com/a/zVYt69A)

For the Desktop Icons Extension I have everything unchecked. How can I remove all these files from my Desktop?

---

### Post by CatKiller on 2019-06-15
There's a setting somewhere for whether the "desktop directory" is ~/Desktop or ~. It looks like something has changed that setting. I don't use Gnome any more, so I couldn't tell you where it is, just that I remember seeing it.

---

### Post by r-a-mercer on 2019-06-15
Thanks! That was the problem. [FONT=courier new]~/.config/user-dirs.dir[/FONT] contained:

[FONT=courier new]XDG_DESKTOP_DIR="$HOME"[/FONT]

editing this to set the Desktop directory as [FONT=courier new]$HOME/Desktop[/FONT], running [FONT=courier new]xdg-user-dirs-update[/FONT], logging out, and logging back in again did the trick!

---

