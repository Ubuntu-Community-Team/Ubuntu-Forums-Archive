---
title: "xterm doesn't use color by default.."
date: 2007-12-17
forum: General Help
---

### Post by Mateo on 2007-12-17
not sure if this is an xterm problem or what.  I'm comparing my experience of xterm with the "console" (ctrl+alt+f1, etc).  In the "console" I type 'ls' and it's in color.  It's not in xterm (unless I do ls --color).  If I type 'elinks'  in the "console" it's in color.  It's not in xterm (and i don't know how to get it in color).

So what's up?

---

### Post by Lostincyberspace on 2007-12-17
Type bash and then there should be color for you. or just use gnome-terminal it uses bash by default. And has many more features.

---

### Post by Mateo on 2007-12-17
ok, that makes ls work.  elinks still doesn't use color.  maybe "console" uses something besides bash?

---

### Post by Lostincyberspace on 2007-12-17
The console in Ubuntu uses bash by default. I don't know what elinks is so I cant help.

---

### Post by Mateo on 2007-12-17
thanks anyways.

what does xterm use by default?  can i change it to use bash?

---

### Post by Lostincyberspace on 2007-12-17
I am not sure what xterm uses but you should be able to change it by adding ```
-e bash
``` to the launcher or where ever you run it.

---

### Post by vambo on 2007-12-17
> **Mateo said:**
> thanks anyways.

what does xterm use by default?  can i change it to use bash?

To find out which shell your using, do this

 ```
printenv | grep -i xterm
```

If you're running bash you should get this:
> XTERM_SHELL=/bin/bash

If not, you'll find out which shell xterm thinks it has.
Can't say I've ever had to set this manually. Best place is probably .bashrc

> export XTERM_SHELL=/bin/bash

Someone more knowledgeable may know more.

---

