---
title: "Problem installing package manually"
date: 2017-01-20
forum: General Help
---

### Post by peter1897 on 2017-01-20
I am trying to install [xfdashboard ]("http://goodies.xfce.org/projects/applications/xfdashboard/start")on Xubuntu 14.04. I downloaded the tarball file, extracted it and run ./configure. It gave me error message that intltool is too old. I run 'apt-get install intltool' and that seems to fix the problem because when i run ./configure again i didn't get this error message, but i get another error message: configure: error: X Window system libraries and header files are required

What does it mean and how to fix it?

---

### Post by olduse78802 on 2017-01-20
Try this 

[https://ubuntuforums.org/showthread.php?t=883303](https://ubuntuforums.org/showthread.php?t=883303)

---

### Post by peter1897 on 2017-01-20
I run this command 'sudo apt-get install xserver-xorg-dev' and after that i run ./configure but i get even more errors:
```
Package xcomposite was not found in the pkg-config search path.
Perhaps you should add the directory containing `xcomposite.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xcomposite' found
checking whether to build with X11 extension XDamage... yes
Package xdamage was not found in the pkg-config search path.
Perhaps you should add the directory containing `xdamage.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xdamage' found
checking whether to build with X11 extension Xinerama... yes
Package xinerama was not found in the pkg-config search path.
Perhaps you should add the directory containing `xinerama.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xinerama' found
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libwnck-3.0 >= 3.0... not found
*** The required package libwnck-3.0 was not found on your system.
*** Please install libwnck-3.0 (atleast version 3.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.


```

---

### Post by ajgreeny on 2017-01-20
> **olduse78802 said:**
> Try this 

[https://ubuntuforums.org/showthread.php?t=883303](https://ubuntuforums.org/showthread.php?t=883303)
That info is now 8 years old and unlikely to be very useful.

I have looked for a ppa repository that might help but there does not seem to be one for 14.04, though there is for 16.04.
[https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras)
Xubuntu 14.04 will lose support in April this year, so now might be the moment to move to 16.04 if xfdashboard is important to you.

---

### Post by peter1897 on 2017-01-20
What if i move to 16.4 and some software stop working because it doesn't have support for 16.04?

---

### Post by ajgreeny on 2017-01-20
There is no way to answer that as we have no idea what software you use.

You will have to move from Xubuntu 14.04 in April anyway as there will be no further updates to it, so now would be a good time to investigate the use of that software in 16.04.
I have found that all software I used in 14.04 still works fine in 16.04, though everything I have is from the repos or a few PPAs.
I can not comment on any applications that are not ubuntu-repository (including PPAs) packages.

---

### Post by Dennis N on 2017-01-20
I would install 16.04 in a dual boot setup, leaving 14.04 in place for now, still usable in case of emergency (not likely to be needed). Then you can install this xfdashboard from the PPA, and you will also be free to start using 16.04 as your new OS. Copy your personal files over to the newer version.

---

