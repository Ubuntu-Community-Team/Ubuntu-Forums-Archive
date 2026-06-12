---
title: "A bash/dash root shell question"
date: 2007-05-09
forum: General Help
---

### Post by IgnorantGuru on 2007-05-09
Edgy...  I realize root sh defaults to dash.  But even when I run a script that begins with "#!/bin/bash", sh stills seems to use dash.  If I run it explicitly with bash then it's okay.  Is this normal?

IOW if I am in a root dash shell (the default?), and type 'sh myscript', and the first line is "#!/bin/bash", shouldn't it use bash?

I read this discussion and it seems to imply it should work this way...
[https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463)

---

### Post by DoktorSeven on 2007-05-09
No, since the first line is used when a script is ran with ./scriptname (after chmod +x), not with a program

Running it with sh scriptname runs the program with whatever /bin/sh points to, which by default is dash, *regardless of what's in the first line.*

As noted, chmod +x scriptname then ./scriptname will run it with bash as you desire.

---

### Post by IgnorantGuru on 2007-05-09
Gotcha - thanks!

---

