---
title: "Video slow after resuming from hibernate"
date: 2007-09-06
forum: General Help
---

### Post by mfield on 2007-09-06
Hi,

I installed Feisty on a Dell Vostro 1400 with an Nvidia graphics card.  I am running the nvidia (proprietary) driver.  Standard hibernate does not work (I get a message that it cannot unload the nvidia module, and based on what I have read elsewhere, this is a bug in the hibernate script).  However, s2disk will hibernate the system just fine.  I have modified my xorg.conf and acpi-support files as described at [https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend).  The system resumes from hibernation just fine also...with one problem:  The video is very slow.  For example, when opening a program, you can see the window draw from the top of the screen to the bottom (or vice versa) -- it does not appear all at once as it normally would.  Does anyone have any ideas as to what might be causing this?  Has anyone else seen this problem?

Thanks,
Marc

---

