---
title: "where/how can you see if Laptop-mode-tools is enabled"
date: 2015-05-06
forum: General Help
---

### Post by sebastiaan5 on 2015-05-06
My question is if you can see somewhere if Laptop-mode-tools is enabled. I don't see it in my system monitor.

greetings,
Sebastiaan

---

### Post by ian-weisser on 2015-05-06
Here is one way:

```
$ sudo laptop_mode status    ## AC Power
[...lots of output...]
Laptop mode 
**enabled, not active** [unchanged]

$ sudo laptop_mode status    ## Battery Power
[...lots of output...]
Laptop mode 
**enabled, active** [unchanged]
```

---

