---
title: "gksu not working correctly"
date: 2007-05-17
forum: General Help
---

### Post by fearpi on 2007-05-17
Lately, when I run Synaptic from the menu, it prompts me for my password, and after I enter it, there is no trace of synaptic. pstree shows that gksu and synaptic are still running. If I run "sudo synaptic" from the terminal, everything works fine.

---

### Post by aysiu on 2007-05-17
Try pasting these commands into the terminal: ```
sudo killall gksu
sudo killall synaptic
gksudo synaptic
``` If you get any errors, post them back here.

And don't use *sudo synaptic*--read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

