---
title: "Nvidia"
date: 2007-02-13
forum: General Help
---

### Post by koulanji on 2007-02-13
I recently purchased an nvidia graphics card. What do i do after i've reconfigured xorg to regain my gdm?

---

### Post by MCSE_Crossover on 2007-02-13
Did you already install the nVidia graphics drivers?

If not, you will need to enable the restricted repositories and run:

***"sudo aptitude install nvidia-glx nvida-kernel-common"***

This will install the main nVidia drivers on your system. Afterwards, run:

***"sudo nvidia-xconfig"*** and this should take care of your Xorg configuration. Just reboot or execute a CTRL+ALT+BACKSPACE to restart gnome.

If you are still having issues with the drivers after performing the above steps, check your xorg.conf and ensure that it specifies "nvidia" instead of "nv" for your driver.

That file is located at /etc/X11/xorg.conf

Hope that helps.

I usually test that everything is working properly by giving one of my OpenGL screensavers a test run. :)

---

### Post by r4ik on 2007-02-13
Or run Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by koulanji on 2007-02-13
Thanks. it's exactly what im trying to install now, but unfortunately ubuntu fails to resolve the archives, sooo im in pretty much of a quandary

---

### Post by MCSE_Crossover on 2007-02-13
Check these two links:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")

Have you done both?

---

### Post by koulanji on 2007-02-13
editing my sources list does not help me any, since i do not have a gdm :) I am basically in text mode

---

### Post by MCSE_Crossover on 2007-02-13
It will still help. You edit the source list, then perform an "apt-get update" to update your respositories. Then, from there you can perform the above mentioned commands to install and configure your nVidia drivers.

Your gonna have to use "Vi" instead though or some other terminal editor.

How come your gdm isn't working? Because you added that card? Have you tried doing a "sudo dpkg-reconfigure-xorg" ?

That will graphically walk you through a reconfig of your xserver from the command line...

---

### Post by koulanji on 2007-02-13
When I enter the command for the sources list i get "cannot find display" I guess I lose

---

### Post by MCSE_Crossover on 2007-02-13
> **koulanji said:**
> When I enter the command for the sources list i get "cannot find display" I guess I lose

type "sudo dpkg-reconfigure xserver-xorg"

See if that works.

---

### Post by koulanji on 2007-02-13
works

thanks

---

### Post by MCSE_Crossover on 2007-02-13
Excellent! Glad to hear it!

---

