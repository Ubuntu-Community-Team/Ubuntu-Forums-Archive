---
title: "Messed up Window / Title Bar Buttons?"
date: 2018-01-08
forum: General Help
---

### Post by Matt_Boling on 2018-01-08
So, I decided to install Numix, used gnome tweak to change it to Numix, decided that I liked Ambiance a bit better, changed back, and now my desktop is screwed up in terms of the title bars.
Particularly, the minimize-maximize-close buttons are extremely fuzzy, and the themes don't seem to match as they did in a vanilla Ubuntu installation.

[IMG]https://image.ibb.co/k2giwm/Screenshot_from_2018_01_08_17_02_52.png[/IMG]

I tried reinstalling light themes and gnome-tweak-took, but to no avail.

Great start to my usage in Ubuntu 17.10!

Does anybody have a fix? It's visually distracting.

---

### Post by Matt_Boling on 2018-01-08
Found the solution:

```
dconf reset -f /
```

---

