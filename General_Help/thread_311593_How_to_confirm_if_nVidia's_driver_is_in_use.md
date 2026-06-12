---
title: "How to confirm if nVidia's driver is in use?"
date: 2006-12-03
forum: General Help
---

### Post by galeron on 2006-12-03
Hi,

I'm running Edgy Eft. How do I confirm that nvidia-glx driver I've installed is being used?

My nvidia-glx driver comes from tseliot's repositories. When my computer boots up, I don't see the nVidia splashscreen. Hence, I suspect that though my xorg.conf uses the nvidia driver, instead of the nv driver, the nv driver is being used instead.

Help?

---

### Post by lamego on 2006-12-03
I am not sure about NVidia, for ATI I would check like this:
> lamego@lamego-desktop:~$ glxinfo  | grep -i "vendor string"
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.
lamego@lamego-desktop:~$ 


---

### Post by Titus A Duxass on 2006-12-03
Did you run sudo nvidia-xconfig after installing nvidia-glx?

---

### Post by galeron on 2006-12-03
Hi,

Does this

```
dick@hydrogen-ubuntu:~$ glxinfo | grep -i "vendor string"
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
dick@hydrogen-ubuntu:~$ 

```

indicate that the nVidia driver is being used? I was under the impression that all it did was to detect the card manufacturer, not the video driver.

Yes, I did run a "sudo nvidia-xconfig", with no problems cropping up.

---

### Post by CatKiller on 2006-12-03
The short version I'd use is ```
glxinfo | grep render
``` and if it says **direct rendering: Yes** then you're probably using the nvidia driver.

The long version would be to check the xorg log with ```
less /var/log/Xorg.0.log
``` (Page Up/Down to scroll, Q to quit) and look for the **LoadModule: "nvidia"** line.

---

### Post by galeron on 2006-12-03
Alright, it seems that the nVidia driver is being used after all. Both methods returned positives. Yet I'm still curious why the splashscreen is not showing up. How do I check if the nVidia splashscreen is being disabled?

---

### Post by CatKiller on 2006-12-03
> **galeron said:**
> How do I check if the nVidia splashscreen is being disabled?

Look for the ```
        Option          "NoLogo"

``` line in the Device section of your xorg.conf.

EDIT: Or something like > (**) NVIDIA(0): Option "NoLogo" in your log.

---

