---
title: "udev rules and livecd"
date: 2006-11-10
forum: General Help
---

### Post by bleucanard on 2006-11-10
I noticed one thing on the live cd :

When booting from the downloaded live cd:
if I add a udev rule by copying it to udev/rules.d
(for a device our company makes),
udevtest tells me that it will run the rule exactly as 
I expect. However, when I plug the device, the rule is not seen/run.

If I remaster the cd (using the great program reconstructor) 
and preinstall the rule and boot the cd, it 
works fine.

Is that because of the way the live cd mounts the filesystem (udevtest sees the rule, but udev daemon doesn't ?)

(This is just out of curiosity, it is working now that I preinstall the 
root on the remastered cd)

Pierre

---

