---
title: "nvidia driver conflict"
date: 2006-10-14
forum: General Help
---

### Post by jolt256 on 2006-10-14
Like a fool, I installed Nvidia's official Linux driver, then tried uninstalling it and installing nvidia-glx from dapper and (after much breakage) eventually went back to the nvidia official driver. Long story short, the system works - except that at each boot I must do this before the X server will start:
```
sudo modprobe -r nvidia
sudo modprobe nvidia
```

For some reason, the module loader is finding the (older) kernel module from dapper and loading that instead of the nvidia module, but it finds the proper version when I modprobe manually. I renamed /lib/linux-restricted-modules/2.6.15-27/nvidia to nvidia.disabled, but that doesn't seem to have solved the problem. What can I do to get it to find the right module on bootup, other than sticking some kludge script in /etc/init.d?

edit: I tried using envy. It complains that my graphics card (7900GS) is not supported by the driver.

---

