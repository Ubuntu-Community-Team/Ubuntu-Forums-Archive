---
title: "PC Does not Come Back from Suspend. - 22.04"
date: 2023-11-20
forum: General Help
---

### Post by jt252 on 2023-11-20
My PC does not come back from suspend, I would have to reboot in order to get back in. I have a Dell OptiPlex 7060 running Ubuntu 22.04

---

### Post by MAFoElffen on 2023-11-20
Waking from sleep problems have to do with two things, the Graphics driver, and how far the CPU is allowed to go down into the sleep state.

Do this first:
```

sudo lshw -C video

``` 
to ensure it is using a graphics driver and not running as "Unclaimed".

Next do
```

sudoedit /etc/default/grub

```
Add this boot parameter
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash intel.max_cstate=4"

```
Save and Exit
```

sudo update-grub
sudo reboot

```
Pick up the changes, reboot and test.

---

### Post by portalan on 2023-11-21
I have the same issue. Adding the steps above made no difference.

---

### Post by MAFoElffen on 2023-11-21
> **portalan said:**
> I have the same issue. Adding the steps above made no difference.
Welcome. 

Please start your own thread so that you can get personal attention. In the first post, please describe the CPU and graphics GPU, the release version you are running and which kernel version.

---

