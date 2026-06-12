---
title: "Out of Disc Space Already?"
date: 2016-10-04
forum: General Help
---

### Post by sportscrazed2 on 2016-10-04
Installed ubuntu on a cloudbook with 32gb flash memory. I chose the option to use home encryption because i didn't think it would use any extra space. Well now I can't even download a simple small file because it tells me i'm out of space. I only have a few jpgs on the system for wallpapers.  There is no way this can be possible right?  Anyone have a fix?

update it's the android sdk i just need the platform tools what can i delete safely?

---

### Post by ian-weisser on 2016-10-04
It's probably very easy to fix if you answer a few simple questions.

Which version of Ubuntu? 14.04? 16.04? Something else?

Please show us the complete output of of the following commands:
```
df
df -i
ls /boot
dpkg -L | grep linux-image
```

---

