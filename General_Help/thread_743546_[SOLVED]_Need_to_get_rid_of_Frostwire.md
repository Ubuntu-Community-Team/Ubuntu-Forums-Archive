---
title: "[SOLVED] Need to get rid of Frostwire"
date: 2008-04-02
forum: General Help
---

### Post by djmoore85 on 2008-04-02
I need to get rid of Frostwire, I downloaded it yet every time I go to open it from the menu it doesn't do anything. No program load or anything. My question is how do I find it to delete it, I can't delete it from the task bar menu. Thanx in advance. Also, any suggestions on a good P2P music program for Ubuntu?

---

### Post by ryanhaigh on 2008-04-02
How did you install it? If you got a .deb file from somewhere then the command 
```
sudo apt-get remove frostwire
``` should do it. Alternately you can go to system>admin>synaptic package manager, search for it, mark for removal and apply.

Before you do that though you may want to try running it from a terminal to see if there are error messages that could help you get it going.

I know there is a client for the soulseek network in the repositories but can't recall what it is called maybe nicotine?

---

### Post by djmoore85 on 2008-04-03
Thanks man I appreciate it problem solved

---

