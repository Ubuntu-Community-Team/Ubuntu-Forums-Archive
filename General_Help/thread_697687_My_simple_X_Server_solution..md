---
title: "My simple X Server solution."
date: 2008-02-15
forum: General Help
---

### Post by XziviT on 2008-02-15
Well i finally installed ubuntu on my computer, its incredible that nobody gave me a real answer so i was playing around with my computer and i realized that the ubuntu in my computer couldnt support the 1900x1200 screen resolution so i went back to windows and changed the resolution to 800x600, then i came back to install ubuntu and it worked! Ubuntu instaled itself with success, then i know you wont like your windows with a resolution of 800x600 so i changed it again and then i went back to ubuntu and it was working fine! The only problem is that i cant use or see the 3d desktop cube, when i try to enable the desktop efects it sais something about my NVIDIA card is not enabled and i have no idea what to do...

Note: If this dont work for you dont ask me for other solutions cuz i have no idea what to do. And if you know what can i do to enable the cube and the effects please tell me.

---

### Post by lncoll on 2008-02-15
To use the cube, call it compiz because the cube is a plugin for compiz, you need direct rendering. To get direct rendering with an nVidia VGA the best solution is installing the restricted drivers, so steep by steep:
 [LIST=1]
[*]Test if you have direct rendering. In a console type glxinfo | grep direct, the rsult of this command is self explanatory.
[*]If you have not direct rendering try to install the restricted driver. System -> Administration -> Restricted driver manager.
[*]After installing, reboot and test again for direct rendering
[*]If direct rendering, enable desktop effects, else, write with glxinfo results.
[/LIST]
I hope this can help, even with my bad english.:lolflag:

---

