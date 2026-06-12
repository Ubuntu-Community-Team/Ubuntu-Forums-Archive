---
title: "Can't get NVIDIA drivers to work in 13.10 (NVidia GeForece 7200 GS)"
date: 2014-02-19
forum: General Help
---

### Post by chris.ribal2 on 2014-02-19
Hi,

          I'm trying to get ubuntu 13.10 working on a desktop with a  nvidia 7200gs. First i've tried to install the official drivers from the  nvidia website, which didn't work - the installer aborted on creating  the kernel modules.
  Googling around i've found the x-edgers ppa to install the drivers  from. According to the docs i've installed the matching drivers for my  card:
  ```
# sudo apt-get install nvidia-304 nvidia-304-settings
```
  After rebooting the x server doesn't start, but there are no fatal  error messages in the x log. Listing the loaded modules doesn't include  any nvidia module. **BUT**: if i manually load nvidia-304 module instead of nvidia everything works fine - i can start lightdm and even login:
  ```
# lsmod | grep nvidia
# modprobe nvidia-304
# lsmod | grep nvidia
    nvidia         xxxxxxxxxx 0
# service lightdm start
```
  What to do here to have the appropriate module started on boot?

Thanks in advance
Chris

---

### Post by squakie on 2014-02-19
If I'm following you correctly, what you want is for the module nvidia-304 to be loaded automatically at boot, correct?  In other words, make this permanent.

There is a file in the /etc folder called "modules" that tells the kernel the additional modules you want loaded.  You need to add to this file:

-open a terminal window via ctrl/alt/F1
- login with your normal userid/password (the password is not echoed to the screen)
- type:
cd /etc
sudo cp modules modules_original
sudo gedit modules
- scroll to the very bottom of the file, press "enter" and add the following line:
nvidia-304
- click the "Save" button
- exit the editor
- exit the terminal
-reboot

The module should be loaded automatically now.

---

### Post by monkeybrain20122 on 2014-02-20
You should have run in the terminal
```
sudo nvidia-xconfig
```

..then reboot.

---

### Post by squakie on 2014-02-21
> **monkeybrain20122 said:**
> You should have run in the terminal
```
sudo nvidia-xconfig
```

..then reboot.

I don't use nVidia, so I didn't know this.  I'll remember that for the next time a question comes up like this.

Thanks!

---

