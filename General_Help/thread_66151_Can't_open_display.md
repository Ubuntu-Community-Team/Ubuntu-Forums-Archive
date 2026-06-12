---
title: "Can't open display???"
date: 2005-09-16
forum: General Help
---

### Post by uwido on 2005-09-16
guys what does the error if i receive the error "Can't open display", i receive that everytime i launch a game from cedega... what should i do to solve this problem.. need for immediate response from all of you guys...

---

### Post by bsussman on 2005-09-16
I assume you are trying to run from the commandline.

type:

 ```
> env|grep DISPLAY
``` 

We expect something like DISPLAY=:0.0

If not, you can manually type:

 ```
>export DISPLAY=:0.0
>whatever you want to run command goes here
``` 

but this needs to be set automatically for convenience.  IT usually is but I have not found where...

---

