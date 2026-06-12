---
title: "Problem with gnome-terminal and custom command"
date: 2008-05-23
forum: General Help
---

### Post by Nuxly on 2008-05-23
Hello there.
I've set a custom command to the default profile but accidentally made gnome-terminal close when the command has been executed. It closes as soon as I start it, the window won't even appear, and I have no other profile. I've taken a look at the documentation but there doesn't seem to be any safemode or anything else.
What should I do?
Thanks

Using Ubuntu 8 hh.

---

### Post by Nuxly on 2008-05-23
nvm, fixed it.
If you have the same problem, here is what I did:
I switched to tty2, typed this:
su root
cd /bin
mv bash /bash

As the custom command was bash, gnome-terminal wasn't able to find it and returned an error, and its window showed up. I just removed the command and moved bash back to /bin.

---

