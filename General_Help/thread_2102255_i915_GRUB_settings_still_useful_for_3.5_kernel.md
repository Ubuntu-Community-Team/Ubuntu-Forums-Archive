---
title: "i915 GRUB settings still useful for 3.5 kernel?"
date: 2013-01-06
forum: General Help
---

### Post by daKoolaid on 2013-01-06
I just installed Xubuntu Quantal into a laptop with a 2nd gen Sandy Bridge processor, Intel graphics. I was using the i915 lines in Grub but are they still necessary with the newer kernel? I don't notice any increase in heat or fan activity without them. In fact, 3.5 seems to run cooler than 3.2 did with Precise.

The Grub line I used was.
```
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 i915.powersave=1"
```

---

### Post by shuverisan on 2013-01-07
I'm not using them on my Samsung Series 5 notebook and it runs just fine. Cool and fast, the fan is rarely on and on battery it uses about 8W. I haven't tried booting with the Grub changes yet.

---

