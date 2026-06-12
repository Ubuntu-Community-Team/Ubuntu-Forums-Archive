---
title: "Why do my SSH connections freeze (forcing me to kill terminal)"
date: 2007-09-08
forum: General Help
---

### Post by skelooth on 2007-09-08
Hello. I ssh into my workplace. After a recent move I have run into a disturbing problem. After just a few minutes of inactivity via ssh (whether it be via gedit, nautilus, or the commandline) the connection freezes and I have to xkill the window manually. This did not happen at my old apartment and I am using the same configuration sans a line i had to put in a config file:

GSSAPIAuthentication no

Otherwise I couldn't even connect, which I find so weird being that it worked fine w/o that before I moved.

I am connecting to a red hat enterprise 4 server and have never encountered this problem on it before moving. I could really use some ideas. I'm not even sure how to go about searching for an answer to this one.

---

### Post by skelooth on 2007-09-08
Can someone recommend where I can go to get help with this problem?

---

### Post by croto on 2007-09-12
Did you change your router at home? It may be the cause of the problem. Just to rule out that possibility, connect your computer *directly* to the modem, and see whether the problem persists.

---

