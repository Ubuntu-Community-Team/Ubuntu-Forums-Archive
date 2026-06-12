---
title: "Native games cause transparent windows to have backgrounds."
date: 2020-06-02
forum: General Help
---

### Post by kyza-one on 2020-06-02
I've noticed that some natively built games such as Terraria and ShellShock Live on Steam cause transparent windows to have backgrounds instead of staying transparent.

For example, here's the before and after of what ShellShock Live does to latte-dock. Terraria and other natively built games that I've tested do the same thing.

[IMG]https://dont-you-hate-it-when-a-url-is-super-long-and-it-looks-horrible.kyza.net/RZoIjz.png[/IMG]
[IMG]https://very-safe-link.kyza.net/VEKscC.png[/IMG]

I managed to get around this on ShellShock Live by launching it with Proton 4.2-9, but this is pretty hacky and it doesn't seem to work for other people.

Does anyone know of a better solution to keep all my windows transparent while these games are open?

Here's some of my system info.
[IMG]https://zenzizenzizenzic.kyza.net/oop3DZ.png[/IMG]

Thank you!

---

### Post by CatKiller on 2020-06-02
Many games will ask the window manager to disable the compositor for improved performance, since then the GPU isn't trying to do two jobs at the same time. 

> **kyza-one said:**
> Does anyone know of a better solution to keep all my windows transparent while these games are open?

The option to allow applications to turn off the compositor is in the KDE System Settings somewhere. I can't remember exactly where off the top of my head.

---

### Post by kyza-one on 2020-06-02
> **CatKiller said:**
> The option to allow applications to turn off the compositor is in the KDE System Settings somewhere. I can't remember exactly where off the top of my head.

Thank you! This solved the problem. For future reference, here's an image showing where the setting is.

[IMG]https://i-am.kyza.net/fX4FIu.png[/IMG]

---

