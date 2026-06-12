---
title: "Text mode"
date: 2016-10-10
forum: General Help
---

### Post by dtree46 on 2016-10-10
Trying to install Nvidia drivers.
Says to run driver software in text mode.
How do you change from X to text mode?

dlw

---

### Post by sudodus on 2016-10-10
A simple way was was to use the boot option text. But it does not work since the introduction of systemd.

Now I think the simplest way is to boot as usual into graphics mode (if it works), and use the hotkey combination

***ctrl + alt + F1***

then you get to a text screen. But you should turn off the graphics process, and you can do that with the command line

```
sudo service lightdm stop
```

After that you can start installing the driver software.

-o-

Which version of Ubuntu are you running? And what is the model name and number of your nvidia card?

By the way, did you try the standard method to use the nvidia driver, that is recommended automatically by Ubuntu? I think it works directly from graphics mode. See this link: [BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by SeijiSensei on 2016-10-10
> **sudodus said:**
> By the way, did you try the standard method to use the nvidia driver, that is recommended automatically by Ubuntu? I think it works directly from graphics mode. See this link: [BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I usually just open a terminal and run "sudo apt-get install nvidia-current".  

Sometimes you have to select an legacy driver package for older cards, in which case I use "nvidia-NNN" instead of "nvidia-current".  You can list the available driver packages with "apt-cache search nvidia-* | grep driver".  On my 14.04 system that returns:
```

$ apt-cache search nvidia-* | grep driver

nvidia-173 - NVIDIA legacy binary driver - version 173.14.39
nvidia-304 - NVIDIA legacy binary driver - version 304.131
nvidia-304-updates - NVIDIA legacy binary driver - version 304.131
nvidia-340 - NVIDIA binary driver - version 340.96
nvidia-340-updates - NVIDIA binary driver - version 340.96
nvidia-352 - NVIDIA binary driver - version 352.63
nvidia-352-updates - NVIDIA binary driver - version 352.63

```
I have one quite old machine using 304. This one has a GTX 750 card and uses 352.

---

### Post by Bucky Ball on 2016-10-10
Or you can open Additional Drivers and install the driver from there depending on your card and what is offered. Probably easiest.

---

