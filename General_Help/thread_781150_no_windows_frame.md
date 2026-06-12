---
title: "no windows frame"
date: 2008-05-04
forum: General Help
---

### Post by Khuezy on 2008-05-04
Compiz fails to load and I don't see the frame of the windows, no minimize, max, or close

thanks.

---

### Post by KaliVoid on 2008-05-04
if you using nVidia video card then add this to 
your xorg.conf in Section "Device" :
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

backup the file before changing it .

---

### Post by MrFSL on 2008-05-04
run compiz from a terminal and post the output.

---

