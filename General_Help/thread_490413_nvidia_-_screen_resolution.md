---
title: "nvidia - screen resolution"
date: 2007-07-02
forum: General Help
---

### Post by jvels on 2007-07-02
Hi

I use ubuntu 7.04 on my laptop with nvidia geforce go 7600.

As root i run: sudo nvidia-settings

When I try to "Save X config file" I get this error:


```

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: GeForce Go 7600)!

ERROR: Failed to add display device 'Seiko' to screen 0!

ERROR: Failed to add X screen 0 to X config.

ERROR: Failed to add X screens to X config.

ERROR: Failed to generate an X config file!

```

I have tryed to add this code in my x11org.conf file but I do not help :-(
```
Option         "DynamicTwinView" "false"
```

Any ideas how i solve this problem?

Best Regrads
Jesper Vels

---

