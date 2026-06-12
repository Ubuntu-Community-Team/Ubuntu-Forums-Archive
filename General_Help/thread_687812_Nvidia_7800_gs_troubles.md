---
title: "Nvidia 7800 gs troubles"
date: 2008-02-04
forum: General Help
---

### Post by Schnare on 2008-02-04
I recently installed a Geforce 7800 GS and reinstalled ubuntu.
The restricted drivers won't work for it and neither will the drivers I installed through envy.
I have currently uninstalled the envy drivers but am at a loss with what I should do next
Any help would be appreciated.

---

### Post by pdub on 2008-02-04
Can you get to text mode login?

ctrt+alt+F1

Then login and see if the nvidia module is loaded.
```

lsmod | grep nvidia
```

if the module is loaded, please post the result.

If there is no module loaded then try.

```
sudo modprobe nvidia
```

If the module loads then try to start the gdm.

```
sudo /etc/init.d/gdm restart
```

---

### Post by Schnare on 2008-02-06
This is what i get

nvidia               4713780  0 
i2c_core               22784  3 i2c_ec,nvidia,i2c_viapro
agpgart                35400  2 nvidia,amd64_agp

---

### Post by pdub on 2008-02-06
So it appears tha the nvidia driver is loading. I assume you xorg.conf is set to use the nvidia driver.

```
    Driver         "nvidia"
```


Try installing the drivers from the nvidia site, then make sure you have disabled the NVidia restricted modules.

```
sudo nano /etc/default/linux-restricted-modules-common
```

**DISABLED_MODULES="nvidia nvidia_legacy" **


Then delete the following file if it exists.

```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```

---

### Post by Schnare on 2008-02-06
it won't let me open the drivers
it says that gedit can't detect any character coding

---

### Post by pdub on 2008-02-07
Follow the installation instructions on the nvidia site.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

