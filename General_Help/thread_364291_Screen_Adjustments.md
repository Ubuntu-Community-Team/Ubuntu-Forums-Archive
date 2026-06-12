---
title: "Screen Adjustments"
date: 2007-02-18
forum: General Help
---

### Post by KewL on 2007-02-18
Hey guys, I run the latest version of ubuntu. Anyway, my screen is to far to the left and it cuts out some of it. How can I adjust the screen position? I have a nvidia 7600gs 512mb (PCI-e), with the drivers installed, but I don't see anything about adjusting the screen in the settings.

---

### Post by dexter on 2007-02-18
What kind of screen do you have? If it's a CRT (not a flat one), you should be able to adjust the screen position using the buttons on the screen.

---

### Post by xopher on 2007-02-18
Yeah, Id try adjusting with the screen buttons first too.

Run nvidia-settings (in a terminal): ```
nvidia-settings
```

Make sure the resolution is correct. Not sure if this app had the ability to change the screen position too, I wouldn't count on that though.

Oh, for nvidia-settings to work (to actually be there), you need to have nvidia-glx (the 3D-capable nvidia driver) installed.

---

### Post by KewL on 2007-02-18
Dexter - I tried the buttons, it moved the black around everything. Its the ubuntu os thats hanging off.  In windows theres a adjustments tab in the nvidia settings with arrows to move it.

xofer -  pretty sure i installed it right, used this guide. Method 1
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

[IMG]http://img157.imageshack.us/img157/2084/screenshotnvidiaxserverrp3.png[/IMG]

---

