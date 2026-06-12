---
title: "[SOLVED] NVidia Kernel Driverless"
date: 2007-02-24
forum: General Help
---

### Post by Zeotronic on 2007-02-24
Recently I figured out how to fix a problem to get my NVidia GeForce 5600 card to work, but before I could fix this problem I got another problem. Every time I try to run it's command in Terminal:
```
sudo nvidia-glx-config enable
```
I always get the following error:
> Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.
Now, I have some general idea as to what this means, but no idea on how to fix it, also I never ran into this error originally.

---

### Post by DagMan on 2007-02-24
I've had that package not work for me too.  Before it was added to the software repositories, we all used to follow this guy's guide form this site and it worked great.  You will want to follow method 2
[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)
getting your driver from here
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I have a Geforce 5500 and the 8776 driver has worked for me on both Ubuntu and Gentoo.  Maybe yours requires a newer one.  These are from the 32 bit driver section [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

