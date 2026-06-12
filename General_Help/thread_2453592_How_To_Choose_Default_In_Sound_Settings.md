---
title: "How To Choose Default In Sound Settings?"
date: 2020-11-13
forum: General Help
---

### Post by O)9(yo&amp;# on 2020-11-13
I have a Steinberg audio interface. Ubuntu recognizes it, but chooses "digital" output by default. I want it be "analog," but I have to change the setting every time. Is there a way to make "analog" the default setting?

---

### Post by Yellow Pasque on 2020-11-13
You can probably do it with 'pacmd' commands. Start here:
```
pacmd list-cards
```

---

### Post by O)9(yo&amp;# on 2020-11-19
> **Yellow Pasque said:**
> You can probably do it with 'pacmd' commands. Start here:
```
pacmd list-cards
```

Thanks for the tip, but for some reason it seems to be working now. After resetting it a few times, it is now holding, with Analog selected as default. Hopefully this will continue. If not, I'll have to try your suggestion. :)

---

