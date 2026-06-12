---
title: "Need help uninstalling nvidia drivers,Also driver doesnt show under details"
date: 2014-01-28
forum: General Help
---

### Post by RiotsHere on 2014-01-28
Here are all the stupid drivers I have
 ```

rc  nvidia-304                               304.116-0ubuntu0.0.1                    NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-319                               319.32-0ubuntu0.0.1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                            1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-modprobe                          319.37-0ubuntu1                         Load the NVIDIA kernel driver and create device files
ii  nvidia-settings                          331.20-0ubuntu0.0.1                     Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319                      319.32-0ubuntu0.0.1                     Tool for configuring the NVIDIA graphics driver

```

I really don't know how to fix any of this. I installed one thinking that it worked then went on installing opencl. Opencl did not work because I don't think the driver is even in use because no drivers are showing under my graphic settings under details. So I then installed other drivers thinking it didn't work then I got this in my terminal telling me I had all of these lol. I only want 319 can't seem to get this working and on a side note purge doesnt work.

---

### Post by RiotsHere on 2014-01-28
Ok now under details/graphics it says:  Driver GeForce 8600 GTS/PCIe/SSE2 
Does this mean it has a driver in use o.0

---

### Post by deadflowr on 2014-01-28
You have the 319 driver, the rest are the needed packages to run it, with the added setting-management program.
The 304 driver isn't installed, so don't worry about it.
You probably only need to generate an xorg.conf file.
try running this from a terminal
```
sudo nvidia-xconfig
```

then do a reboot.

---

### Post by RiotsHere on 2014-01-28
How will I know if it worked?

---

### Post by deadflowr on 2014-01-28
You can see if the nvidia driver is the driver running by doing
```
sudo lshw -c display | grep driver
```
if nvidia is the driver listed, then the nvidia driver(in this case the 319 driver) is in use.

How well it is being used, I don't know.

---

### Post by RiotsHere on 2014-01-28
I'm getting no driver listed just this:  configuration: driver=nvidia latency=0

---

### Post by deadflowr on 2014-01-28
> **RiotsHere said:**
> I'm getting no driver listed just this:  configuration: driver=nvidia latency=0

** driver=nvidia** 

It running the nvidia driver.
Though it doesn't say which.
I know you can determine which by running the unity support script
```
/usr/lib/nux/unity_support_test -p
```
it should list the driver in use in the line
OpenGL version string:
There are probably other ways...

---

### Post by RiotsHere on 2014-01-28
ok it is running. Sorry about that. It was looking like it didn't work thanks for the help!

---

