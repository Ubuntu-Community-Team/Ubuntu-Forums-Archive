---
title: "Xorg - nvidia module and driver not matching"
date: 2006-10-28
forum: General Help
---

### Post by cmit37 on 2006-10-28
Hi,
I recently upgraded the distro from 6.06 to 6.10. Tonight not having anything better to do I came across an Ubuntu 6.10 review where the guy enabled the 3d effects so I tried to follow his instructions.

I added 2 new repositories and installed the usual compo.. etc packages. The update applet notified me of a new nvidia-glx and the associated packages(I guess they came from the new repository) and I upgraded and rebooted the computer.

The problem is that now I can not get Xorg to start. All I was getting was a black screen and an unresponsive keybord so I couldn't go to the console.

I then booted in the recovery mode. At the console I edited the sources list and removed the last 2 repositories and updated the apt database. I then uninstalled nvidia-glx and the associated Xorg packages. I then reinstalled what I assume to be the old nvidia packages. 

Upon rebooting the error I am getting when Xorg fails to start is something along the lines of the nvidia module 9(a few more numbers) does not match the 8(some more numbers) driver.

I then edited Xorg.conf and tried changing the driver from nvidia to nv, saved and rebooted. Xorg reported that it couldn't find the nv module. I also tried to use vesa as a driver and that also didn't work.

Can somebody please help me get Xorg working again?

---

### Post by cmit37 on 2006-10-29
I think that I may just have to wipe everything and install 6.10 from scratch.

---

### Post by PriceChild on 2006-10-29
Could you work from terminal and follow the guide again?

There's definately no need to reinstall.

Possible post the instructions here?

it sounds like you still have the linux-restricted-modules packages installed.

---

### Post by Mandolin-Man on 2006-11-02
yeah i am having the same problem as you but there is no need to restart in recovery mode just TRY typing control alt and f1 this will bring you onto "tty" screens this is like the same as the konsole:-D

---

### Post by closer9 on 2006-11-02
I had a problem like this... where the kernel and the nvidia drivers were mismatched.

I was told to use a script called "envy" to fix it, and it worked just fine.

Link to envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Or if you dont cant access the site (no browser)... use wget:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.5.1-0ubuntu2_all.deb
```

---

