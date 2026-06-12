---
title: "Ubuntu 18.04.3: My monitor suddenly went low resolution"
date: 2020-01-18
forum: General Help
---

### Post by Dedalo on 2020-01-18
I don't know what has happened. I have a gtx 1060. I have installed the drivers weeks ago, everything was working fine. Today I restarted the computer, and suddenly I have low resolution on my display, which was configured to 1080.

---

### Post by Autodave on 2020-01-18
What drivers did you install and where did you get them from?

Have you checked cables to make sure that they are inserted fully?  What cables and adapters are you using to connect the monitor to the PC?

---

### Post by Dedalo on 2020-01-18
I am using the power cable, and an hdmi cable. I've downloaded the drivers from the nvida webpage. I had just reinstalled them, and now I recovered the proper resolution. I don't really know what happened, I had installed other stuff to do CUDA, but it was weeks ago, and everything worked fine until today. However, after reinstalled the drivers, everything came back to normality.

---

### Post by Autodave on 2020-01-18
You should never use the drivers from nVidia's web site.  You should only install them from from the Linux repositories.  When installed like you did, every time there is an update, your driver will not update since it was installed from the website.  If it had been installed from the repositories, *then *it would be updated automatically.

You need to purge the driver that you are now using and reinstall from the repositories.

---

### Post by Dedalo on 2020-01-18
> **Autodave said:**
> You should never use the drivers from nVidia's web site.  You should only install them from from the Linux repositories.  When installed like you did, every time there is an update, your driver will not update since it was installed from the website.  If it had been installed from the repositories, *then *it would be updated automatically.

You need to purge the driver that you are now using and reinstall from the repositories.

How do I do that? the drivers from the repository are the same than the one on the nvidia webpage?

BTW, I would also like to monitor my multicore cpu temperature (per core temperature), how can I do it?

---

### Post by CelticWarrior on 2020-01-19
Yes, the drivers in the repository are exactly the same version.

The main difference is they were packaged and tested for Ubuntu and, because of that and as already commented, they are rebuild for any kernel update, something that you already found out doesn't happen if using the Nvidia binaries.

---

### Post by Dedalo on 2020-01-20
Ok. Thanks. When I first installed ubuntu, I had video, but when I watched a video on youtube, the frames were not right, it was something with the drivers, because after I've installed Nvidia drivers, it started to work properly. Would you tell me how should I do to install the drivers form the repository?

Thanks a lot.

---

### Post by NM5TF on 2020-01-20
> **Dedalo said:**
> How do I do that? the drivers from the repository are the same than the one on the nvidia webpage?

[COLOR="#FF0000"]BTW, I would also like to monitor my multicore cpu temperature (per core temperature), how can I do it?[/COLOR]

there are 2 ways to monitor CPU temperatures, depending on how you want to display them...

to have then show in a terminal, type

```
sudo apt install lm-sensors
```

and then type

```
sudo sensors-detect
```

you will see a lot of questions, but it is almost always safe to just answer yes to all...let it run until it finishes

then type

```
sensor -f
```

it will look something like this if using Fahrenheit...[COLOR="#FF0000"]to show Celsius just leave off the -f[/COLOR]

```
[tommy@tommy ~]$ sensors -f
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +156.2°F  
Core0 Temp:  +152.6°F  
Core1 Temp:  +150.8°F  
Core1 Temp:  +150.8°F  

acpitz-acpi-0
Adapter: ACPI interface
temp1:       +123.8°F  (crit = +203.0°F)
```

you could also use Psensor

```
sudo apt install psensor
```

it should now be in your menu...you can show them in a menu, or have them show on your panel...
directions are here  [https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/](https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/)

tommy

---

### Post by Dedalo on 2020-01-30
How do I do to install the nvidia drivers from the repository?

BTW, if you have a link that says how to install CUDA, that will be of great help too.

Thanks!

---

### Post by CelticWarrior on 2020-01-31
Open Additional Drivers, select the recommended version and apply. That would have been all you had to do if you didn't install the Nvidia binaries. But because you did now you should first remove everything you installed from the Nvidia run file. In a nutshell, just run the same command as you did before to install but now with an additional parameter: --uninstall . You can use this [https://askubuntu.com/a/220734](https://askubuntu.com/a/220734) for reference, replace the file name to reflect the one you used and, of course, you do need that file again to uninstall.

Cuda is also in the repos:

```
sudo apt install libcuda1-XXX #Replace XXX with the major version you end up installing via Additional Drivers
```


At this point I hope you have understood that installing Nvidia drivers (and CUDA support) *comme il faut* for Ubuntu is much easier than the generic method with the downloaded Nvidia installer, safer (specifically tested in Ubuntu) and doesn't require reinstallation whenever there's a kernel update.

---

