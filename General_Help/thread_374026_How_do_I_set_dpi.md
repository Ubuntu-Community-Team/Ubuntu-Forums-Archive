---
title: "How do I set dpi?"
date: 2007-03-02
forum: General Help
---

### Post by Michael%S on 2007-03-02
Just a simple question: how do I set the dpi for a display?
There's a guy whom I help with his Ubuntu machine, and he has this machine set up in his living room with a huge plasma screen. I had to fix the resolution so it wouldn't be way too low for that monitor, but once I did the fonts were too small to read. I understand it's possible to set a universal dpi for display, which is exactly what I want to do there. I just couldn't figure out how.

---

### Post by kerry_s on 2007-03-02
Add a line to your xorg.conf monitor section.

```
    Option         "DPI" "96 x 96"
```

go higher for larger, i think 30" is like "123 x 123"

gksu gedit /etc/X11/xorg.conf

---

