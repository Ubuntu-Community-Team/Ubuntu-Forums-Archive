---
title: "Palm Z22"
date: 2007-07-06
forum: General Help
---

### Post by nonmi9 on 2007-07-06
i can't get my Z22 to connect to Ubuntu, now im new to this OS so i have no real idea as to what im doing, but know a lot about computers...just not this OS...

---

### Post by defishguy on 2007-07-06
Can you post the steps that you have taken?

---

### Post by nonmi9 on 2007-07-07
name:Cradle
Type:USB
Timeout:2
Device: have tried all of them...
Speed:57600
Yes, used
 then nothing happens...

---

### Post by codesplice on 2007-07-08
To get my Palm to work, I had to make sure that the **visor** module was loaded (to handle the USB sync cradle).

Add "visor" to the last line in your /etc/modules file.
Either restart or manually load the module with
```
sudo modprobe visor
```

Hope this helps.

---

