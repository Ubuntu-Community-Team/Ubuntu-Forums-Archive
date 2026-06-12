---
title: "Azureus: How to install plugins?"
date: 2007-06-01
forum: General Help
---

### Post by wie6Ein0 on 2007-06-01
How can I install plugins for Azureus under Ubuntu Linux? In Windows, there was a way to view list within program and automatically download and install plugins, but under linux, I'm lost! Please help!

---

### Post by steeleyuk on 2007-06-01
Copy your plugins to /home/<username>/.azureus/plugins

Then, within Azureus click Tools > Options > Plugins > Scan for New Plugins

---

### Post by doogy2004 on 2007-06-01
You should be able to install them the exact same way that you would in windows.  Azureus is a Java application it is the exact same code and interface on all OSs.

---

### Post by P3r3s on 2007-06-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/84396](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/84396) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **doogy2004 said:**
> You should be able to install them the exact same way that you would in windows.  Azureus is a Java application it is the exact same code and interface on all OSs.

No it isn't. The Ubuntu package is patched to not allow the instalation of plugins (don't ask me why?!?!:confused:).


> **steeleyuk said:**
> Copy your plugins to /home/<username>/.azureus/plugins

Then, within Azureus click Tools > Options > Plugins > Scan for New Plugins

Unfortunately this work-around doesn't work for all plugins, like SafePeer. :( 

I'll try to repack azureus in order to work the original way.

---

### Post by jasonwert on 2007-06-07
> **steeleyuk said:**
> Copy your plugins to /home/<username>/.azureus/plugins

Then, within Azureus click Tools > Options > Plugins > Scan for New Plugins

I used this method to install SafePeer and it worked like a charm for me, thanks!

---

