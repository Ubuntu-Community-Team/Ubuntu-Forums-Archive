---
title: "Losing DISPLAY on new tab"
date: 2014-09-08
forum: General Help
---

### Post by ramicio on 2014-09-08
i have Xming on my Windows machine serve my X stuff from my headless Ubuntu server. I log into the server from multiple locations. Only my Windows machine has the X serving going on. It seems when I start logging in from other machines (that aren't running X serving) that new tabs (Byobu) start telling me that it can't initialize the display. DISPLAY isn't being set on new tabs. Even if I go create new a new tab on my Windows machine, it still gives me the error. Is there a way to specify persistently what the DISPLAY variable is from boot, and regardless of who/what creates new tabs? What should I even set this variable to?

---

