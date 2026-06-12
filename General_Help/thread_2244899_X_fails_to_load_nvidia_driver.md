---
title: "X fails to load nvidia driver"
date: 2014-09-19
forum: General Help
---

### Post by emunson2 on 2014-09-19
I started my machine today and X was refusing to come up saying that the nvidia driver was missing.  So I reinstalled nvidia-331 from aptitude.  I have my desktop back and lsmod shows the nvidia driver loaded, but my Xorg.0.log says it is using th nouveau driver.  I am not sure how to get back to the nvidia one.

lsmod output:
```
nvidia              10675249  0 
```

Xorg.0.log
```
[     8.984] (==) Assigned the driver to the xf86ConfigLayout
[     8.984] (II) LoadModule: "nvidia"
[     8.984] (WW) Warning, couldn't open module nvidia
[     8.984] (II) UnloadModule: "nvidia"
[     8.984] (II) Unloading nvidia
[     8.984] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     8.984] (II) LoadModule: "nouveau"
```

---

### Post by gifford on 2014-09-19
Try opening software and updates, go to additional drivers and activate the appropriate nvidia-331 driver.

---

### Post by emunson2 on 2014-09-19
These nvidia packcages are installed:
```

emunson@bert:~ $ dpkg --get-selections | grep -v deinstall | grep nvidia
nvidia-331                                      install
nvidia-libopencl1-331                           install
nvidia-opencl-icd-331                           install
nvidia-settings                                 install
```

And I already used the driver selection tool to pick the nvidia-331 drivers and rebooted.  That tool shows the nvidia drivers as active.

---

### Post by emunson2 on 2014-09-19
I found the problem, update-alternatives --config x86_64-linux-gnu_gl_conf is pointing to /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf.  If I select the apropriate one from /usr/lib/nvidia-331/ld.so.conf and then log out and back in, almost everything is fine*.  However, this does not seem to persist across a reboot.

* Desktop renders faster and my second monitor works, however, I cannot start Steam

---

