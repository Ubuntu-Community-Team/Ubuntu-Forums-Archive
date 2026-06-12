---
title: "xorg file"
date: 2008-06-11
forum: General Help
---

### Post by SpenceMakesSense on 2008-06-11
I recently installed nvidia settings to get my desktop cloned to me tv but i got undesirable results, so when I disabled everything I had enables and unistalled it but I think that it still kept the xorg file the same because my compiz effects are very laggy. What should my xorg file say so its back to normal. If I end up having to reinstall themes ect. I dont care. But I really dont know much about it.

---

### Post by ajmorris on 2008-06-11
> **SpenceMakesSense said:**
> I recently installed nvidia settings to get my desktop cloned to me tv but i got undesirable results, so when I disabled everything I had enables and unistalled it but I think that it still kept the xorg file the same because my compiz effects are very laggy. What should my xorg file say so its back to normal. If I end up having to reinstall themes ect. I dont care. But I really dont know much about it.

Hi there,
You can regenerate your xorg.conf file by doing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
from a terminal, then just restart X after it (CTRL+ALT+BACKSPACE)

AJ

---

