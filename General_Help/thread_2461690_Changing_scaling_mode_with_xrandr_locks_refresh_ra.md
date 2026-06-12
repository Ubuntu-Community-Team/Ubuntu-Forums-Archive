---
title: "Changing scaling mode with xrandr locks refresh rate to 60hz"
date: 2021-05-05
forum: General Help
---

### Post by 95pcat on 2021-05-05
I have a 1080p 144hz monitor and I wanted to switch to 1024x768 without stretching, but setting the scaling mode with xrandr to anything other than none locks the refresh rate to 60hz. Ubuntu display settings still reports the monitor at 144hz and I tried to use xrandr --refresh to force 144hz but it's still obviously at 60hz by the choppier mouse movement and the monitor itself is reporting it's at 60hz. Even using 1920x1080 with the scaling mode change will lock it to 60hz. Setting the scaling mode back to none will let the monitor start working at 144hz again. I have an R7 370 on Ubuntu 20.04.2 and I've tried with both the Radeon and AMDGPU driver. Am I doing something wrong or is this just a bug?

---

