---
title: "Ubuntu 12.04 does not completely boot after boot"
date: 2013-02-13
forum: General Help
---

### Post by shujaansari on 2013-02-13
Two days ago Ubuntu update manager offered some update, I updated  without even looking at the updates, the computer indicates that it needs a restart as soon as i restart it it boots normally then i see my desktop but it hangs i can move the mouse but the launcher does not appear nor does the top panel, when i try to open the terminal nothing happen i restart my pc then enter through failsafe graphic mode 


Any suggestion 
i am using dell i3 laptop

help!!

---

### Post by hawthornso23 on 2013-02-14
My first guess would be that you probably had a kernel update that broke your graphics drivers. There is a graphics kernel module that needs to be reinstalled whenever the kernel gets updated. If it doesn't get reinstalled for some reason the kernel upgrade will break your graphics. Try reinstalling your graphics drivers.

---

