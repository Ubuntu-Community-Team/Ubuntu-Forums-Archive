---
title: "Please Help!!! Unable to enable desktop effects!"
date: 2008-05-12
forum: General Help
---

### Post by linus_ernstsson@hotmail.c on 2008-05-12
Hi.
When I installed Ubuntu 8.04, from 7.10, my desktop effects stopped working. When I try to enable them, the error message "Desktop effects could not be enabled" appears. This is extremely frustrating, and I haven't been able to find a single person with the same problem.

I was told to Enable Restricted Drivers, but I have no options. No restricted drivers appears in the list...

On Ubuntu 7.10 all desktop effects worked just fine.
Please Help!
](*,)

---

### Post by Canis familiaris on 2008-05-12
Post the output of the following commands:
```
glxinfo | grep direct
```
```

lshw -C video
```

---

### Post by CarnivorouZ on 2008-05-12
> **linus_ernstsson@hotmail.c said:**
> This is extremely frustrating, and I haven't been able to find a single person with the same problem.
](*,)

There is a LOT of people with a similar problem if you look through past posts.  I for one can not enable effects either and have been looking for a cure also since 8.04 release day.

Anurag: Here is my output from those commands - 
```
chase@chase-linux:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
chase@chase-linux:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Radeon X1650 Pro
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 9e
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon X1650 Pro (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
chase@chase-linux:~$
```

---

### Post by sowelie on 2008-05-12
CarnivorouZ, you need to install the ATI drivers.  There are a bunch of articles around that explain how to do it.  Does it not show up in restricted drivers?  Check the /var/logs/Xorg.0.log file for errors related to the driver if you've already installed it.

---

### Post by CarnivorouZ on 2008-05-12
Sure I can install the Ati drivers again. But it will lead me to a black screen after the Ubuntu splash screen :(
I can post my xorg. or any other info anybody wants to see but if I enable the driver as I did again just now, I will get the black screen and be forced to xfix and reset my xorg in order to get past it.

---

### Post by sowelie on 2008-05-12
That's your problem, without running the ATI proprietary drivers, you can't run compiz.  When you get the black screen, hit ctrl + alt + f1 to get to a terminal.  Then, view your xorg log.

```
nano /var/logs/Xorg.0.log
```

Look for (EE) and (WW) to find out what is wrong.

---

### Post by emperor496 on 2008-05-12
I have the same problem also... while installing ATI driver on Terminal a massage apear "You need to run this installer as super-user".
what is that??

---

### Post by CarnivorouZ on 2008-05-12
When it goes to black screen after the splash screen, it is completely unresponsive.  ctrl+alr+f1 and any other combination I have tried does nothing.  Only a hard restart works.  When I restarted in recovery mode and went into shell and typed nano /var/logs/xorg.0.log it went into a window titled GNU nano 2.0.7 but it had no script and I didn't know what to type or how to look for what you described, sorry.

---

