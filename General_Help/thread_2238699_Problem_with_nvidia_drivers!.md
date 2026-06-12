---
title: "Problem with nvidia drivers!"
date: 2014-08-09
forum: General Help
---

### Post by Mengsk91 on 2014-08-09
Well, here's the thing. I was running 12.04 flawlessly until, yesterday (8/8/2014) something about support appeared and just messed up my OS. I decided to switch to 14.04.
After a fresh install, Ubuntu runs very slow. As recommended, I've checked if additional drivers. Having a nvida GeForce 5200 128 MB, a legacy drivers was available. After activating them and rebooting, the "running on low graphic mode" appears.
I really don't know what to do. Help would be really appreciated.

---

### Post by mooreted on 2014-08-09
Open a terminal and enter:

sudo nvidia-xconfig

It will create an xorg.config file that may get the driver working.

You can also try nvidia-settings from a terminal and see if it shows you are running the driver.

---

### Post by grahammechanical on 2014-08-09
You might get better results using the open source video driver called Nouveau. But is your graphic adapter capable of running 14.04 with Unity. I ask because I think that a graphic adapter with only 128 MB of its own memory is close to the minimum required.

```
/usr/lib/nux/unity_support_test -p
```

With 12.04 if the graphic adapter was not capable of running Unity 3D then Ubuntu was installed with Unity 2D. In 14.04 if the graphic adapter is not capable of running Unity 3D and its need for hardware accelerated graphics then a version of the open source video driver called llvmpipe is used as fall back. It tries to give the user Unity 3D but even on capable graphic cards it does seem slow.

This may have been your problem all along. System Settings details will tell you if you are running under llvmpipe.

Regards.

---

### Post by mooreted on 2014-08-09
That's true, you might try Gnome Fallback (Metacity), xfce or Lxde.

---

### Post by Mengsk91 on 2014-08-09
Thanks both of you for your advices!

> **grahammechanical said:**
> But is your graphic adapter capable of running 14.04 with Unity. I ask because I think that a graphic adapter with only 128 MB of its own memory is close to the minimum required.

Indeed! I came upon that afterwards. Having read that, I've decided to check why my Precise failed in the first place.

Apparently, the problem had to do with hardware enablement stacks (HWE). Burning an up-to-date disc of Precise seems to solve the issue.

---

### Post by mooreted on 2014-08-09
> **Mengsk91 said:**
> Thanks both of you for your advices!



Indeed! I came upon that afterwards. Having read that, I've decided to check why my Precise failed in the first place.

Apparently, the problem had to do with hardware enablement stacks (HWE). Burning an up-to-date disc of Precise seems to solve the issue.

Excellent, glad you figured it out.

---

