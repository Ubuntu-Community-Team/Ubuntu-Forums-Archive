---
title: "[SOLVED] low graphics mode after kernel update?"
date: 2008-05-29
forum: General Help
---

### Post by jessika-kaos on 2008-05-29
I restarted my computer after the update to the 2.6.24-17 kernel and am stuck in low graphic mode. It worked fine just after the update several days ago, but now it will only boot into the proper resolution if i choose the old kernel in grub.

I haven't changed anything on my system since the update, and it *was* working fine.

I am using an Nvidia 7600 GT and the restricted modules package is installed.

---

### Post by jessika-kaos on 2008-05-29
Also, running "configure" from the low graphics mode error message, and selecting my hardware and driver causes no change. When I look under the Hardware Drivers menu, the nvidia driver is not even listed.

---

### Post by danwood76 on 2008-05-29
Try changing the driver to the nv driver in the xorg.conf, that should work with your graphics card.

Install the nvidia drivers manually from the nvidia site should solve your issue.

---

### Post by jessika-kaos on 2008-05-29
I thought maybe my drivers needed to be updated, but since everything worked OK after rebooting the first time I dismissed the idea. 

Now, I am unable to install the Nvidia drivers from the website without stopping X, but whenever I try sudo /etc/init.d/gdm stop it appears to work, but the installer warns me that X is still running. I guess it automatically restarts each time. How do I prevent that? I tried installing the driver from the recovery console, but I got a warning that I had to be in runlevel 3.

---

### Post by PmDematagoda on 2008-05-29
You will have to kill Xorg after stopping GDM, kill X with:-
```
sudo killall Xorg
```

---

### Post by jessika-kaos on 2008-05-29
Well, the divers are installed and the hardware manager says they are in use, but I am still stuck in low graphics mode. I tried using the exact xorg.conf I was using previously, and that didn't work. I will keep playing around with it.

---

### Post by danwood76 on 2008-05-29
Have you tried configuring with:
```

sudo nvidia-config

```

---

### Post by Zorael on 2008-05-29
If your nvidia driver is reinstalled properly - which they have to be upon kernel upgrades unless you use the nvidia-glx* packages, in which case it'll do so by itself - it should work provided it's defined to be used in xorg.conf.

> **danwood76 said:**
> Have you tried configuring with:
```

sudo nvidia-config

```
I think that's [FONT="Courier New"]nvidia-**_x_**config[/FONT]. :>

Make it the following to add random tweaks (I use).
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

---

### Post by jessika-kaos on 2008-05-29
Well, if I use sudo dpkg-reconfigure -phigh xserver-xorg, my resolution is somewhat better, but the nvidia driver is not used (plust I have two monitors). If I enable the nvidia driver in the hardware manager and reboot, I boot into low graphics mode. If I run nvidia-xconfig to change the drivers in xorg.conf to nvidia, and restart, I boot into low graphics mode.

I am now running at 800x600, and the hardware manager swears that the nvidia driver is in use, but when I run nvidia-settings, I get an error message telling me that I am not using the nvida driver (which I am) and to run nvidia-xconfig (which i did).

I will try running nvidia-xconfig with Zorael's tweaks now and report back. Thanks!

*EDIT: No luck, still cant get out of low graphics mode.*

---

### Post by jessika-kaos on 2008-05-29
> If your nvidia driver is reinstalled properly - which they have to be upon kernel upgrades unless you use the nvidia-glx* packages, in which case it'll do so by itself - it should work provided it's defined to be used in xorg.conf.

Yeah, like I said, it worked after the first reboot (which the system told me was needed after the update). Then two days later I restarted and this happened. In the interim I installed nothing and made no changes to settings except played with some different settings in the sound menu to see whether ALSA or PulsAudio made a difference in wav file playback. That obviously has nothing to do with X or graphics.

---

### Post by jessika-kaos on 2008-05-29
I have uninstalled the linux-restricted-modules and linux-restricted-modules-common packages, and blacklisted nv and nvidia-new. I thought maybe they were interfering with the nvidia driver from the website. I then reinstalled that driver. Still no change.

When the PC boots, and just before x starts, the screen flickers several times. I saw this mentioned in a couple of other posts, but none of the resolutions have worked for me. I *really* don't want to reinstall the OS. What could prevent the system from utilizing the nvidia driver? I guess I don't know enough about what I'm trying to fix.

lsmod | grep nvidia returns nothing. any ideas?

---

### Post by danwood76 on 2008-05-29
Well if you blacklist the module in modprobe it will not load.

Un blacklist it and get back to where you were in low graphics mode and then have a look in the xorg logs for errors and warnings:
```

cat /var/log/Xorg.0.log | grep '(EE)'
cat /var/log/Xorg.0.log | grep '(WW)'
cat /var/log/Xorg.0.log.old | grep '(EE)'
cat /var/log/Xorg.0.log.old | grep '(WW)'

```

---

### Post by jessika-kaos on 2008-05-29
I de-blacklisted a few tries ago. I have checked my logs and don't see anything that sticks out.

[my xorg.0.log for instance.]("http://pastebin.com/m1becf239")

---

### Post by danwood76 on 2008-05-29
If you had run those commands you would have found something.

> 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


Its obvious that you arent installing the driver correctly, or one of the libs it uses is broken.
Do you get any errors wehn doing:
```

sudo modprobe nvidia-new

```

---

### Post by jessika-kaos on 2008-05-29
that last command produces no output. right now I have the nvidia-glx-new driver installed, and have uninstalled the one I got from nvidia's website. I don't know whether it installed correctly or not - but it said that it had completed installation.

I don't know if this makes any sense:

sonne@HIVE:~$ sudo modprobe -l | grep nvidia*
/lib/modules/2.6.24-17-generic/volatile/nvidia.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/video/nvidia/nvidiafb.ko

---

### Post by jessika-kaos on 2008-05-29
Fixed the problem, but I'm not sure how. I started with another plain xorg.conf and re-added the lines from my old xorg.conf back section by section. 

Running: "diff /etc/X11/xorg.conf /etc/X11/xorg.conf.backup12" shows that they are exactly the same, yet this one works.

Thanks to all who tried to help, I still don't know what caused it to fail in the first place.

---

