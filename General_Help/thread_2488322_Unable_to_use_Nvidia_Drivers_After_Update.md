---
title: "Unable to use Nvidia Drivers After Update"
date: 2023-07-01
forum: General Help
---

### Post by scpatl4now on 2023-07-01
I ran updates this morning on Ubuntu 22.04 and it had a bunch of kernel updates.  After it rebooted it ended up at the black screen with the small blinking curser on the upper left corner.  This happens from time to time (more frequently lately) and removing the Nvidia drivers at the recovery copnsole usually does the trick and I just reinstall the drivers when I log in.  This time, when I reboot after installing the Nvidia driver, I am back to the blinking curser.  Updates should not break my system.  I dont know what to do at this point as I am using the Nouveau driver and need the nvidia one.  I tried to install the 535 driver.

---

### Post by oldfred on 2023-07-01
How are you installing nVidia driver?
If you install from Ubuntu repository, kernel updates should automatically use driver.
If you installed directly from nVidia, then you have to manually reinstall with every kernel update.

---

### Post by scpatl4now on 2023-07-01
I had the Nvidia 535 driver installed from additional drivers.  Todays update installed kernel 6.01 OEM  (I don't know what an OEM kernel is and why I was asked to install it) and now I get the blank screen with cursor prior to the login screen.  I can go into recovery console and purge the nvidia drivers, which lets me reboot and log in, but I cannot install the nvidia driver from additional drivers as when I reboot I'm back at the blank screen

---

### Post by scpatl4now on 2023-07-01
In recovery console I was able to use startx and resume to log on, but my nvidia profile was empty and resolution was not right.

---

### Post by scpatl4now on 2023-07-01
Ok, I was able to fix this, but I am not sure which did it.  First I ran this command from the Nvidia forums

> sudo apt install linux-headers-$(uname -r)
 which did install an update
then 
> dkms status


after that, I uninstalled Virtualbox since it seems to be causing problems.  I installed the 535 driver from additional drivers and I'm good now

---

