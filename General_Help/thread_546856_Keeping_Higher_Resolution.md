---
title: "Keeping Higher Resolution"
date: 2007-09-09
forum: General Help
---

### Post by SailRacer on 2007-09-09
I've got Ubuntu running nicely on my laptop. I have an NVidia Tools program that I can use to set my resolution to 1440x900 which is perfect for this machine. Every time I reboot, it reverts to 1024x768. Going to the system menu, and selecting screen resolution will not give me the 1440 option, unless I've already set it up with the NVidia program.

The NVidia Tools program also gives me the option to save that setting to xorg.conf, and I've done that... repeatedly, but it still boots back in 1024x768. I've even made the change in NVidia Tools, gone to the Screen Resolution thing, and (since 1440x900 now shows up there) set it as default. Still reboots to 1024x768.

Any thoughts?

---

### Post by Phurious on 2007-09-09
Try running the nvidia settings tool from a terminal using the following command:

```
sudo nvidia-settings
```

Once you have adjusted the resolution to your desired setting, make sure you "Save to X Configuration File".

---

### Post by SailRacer on 2007-09-09
Worked! Thanks!

---

