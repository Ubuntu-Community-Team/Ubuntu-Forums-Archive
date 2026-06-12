---
title: "Cannot reinstall gnome"
date: 2007-12-08
forum: General Help
---

### Post by zaomaster on 2007-12-08
So, I'm a tinkerer and can't leave well enough alone.  I was trying out a version of xserver-xorg from the unstable repository and it didn't work so well.  So when I tried to uninstall it and reinstall the older version I somehow deleted gnome (I have no idea how this happened).  I'm now using kde, but I don't care for it as much.  Yet, when I try and install gnome again, or ubuntu-desktop (which is also uninstalled), I get these two messages respectively:

```
sudo apt-get install gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.18.3ubuntu2) but it is not going to be installed
         Depends: gnome-office (= 1:2.18.3ubuntu2) but it is not going to be installed
E: Broken packages

```

and 

```
sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: fast-user-switch-applet but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
E: Broken packages

```

Any idea what I can do to fix this?

Oh, and I've reset my repositories so that I'm just using the standard ones.

---

### Post by -grubby on 2007-12-08
You could try:

> sudo apt-get install -f

---

### Post by zaomaster on 2007-12-08
just tried it.  but no-go, same response from apt.

anything else I can try?

---

### Post by rsambuca on 2007-12-08
It is your repos.  Post your sources.list

---

### Post by aysiu on 2007-12-08
> **rsambuca said:**
> It is your repos.  Post your sources.list
Or, just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#key) and then try ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by zaomaster on 2007-12-08
> **aysiu said:**
> Or, just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#key) and then try ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

it's working now, even as I type.

thanks!

---

### Post by zaomaster on 2007-12-08
ok, so I ran into another snag.  Doing what was said above, everything downloaded alright but then I got this message:

```
Setting up ubuntu-desktop (1.79) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
Cannot find /lib/modules/2.6.24-rc3-zen3-ubuntu-x86
update-initramfs: failed for /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
Cannot find /lib/modules/2.6.24-rc3-zen3-ubuntu-x86
update-initramfs: failed for /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
dpkg: subprocess post-installation script returned error exit status 1
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Could not regain the system lock!  (Perhaps another apt or dpkg is running?)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

I tried, at one point the zen kernel, but deleted it and it's headers using synaptic.  Did it miss something?  Did I miss something?  Running 'dpkg --configure -a' gives me this response:

```
~$ sudo dpkg --configure -a

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
Cannot find /lib/modules/2.6.24-rc3-zen3-ubuntu-x86
update-initramfs: failed for /boot/initrd.img-2.6.24-rc3-zen3-ubuntu-x86
dpkg: subprocess post-installation script returned error exit status 1

```

Anymore help?  You guys have been great so far.

EDIT:
I found documents from uninstalled kernels in my /var/lib/initramfs-tools  After deleting them everything works right.

EDIT 2:
Solved.  I'm now working in gnome 2.20!

---

