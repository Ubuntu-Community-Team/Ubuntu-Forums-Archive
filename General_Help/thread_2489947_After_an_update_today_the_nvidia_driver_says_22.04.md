---
title: "After an update today the nvidia driver says 22.04 is running X server"
date: 2023-08-15
forum: General Help
---

### Post by foxsquirrel on 2023-08-15
This is related to the other post I made this morning regarding the recent update that the broke the machine.

Trying to reinstall the driver and it claims that 22.04 is running X server and it will not install....

Even during log in it shows Ubuntu selected and not X 

Shows that wayland is running.

```
fred@eng-dev2:~$ pstree | grep wayland
        |-gdm3-+-gdm-session-wor-+-gdm-wayland-ses-+-gnome-session-b---2*[{gnome-session-b}]
        |      |                 |                 `-2*[{gdm-wayland-ses}]
fred@eng-dev2:~$ 

```

---

### Post by MAFoElffen on 2023-08-15
You seem to be installing the nVidia binary Linux driver straight from nVidia... Not an nvidia-driver-XXX from the Ubuntu repo.

So even thought the error say "X", it really means that the script checks if there is a graphics engine running (either Wayland or Xorg X11) and you need to exit out of it to install. Their script only runs from Console. The instructions I wrote for it over 12 years ago in my Graphics Resolution Sticky are still relevant, and explain that clearly.

So, from there, it you "log out", where it returns to your Graphical Login panel (GDM, LightDM or SDDM), then press <Cntrl><Alt><F4> and log in with your credentials, then you could run that script.

Question is, why are you installing the Linux binary driver, which is generic in nature, instead of one of Ubuntu's packaged drivers, which have been tested to run on Ubuntu? I  know, you like to live on the edge right?

---

### Post by foxsquirrel on 2023-08-16
> **MAFoElffen said:**
> You seem to be installing the nVidia binary Linux driver straight from nVidia... Not an nvidia-driver-XXX from the Ubuntu repo.

I  know, you like to live on the edge right?

Not really......

I got too trusting of the ubuntu updates, have not had any problems until now. Sadly enough both are critical workstations, I should have known better. Had plenty of blue screens from updates back in the early days of DOS then windows.

Did not touch anything, ubuntu updated, rebooted and it broke. So if that was running on ubuntu drivers from the start ubuntu broke my system. First machine it was assumed the card died, next the second machine same issue. Now, running both on the Intel onboard graphics card just fine. One is okay without gpu its a yocto build machine the other box does need the graphics card. Do you know of a gpu that is going to work with 22.04?

Logged in and changed to X and the Nvidia driver would install but asked about changing from ubuntu drivers to Nvidia. Declined and stopped.

The yocto build box is doing much better, without the RTX a2000. Stuff would stutter and could not get focus of a window without multiple clicks. Now with all 16 cores running 100% the intel onboard graphics is doing better than the A2000 did.

---

