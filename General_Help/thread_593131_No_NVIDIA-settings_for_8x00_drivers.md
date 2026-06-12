---
title: "No NVIDIA-settings for 8x00 drivers?"
date: 2007-10-26
forum: General Help
---

### Post by cwestpha on 2007-10-26
Is there any way to force AA or filtering with the new drivers under 7.10? Whenever you try to install the control utility it wants to un-install the nvidia drivers for the 8x00 series cards. The jaggies are starting to drive me nuts in all 3D apps.

---

### Post by FuturePilot on 2007-10-26
Press Alt+F2 and type in 
```
nvidia-settings
```
They come with the driver. I'm not sure why that separate package is still in the repos
Then go through the sections and check off anything that says SyncToVblank. That will get rid of the tearing.

---

