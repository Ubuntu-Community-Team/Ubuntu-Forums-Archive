---
title: "Remove icons"
date: 2019-01-11
forum: General Help
---

### Post by torbentf on 2019-01-11
Hi,
Down at the left hand corner of the desk top there is an icon that calls up a screen from which you can choose your application. What is that screen called?
In that screen I have 2 icons (they used to be for Skype, but the icon has disppeared and only the text "Skype" shows up) which I want to remove. Where do I find the appropiate files. They are not in /usr/share/applications.
I have seen several methods in this forum, but none of them works.
best regards
torben

---

### Post by CatKiller on 2019-01-11
~/.local/share/applications

---

### Post by torbentf on 2019-01-12
Hi CatKiller,
I found a skype_skypeforlinux.desktop in /var/lib/snapd/desktop/applications. When I moved that, the "ghost" icons disappeared.
Solved
best regards
torben

---

