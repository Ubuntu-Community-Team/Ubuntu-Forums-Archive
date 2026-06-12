---
title: "nohup and killall don't understand aliases?"
date: 2007-11-23
forum: General Help
---

### Post by Interestedinthepenguin on 2007-11-23
If I do ```
 nohup awn
```
('awn' for avant-window-navigator), or ```
killall awn
```, I get: ```
nohup: cannot run command `awn': No such file or directory
``` and ```
awn: no process killed

```

Are aliases really incompatible with nohup and killall, or is there some hidden setting that I haven't taken care of?  

Please, don't be so![-o< 

Thanks.

---

### Post by Interestedinthepenguin on 2007-11-24
I patched the problem by creating a variable that matches the name of my alias:): ```
awn=avant-window-navigator
```.

Execute like this: ```
killall $awn
```

..but if anyone has a better solution: please, let me know.

---

