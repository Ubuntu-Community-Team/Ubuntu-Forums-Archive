---
title: "Can't awake from Suspend with Firewire. Anywhere I can look to solve this?"
date: 2023-04-13
forum: General Help
---

### Post by 777funk on 2023-04-13
For some reason the computer is pretty temperamental about suspending if anything firewire has been connected (audio in my case). 

Is there any common place to look to fix this?

---

### Post by TheFu on 2023-04-16
You can probably power off the interface as part of the suspend task and power it back up as part of the coming out of suspend.  I had to do this with a USB network adapter a few years ago. It is so long ago that I don't remember the details. I just needed to look through dmesg to see the device powered on at boot to learn the device file to be used. Think it was a little on/off script that I put into /etc/ somewhere.

---

