---
title: "Terminal Services?"
date: 2005-09-25
forum: General Help
---

### Post by artinla on 2005-09-25
Could someone tell me what is required to use a linux box as a terminal server?

I want to set up a master system that users could log into remotely.

Thanks,

Art

---

### Post by salsafyren on 2005-09-26
Do you want to use thin clients, look here:

[http://thinstation.sourceforge.net/wiki/index.php/ThIndex](http://thinstation.sourceforge.net/wiki/index.php/ThIndex)

If you want to use your current workstation, you can enable XDMCP, System->Administration->Login Screen Setup. You can then set your clients to use your workstation as login server. Please google for gdm and xdmcp.

/Chris

---

