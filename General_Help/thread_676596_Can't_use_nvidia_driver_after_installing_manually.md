---
title: "Can't use nvidia driver after installing manually"
date: 2008-01-23
forum: General Help
---

### Post by coreyon on 2008-01-23
Hi guys, I had my nvidia driver working with the restricted driver manager, but it seemed slow, so I uninstalled that and installed the binary driver from nvidia's site, it worked with some minor problems. Here is where I made my mistake, I installed the driver from restricted driver manager again, and now both of them won't work, when I restart to ubuntu a message comes up saying ubuntu is running in low graphics mode or something like that, and goes into vesa mode. I know it's because I can't uninstall the driver I installed from nvidia's site, I tried uninstalling the driver from restricted driver manager, and does no good. Is there anything I can do to fix this?

Edit: Yes the xorg.conf is set to use driver nvidia.

---

### Post by Mikecore on 2008-01-23
You need to read the README file that came with the Nvidia driver you downloaded. There is a utility located at ( /usr/bin/nvidia-installer ) you can use this to uninstall the driver. 

```


sudo nvidia-installer --uninstall


```

then reinstall the restricted driver and leave it alone. ( until you learn more )

good luck

---

### Post by Lostincyberspace on 2008-01-23
try using envy to install the graphics driver.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It gives you a nice gui to use and has different versions available and options to uninstall.

---

### Post by coreyon on 2008-01-24
Thank you for the replies, I finally got the nvidia driver to uninstall thanks to that command, but now nvidia-glx-new won't uninstall, and is blocking me from installing any new drivers. 

Here is what I get from synaptic package manager:

The following packages will be REMOVED:
  nvidia-glx-new
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 19.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117538 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any more suggestions?

---

### Post by Mikecore on 2008-01-24
The new driver should be fine why do you want to remove it?

second here is some more help.

```


https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia


```

---

### Post by coreyon on 2008-01-24
The driver says it's there, but it isn't on, and it won't turn on, I think the problem is that it thinks the files are there, but they aren't anymore.

---

### Post by Mikecore on 2008-01-24
So did you look at the guide I posted and did you fix your problem.

---

