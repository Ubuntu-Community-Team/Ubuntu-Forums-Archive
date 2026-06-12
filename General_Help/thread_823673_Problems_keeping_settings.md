---
title: "Problems keeping settings"
date: 2008-06-09
forum: General Help
---

### Post by space3di on 2008-06-09
Sorry if I'm asking a question that appears many times, i have checked this thread could find anything that would answer my question, which is.... i have installed the least ubuntu (8.04) and i have created the cube effect etc.... using compiz, but whenever i restart or shut down and start again ubuntu always start with the basic settings and then i have to manually change in berly manager to start the compiz setting. I have typed in 'compiz --replace' in the terminal, but that hasn't changed anything even after re-boot.

As you may have guess I'm very new to ubuntu so might not have the correct terminology.

Thanks.

---

### Post by wdaniels on 2008-06-09
Did you set the "Extra" effects in System->Appearance->Visual Effects? This should cause compiz to start by default. Or you could try:

```
gconftool-2 --set "/desktop/gnome/applications/window_manager/default" --type string "/usr/bin/compiz"
```

---

### Post by space3di on 2008-06-09
Thanks I'll try what you have suggested and let you know how I fair.

---

### Post by space3di on 2008-06-09
Cheers mate you a star. I think it was fault not setting the appearance to extra.

Thanks.

---

