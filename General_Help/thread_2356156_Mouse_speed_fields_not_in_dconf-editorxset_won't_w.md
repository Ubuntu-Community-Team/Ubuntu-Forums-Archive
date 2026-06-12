---
title: "Mouse speed fields not in dconf-editor/xset won't work"
date: 2017-03-20
forum: General Help
---

### Post by janat08 on 2017-03-20
So the fields for speed are not in dconf and xset m doesn't change a thing.

---

### Post by efflandt on 2017-03-20
What did you set for the 2 numbers for acceleration and threshold following **xset m** (for example: xset m 2 5)? The default acceleration in 16.04 and 16.10 is 5 which may work for a mousepad, but is far too fast for me using a regular (wireless) mouse (which does not have any gui speed settings). Although acceleration 2 and threshold 5 works fine for me. But I wanted to change slow acceleration of my mouse without changing mousepad settings, so I use xinput. The xinput command alone gives you a list of device ids, and you can set things specific to that id. So to slow down my mouse (id=11) I added the following in **Startup Applications** to run when X starts:```
xinput --set-ptr-feedback 11 5 2 1
```

---

### Post by janat08 on 2017-03-21
I set max speeds of 16.../1 and 16... (16000) . I still have to swing my finger to cross screen (no change). Is xinput any more ironclad than xset?

---

