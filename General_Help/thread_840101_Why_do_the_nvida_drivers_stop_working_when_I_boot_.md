---
title: "Why do the nvida drivers stop working when I boot using a different kernel?"
date: 2008-06-25
forum: General Help
---

### Post by ubnewbie2 on 2008-06-25
I have recently installed ubuntu studio audio apps (over 8.04) and this installed the realtime kernel. It is now version 2.6.24-19-rt.

When I choose the old kernel (2.6.24-19-generic) from the grub menu, xorg starts in lowres, and the proprietory nvidia drivers are not running.  I cannot get high res.

Rebooting back to the newest (realtime) kernel, it works properly, as normal, using the nvidia drivers.

I don't understand why I can't boot using whichever kernel I choose, and have it work properly.  Can I fix this somehow?

---

### Post by sdennie on 2008-06-25
Because the nvidia kernel modules only install into a single kernel if you've installed them manually.  To fix it for existing kernels, you can run the nvidia installer with -K (only compile for the running kernel).  To fix it for future kernel releases, see this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by ubnewbie2 on 2008-06-25
> **vor said:**
> Because the nvidia kernel modules only install into a single kernel if you've installed them manually.  To fix it for existing kernels, you can run the nvidia installer with -K (only compile for the running kernel).  To fix it for future kernel releases, see this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I need a little help understanding and doing this, because I didn't manually install them, they came with Ubuntu. You see, I clean installed 8.04 on this system.

I did reinstall the older kernel using synaptic, in the mistaken belief that it would then be my default kernel, but no, the realtime kernel stayed as the default. I am trying to change the system back to using the "normal" kernel by default (once I get it working again).

So, can I now manually install the nvidia kernel modules to the older kernel?  I haven't done this before, so I don't know the steps.

---

### Post by sdennie on 2008-06-25
That's quite odd.  Is it possible that you've gotten yourself into an odd package state?  Try:

```

sudo apt-get update
sudo apt-get upgrade

```

It's possible that there is a mismatch between kernels and so you are having problems with the -generic kernel.

---

### Post by ubnewbie2 on 2008-06-25
> **vor said:**
> That's quite odd.  Is it possible that you've gotten yourself into an odd package state?  Try:

```

sudo apt-get update
sudo apt-get upgrade

```

It's possible that there is a mismatch between kernels and so you are having problems with the -generic kernel.

It just reported

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So no change.

OK, so that aside, can I still add the nvidia stuff to that kernel manually?

---

### Post by ubnewbie2 on 2008-06-25
Some new info.  I rebooted and tried an even older kernel (2.6.24-18-generic) that was still sitting there.  It works fine and has nvidia drivers etc.

I must have broken -19-generic by reinstalling it from synaptic.  

So, I wonder what the next kernel update, that ubuntu releases, will see, and what it will update from/to?

---

### Post by sdennie on 2008-06-25
I'm not sure what to make of that.  If you are using the nvidia drivers from Ubuntu (the easiest way to use the drivers), they should be updating without any intervention on your part.  What is the output of:

```

find /lib/modules -name "nvidia.ko"

```

---

### Post by ubnewbie2 on 2008-06-25
> **vor said:**
> I'm not sure what to make of that.  If you are using the nvidia drivers from Ubuntu (the easiest way to use the drivers), they should be updating without any intervention on your part.  What is the output of:

```

find /lib/modules -name "nvidia.ko"

```

```
/lib/modules/2.6.24-18-generic/volatile/nvidia.ko

```

Just to be clear, it HAS been updating without intervention. This problem occurred because...

1. I wanted to step backwards from the current (realtime) kernel I had updated to
2. and possibly because I reinstalled the -19 kernel using synaptic before I tried to use it

We'll just have to see when -20 is released, what the update manager does. I suspect it'll upgrade the realtime kernel.  I wonder how to tell the system to update both, so I can choose which to run myself.

Meanwhile I can use the -18 version for non-realtime.

---

### Post by sdennie on 2008-06-25
Ok.  Before upgrading, try this:

```

sudo apt-get install linux-generic nvidia-glx-new

```

I believe that will make the system install the right modules you need to update the drivers automatically again.  Although, it's hard to say without being in your exact situation.  ;)

---

### Post by ubnewbie2 on 2008-06-25
> **vor said:**
> Ok.  Before upgrading, try this:

```

sudo apt-get install linux-generic nvidia-glx-new

```

I believe that will make the system install the right modules you need to update the drivers automatically again.  Although, it's hard to say without being in your exact situation.  ;)

nvidia-glx-new was already at the newest version.

No worries, we'll just wait and see.

Thanks for all the help.

---

### Post by Gunman1982 on 2008-06-25
I don't really know what you want with a realtime kernel. It isn't necessarily faster just because its named realtime. I think it would be too much to explain how realtime systems work but I can tell you, as long as you don't run any time critical software (management software for an atomic power plant or stuff like that) you don't need a realtime kernel.

---

### Post by sdennie on 2008-06-25
> **ubnewbie2 said:**
> nvidia-glx-new was already at the newest version.

No worries, we'll just wait and see.

Thanks for all the help.

Post back if it works without any problems.  I run nvidia but with a custom kernel and manually installed drivers.  My advice can sometimes be dubious when it comes to the "easy" way to make nvidia work.  ;)

---

### Post by ubnewbie2 on 2008-06-25
> **Gunman1982 said:**
> I don't really know what you want with a realtime kernel. It isn't necessarily faster just because its named realtime. I think it would be too much to explain how realtime systems work but I can tell you, as long as you don't run any time critical software (management software for an atomic power plant or stuff like that) you don't need a realtime kernel.

Well, when working with recording software, using programs like Ardour and jack server, they seem to use a realtime kernel to minimise latency.  I didn't choose to use it explicitly, it came as part of the Ubuntu-studio audio apps package.

I actually only want to get rid of it for normal use because, ever since it was installed, my system doesn't shut down cleanly.  There's a bug here


[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691)

that describes the problem.  I am hoping that using the "normal" kernel will restore my system to clean shutdowns again.

---

