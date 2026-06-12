---
title: "NVidia and Intel and 3 monitors"
date: 2015-11-10
forum: General Help
---

### Post by gingaz on 2015-11-10
Hi,

NVidia + Intel do not work together spitting out [drmSetMaster failed: Invalid argument]("http://askubuntu.com/questions/613021/nvidia-xorg-crashes-on-15-04-drmsetmaster-failed-invalid-argument") error on session login:

```
[     3.660] (II) intel(G0): [DRI2] Setup complete
[     3.660] (II) intel(G0): [DRI2]   DRI driver: i965
[     3.660] (II) intel(G0): [DRI2]   VDPAU driver: i965
[     3.660] (II) intel(G0): direct rendering: DRI2 enabled
[     3.660] (II) intel(G0): hardware support for Present enabled   
[     3.660] (EE) modeset(G1): drmSetMaster failed: Invalid argument
[     3.660] (EE) 
Fatal server error:
[     3.660] (EE) AddScreen/ScreenInit failed for gpu driver 1 -1
<snip>
[     3.661] (EE) Server terminated with error (1). Closing log file.
```


Has anyone come up with the solution for this? I have tried fedora 23 and ubuntu. None of the configurations work. 

Thanks,
Gin

---

