---
title: "Trying install st-link (support st microsystems st-link), possible error in procedure"
date: 2022-04-09
forum: General Help
---

### Post by wb0gaz on 2022-04-09
Following the procedure in (URL below) to install support for st microsystems st-link debug/programming adapter on my Ubuntu 18.04 system.

Question 1. Is this something I can install with sudo apt type command?

I would delete this post as I found the needed info, but cannot find a delete procedure, so here's an abbreviated report---

In a nutshell, 

[https://github.com/stlink-org/stlink](https://github.com/stlink-org/stlink)

contains the current project files.

For installation, there are release versions including .deb (which worked as expected.)

For documentation, directory tree contains tutorial.md, and that can be converted to pdf, which I have done and am now studying.

---> The only remaining issue is that the tool programs require I use sudo to execute.

---

### Post by ActionParsnip on 2022-04-09
How about
```

sudo apt install stlink-gui stlink-tools

```

---

### Post by wb0gaz on 2022-04-09
Thanks, ActionParsnip - I tried that, but to no avail.

$ sudo apt install stlink-gui stlink-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package stlink-gui
E: Unable to locate package stlink-tools

---

