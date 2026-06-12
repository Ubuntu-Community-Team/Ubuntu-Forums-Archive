---
title: "Screen does not go blank when I close the lid"
date: 2013-10-19
forum: General Help
---

### Post by Andric on 2013-10-19
I've searched around this forum and everywhere else on the internet for a solution. I only just realized that the screen doesn't go blank when I close the lid and it's a big problem because sometimes I have to go out and leave my torrents downloading, and when I get back, the whole keyboard is overheating because the screen is still bright against the keys.

I tried gconf-editor and dconf-tools to change the options of the power management from "do nothing" to "blank", I also tried to shut down the X screen from terminal before closing the lid. This command worked:

```
[COLOR=#000000]xset dpms force off[/COLOR]
```

But no matter what, the screen is still on.

I even tried to see if it was actually working, so I left the lid half-closed so that I could still use the touchpad and click enter in case I had to use the terminal command again, apparently the screen is "sleeping" since the pointer doesn't move and none of the keys do anything. And yet the screen is still on.

I'm running Ubuntu 12.04 LTS on an HP 6730b, does anyone else have a problem like this too? Anyone knows how to fix this?

Thanks in advance.

---

