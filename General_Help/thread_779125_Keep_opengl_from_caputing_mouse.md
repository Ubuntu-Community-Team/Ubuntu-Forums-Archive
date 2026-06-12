---
title: "Keep opengl from caputing mouse"
date: 2008-05-02
forum: General Help
---

### Post by soxs on 2008-05-02
I got around a xorg.conf option named Option          "AllowDeactivateGrabs"  "1" in the Section "ServerFlags".
It works pretty fine from jumping between fullscreen and winowed mode via <ALT><RETURN>.
But the opngl app keeps the cursor captured so it renders this option quite useless.
Does a xorg.conf option exist which enables freeing the cursor from the pending opengl app or is the only way to do this properly to run the opengl app in its own xserver?

Edit: -.- damn, may some admin plaese fix the title, it wa supposed to be *capturing*

---

