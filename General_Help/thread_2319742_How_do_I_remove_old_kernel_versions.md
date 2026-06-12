---
title: "How do I remove old kernel versions"
date: 2016-04-06
forum: General Help
---

### Post by Binabik666 on 2016-04-06
I have 2 years of old kernels taking up space
How do I remove the older versions?

---

### Post by QIII on 2016-04-06
Moved to General Help.

---

### Post by oldos2er on 2016-04-06
> **Binabik666 said:**
> I have 2 years of old kernels taking up space
How do I remove the older versions?

Uninstall them with your favorite package manager front-end.

---

### Post by montag dp on 2016-04-06
You can find installed kernels using:

```
dpkg -l linux-image*
```

Then note the package names of the older kernels that are not needed anymore, and use sudo apt-get remove {package name} to remove them.  You might also want to remove the associated linux-headers* files.  Just be sure not to remove the running kernel, as that will screw up your system.

Note: you can also search for and remove installed kernels with Synaptic if you prefer a graphical method.

---

### Post by Bucky Ball on 2016-04-06
> **montag dp said:**
> You can find installed kernels using:

```
dpkg -l linux-image*
```

Then note the package names of the older kernels that are not needed anymore, and use sudo apt-get remove {package name} to remove them.  You might also want to remove the associated linux-headers* files.  Just be sure not to remove the running kernel, as that will screw up your system.

With two years worth of kernels that may take a very long time!

I use Synaptic. Open a terminal and:

```
uname -a
```

Take note of the kernel you're using. You're going to want to keep that and the kernel before it (is a good idea). Now open Synaptic and look for 'linux-image'. You will find a heap. Click a couple of time on the 'Installed Version' column to bring the installed kernels to the top of the list. Mark them all for complete removal except for the one you're using and the one previous to that. 'Apply'.

Once that's done, open a termnal and, to get rid of remaining cruft: 

```
sudo apt-get autoremove
```

That should do it. ;)

---

### Post by Impavidus on 2016-04-07
From 14.04 on you can simply autoremove them:```
sudo apt-get autoremove --purge
```It works most of the time.

---

### Post by Binabik666 on 2016-04-07
Thanks to all who replied - I now have purged the older version Kernels

---

### Post by Bucky Ball on 2016-04-07
Great. Please mark the thread as solved (first link in my signature bottom of post) and share with us which method you employed to achieve your goal! :D

---

