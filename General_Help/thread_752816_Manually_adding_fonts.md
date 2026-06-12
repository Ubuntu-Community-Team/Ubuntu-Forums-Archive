---
title: "Manually adding fonts"
date: 2008-04-12
forum: General Help
---

### Post by Hater Depot on 2008-04-12
I'm trying to add the GulimChe Korean TrueType font to my Ubuntu machine. I've followed various advice and nothing worked so far. I've tried pasting it into my fonts folder, but the system won't let me (I have admin privileges). I've tried pasting it in to the same folder as the other Microsoft fonts installed through the TrueType Core Fonts I got through the synaptic package manager. And I've tried creating my own .font folder in my home directory and putting it in there. No luck with any of this. Does anyone else have an idea?

---

### Post by reyhan on 2008-04-12
As root, 
open nautilus window and type "fonts:///" 
in the location bar. Now copy all the .ttf files there after that
Open a terminal windows and type
```
fc-cache -f -v
```

---

### Post by Hater Depot on 2008-04-12
I've tried to paste the font in there but I just always get the error "Not a directory".

---

