---
title: "Nvidia issue"
date: 2012-12-01
forum: General Help
---

### Post by taunnt on 2012-12-01
OK I'm on Ubuntu 12.10 and for the life of me O can't get the damn Nvidia driver to install. What happens is it will uninstall nouveau and not install the Nvidia drivers. Is there a way to force it? My comp now just reads under display as laptop which I don't have. I have tried time after time to kill lightdm and install the driver and it get's a script err on different versions of the driver. Ny help would be great.

Thanks

---

### Post by Rebelli0us on 2012-12-02
Try installing nvidia-current in Synaptic.

---

### Post by tornadof3 on 2012-12-02
So you need to have the kernel headers installed. I don't know why this isn't mentioned often. I had major problems even this morning after the kernel upgrade.

```
sudo apt-get install kernel-headers-$(uname -r)
sudo apt-get install nvidia-current
```

should work for you.

---

### Post by taunnt on 2012-12-02
> **tornadof3 said:**
> So you need to have the kernel headers installed. I don't know why this isn't mentioned often. I had major problems even this morning after the kernel upgrade.

```
sudo apt-get install kernel-headers-$(uname -r)
sudo apt-get install nvidia-current
```

should work for you.

OK I get this:
sudo apt-get install kernel-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel-headers-3.5.0-17-generic
E: Couldn't find any package by regex 'kernel-headers-3.5.0-17-generic'

sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-current is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'nvidia-current' has no installation candidate

---

### Post by taunnt on 2012-12-03
OK still trying this  with no luck. Is there a force all install command I can try? All I need is overscan compensation to fix my monitor from being too large for the screen.

---

### Post by tornadof3 on 2012-12-03
Possibly my bad, try

```
sudo apt-get install linux-headers-$(uname -r)
```

instead of kernel-headers?? I can't quite remember the command.

---

