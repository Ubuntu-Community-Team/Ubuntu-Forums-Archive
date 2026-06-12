---
title: "Screen Tearing GeForce 7300 GS"
date: 2016-02-03
forum: General Help
---

### Post by xp15 on 2016-02-03
Im using this card with the priority driver, and somehow it works great with the LiveCD and after the installation without updating.
but after installing updates, dragging a window or square select (if it pretty big) looks teared. I can play videos anyway.

---

### Post by grahammechanical on 2016-02-03
When you ran the live session did you install a proprietary video driver? If you did not then you were not using the live session with a proprietary video driver. By default the live session uses the open source video driver which for Nvidia adapters is call Nouveau.

When we install and tick the box "Install third party software" we get some proprietary audio & video codecs and a proprietary video driver installed as well. You can try going to System Settings>Software & Updates>Additional Drivers tab and select another video driver. The system needs to be connected to the internet & you need to allow the utility time to do its job and you should be offered Nouveau and 4 Nvidia drivers one of which will already be activated.

Regards

---

