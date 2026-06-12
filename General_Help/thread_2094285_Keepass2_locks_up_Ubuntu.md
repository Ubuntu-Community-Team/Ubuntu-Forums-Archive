---
title: "Keepass2 locks up Ubuntu?"
date: 2012-12-13
forum: General Help
---

### Post by abexman on 2012-12-13
Several times since I installed Keepass 2.20.1 on Ubuntu 12.04LTS I have had seemingly random lockups of my workspace. My suspicion is this is something to do with Keepass since all ~3 times it happened I was in process of using it. 

Most recently this happened when I was right mouse button clicking in Keepass2, the menu appeared and everything froze. A Youtube video I had been playing continued in the background since I could hear its audio still running. This makes me think its Keepass2 (or mono??) and graphical. In fact when I switched workspaces the graphical element, spuriously stayed on the screen in the new workspace as shown here:

[http://s5.postimage.org/7byahy953/untitled.jpg](http://s5.postimage.org/7byahy953/untitled.jpg)

When this happens the mouse cursor stays active, but I cannot click on anything in the Workspace. Some keyboard commands seem to work like ctrl+alt+f1 and ctrl+alt+right arrow, etc. Launching a terminal does NOT work. I am able to switch to an alternate workspace for example. Even in the alternate workspace though it seems things are a bit restricted though I can launch a terminal window and run some commands in the terminal. This is what I did. 

I then ran ps -A and got a list of processes (I think). Oddly Keepass did not appear in the list?! Did it perhaps crash? What can I do to troubleshoot this in the future?

---

### Post by jmcgee on 2013-03-10
I have the exact same problem.  Anyone else, and anyone got a resolution to this?

---

### Post by stinkeye on 2013-03-10
Doesn't Keepass2 use Mono?
Perhaps the fault lies in mono.

Any advantage in using Keepass2 over KeepassX which
doesn't use mono and works fine here?

---

