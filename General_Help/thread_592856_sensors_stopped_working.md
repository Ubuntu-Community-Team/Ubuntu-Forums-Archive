---
title: "sensors stopped working"
date: 2007-10-26
forum: General Help
---

### Post by Zihub on 2007-10-26
up until fairly recently my sensors-applet has been displaying temperatures of various components on my desktop. However it then stopped doing this for no apparent reason. I upgraded to Gusty since then hoping that it would solve the problem but it hasnt. I have reinstalled the applet as well as reinstalling lm-sensors but it hasnt worked. When booting it also tells me that it failed to load the sensors which it obviously wasnt doing before.

can anyone help me sort the problem?

---

### Post by dabl on 2007-10-26
When you run ```
sudo sensors-detect
``` does lm-sensors appear to work correctly in finding and characterizing the sensors?  Did you allow it to modify the module file (at the end of the script)?

---

### Post by Zihub on 2007-10-27
lm-sensors has found all my sensors and yes i did allow it to modify the file. This has solved the problem. Thanks

---

