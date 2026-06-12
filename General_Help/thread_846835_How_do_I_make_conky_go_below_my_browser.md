---
title: "How do I make conky go below my browser"
date: 2008-07-01
forum: General Help
---

### Post by joy83 on 2008-07-01
So I am using Conky which displays my system information, it is working fine but I have one simple question. The conky display is on top of my browser, I mean when i open my browser the conky display is on the  right and on top of it. I want the display to be below the browser and attached to the screen. 
I have changed the settings in .conkyrc settings file and changed fork background to yes but it still does not change.
How can I change it so that the conky display is not on top of any program but below it?
:(

---

### Post by Doji on 2008-07-01
It's probably one of these:

```
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

Try pasting that into conkyrc

---

