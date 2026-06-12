---
title: "Nvidia drivers not being used?"
date: 2018-10-15
forum: General Help
---

### Post by Kymus on 2018-10-15
I just upgraded to 18.04 today from 17.10. When attempting to play *Divinity: Original Sin*, the game crashed on startup (it worked just fine yesterday). After googling, I found [this thread]("https://steamcommunity.com/app/373420/discussions/0/451848854988674764/") with some suggestions. This lead me to believe that for some reason the nvidia driver was not being used (which by all means, it should be). 

This is the terminal output I'm getting:

```
$ glxinfo | grep "OpenGL version"
OpenGL version string: 3.0 Mesa 18.0.5
```

It's my understanding that *string version* is referring to the OpenGL version and *Mesa* is the open source driver; is that incorrect? When I went in to the *Software and Updates* to check the drivers, it says that I am currently using the proprietary driver (nvidia 390). I tried switching to the other proprietary driver (nvidia 340), did $glxinfo, and I get the same output. I tried the open source driver, did glxinfo, same, went back to nvidia 390, same output.

Based on [other threads]("https://ubuntuforums.org/showthread.php?t=2319830") related to the crash I'm experiencing, it seems that this is solidly an issue of needing OpenGL 4.0 (which AFAIK the nvidia 390 driver supports). Due to this, it's peculiar that I am getting this error. 

I do have some further reason to believe that something may be screwy with my video. Earlier today (post-update) I started playing another game (FTL: Faster Than Light). About 30 minutes in or so my system completely froze and I had to manually reboot (REISUB did nothing). On the reboot, Ubuntu did not load. I got a cycle of errors saying:

```
[ OK ] Starting NVIDIA Persistence Daemon
Stopping NVIDIA Persistence Daemon
[ OK ] Starting NVIDIA Persistence Daemon
Stopping NVIDIA Persistence Daemon
[ OK ] Starting NVIDIA Persistence Daemon
Stopping NVIDIA Persistence Daemon
(etc....) 
```

A REISUB and another boot and I got in to Ubuntu fine. I don't know if these two things are related in any way, or even if my reasoning here is correct, but that's the best I have been able to come up with in my attempt to fix the problem myself.

So the bottom line here I think is: I need to be using an OpenGL 4 driver, which the latest nvidia proprietary driver should be, but it seems that's not what I'm using even when I'm being told otherwise. This seems to have happened right after updating to 18.04 today.

---

### Post by gdesilva on 2018-10-15
My understanding is that what you would need to check is not the OpenGL version but OpenGL Renderer String ie 'glxinfo | grep renderer' which should tell you whether the proprietary driver is in use or not. It should also show you 'Direct Rendering : YES' which I presume to say that the GPU is doing the processing.

---

### Post by Kymus on 2018-10-15
Thanks! I tried it and here's the output:

```
$ glxinfo | grep renderer
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: llvmpipe (LLVM 6.0, 128 bits)

```

I take this to mean that the open source drives are being used as opposed to the proprietary one that should be in use  :???: ](*,)

---

### Post by monkeybrain20122 on 2018-10-15
Did you reinstall the Nvidia driver? You said it is an upgrade from 17.10. Proprietary drivers don't survive upgrades.

---

### Post by Kymus on 2018-10-15
> **monkeybrain20122 said:**
> Did you reinstall the Nvidia driver? You said it is an upgrade from 17.10. Proprietary drivers don't survive upgrades.

Unfortunately I was not aware of this, so no. 

I looked it up and [following this guide]("https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux"), I encountered some problems:

```
$ sudo apt install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-cfg1-390 : Conflicts: libnvidia-cfg1-any
 libnvidia-decode-390 : Conflicts: libnvidia-decode
 libnvidia-decode-390:i386 : Conflicts: libnvidia-decode
 libnvidia-encode-390 : Conflicts: libnvidia-encode
 libnvidia-encode-390:i386 : Conflicts: libnvidia-encode
 libnvidia-fbc1-390 : Conflicts: libnvidia-fbc1
 libnvidia-fbc1-390:i386 : Conflicts: libnvidia-fbc1
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
                      Conflicts: libnvidia-ifr1
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
                           Conflicts: libnvidia-ifr1
 nvidia-340 : Conflicts: libnvidia-cfg1-any
              Conflicts: libnvidia-decode
              Conflicts: libnvidia-decode:i386
              Conflicts: libnvidia-encode
              Conflicts: libnvidia-encode:i386
              Conflicts: libnvidia-fbc1
              Conflicts: libnvidia-fbc1:i386
              Conflicts: libnvidia-ifr1
              Conflicts: libnvidia-ifr1:i386
              Conflicts: nvidia-dkms-kernel
              Conflicts: nvidia-dkms-kernel:i386
              Conflicts: nvidia-persistenced
              Conflicts: xorg-driver-binary
              Recommends: libcuda1-340 but it is not going to be installed
              Recommends: nvidia-opencl-icd-340 but it is not going to be installed
 nvidia-compute-utils-390 : Conflicts: nvidia-persistenced
 nvidia-dkms-390 : Conflicts: nvidia-dkms-kernel
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.77-0ubuntu0.18.04.1) but it is not going to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.77-0ubuntu0.18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

```
$ sudo apt --fix-broken install
[sudo] password for kymus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.13.0-45 linux-headers-4.13.0-45-generic linux-image-4.13.0-45-generic linux-image-extra-4.13.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 302959 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by monkeybrain20122 on 2018-10-15
Well you should remove all nvidia stuffs first. That is the problem with "upgrade" unless you have a pristine system (no third party, no ppa, no proprietary driver) you are likely to leave you with inconsistent packages.

```
sudo apt remove --purge nvidia-*

sudo apt autoremove

sudo apt update

```



Reboot and then install the Nvidia driver. How do you know it is Nvidia-340? what is your card?

---

### Post by Kymus on 2018-10-16
> **monkeybrain20122 said:**
> 

Reboot and then install the Nvidia driver. How do you know it is Nvidia-340? what is your card?


I figured 340 was necessary since (A) the choices given via the terminal output from before (*$ ubuntu-drivers devices*) as well as the choices in the *Software and Updates* menu, and also (B) I was having some issues at the time when trying to install 390 (I forget what it was, and I didn't copy and paste the terminal output specifically for that since at the time I figured it was likely unimportant), so I just went for 340 instead. I hope that answers your question.

After running the commands you suggested and rebooting, I decided to check *Software and Updates* and it claimed that the proprietary driver was still in use (nvidia 390); I didn't feel like experimenting to determine how true that was, so I then did the following as before ([based on this article]("https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux")):

```
~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:02.0/0000:06:00.0 ==
modalias : pci:v000010DEd00001287sv00003842sd00003733bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK208B [GeForce GT 730]
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

~$ sudo ubuntu-drivers autoinstall
[sudo] password for kymus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.77-0ubuntu0.18.04.1) but it is not installed
                     Recommends: libnvidia-gl-390:i386 (= 390.77-0ubuntu0.18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

Now, obviously I'm not completely savvy with this and can very well be wrong or misunderstanding something but, based on this I believe I should run the command suggested at the end because from what I can tell there are dependency issues with nvidia 390 (this is likely why I was having issues with it before, I presume).

This produces a similar problem as before:

```
~$ sudo apt --fix-broken install
[sudo] password for kymus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.13.0-45 linux-headers-4.13.0-45-generic linux-image-4.13.0-45-generic linux-image-extra-4.13.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 22 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 302959 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Regardless, I can still try 340, so here goes:

```
~$ sudo apt install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-cfg1-390 : Conflicts: libnvidia-cfg1-any
 libnvidia-decode-390 : Conflicts: libnvidia-decode
 libnvidia-decode-390:i386 : Conflicts: libnvidia-decode
 libnvidia-encode-390 : Conflicts: libnvidia-encode
 libnvidia-encode-390:i386 : Conflicts: libnvidia-encode
 libnvidia-fbc1-390 : Conflicts: libnvidia-fbc1
 libnvidia-fbc1-390:i386 : Conflicts: libnvidia-fbc1
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
                      Conflicts: libnvidia-ifr1
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
                           Conflicts: libnvidia-ifr1
 nvidia-340 : Conflicts: libnvidia-cfg1-any
              Conflicts: libnvidia-decode
              Conflicts: libnvidia-decode:i386
              Conflicts: libnvidia-encode
              Conflicts: libnvidia-encode:i386
              Conflicts: libnvidia-fbc1
              Conflicts: libnvidia-fbc1:i386
              Conflicts: libnvidia-ifr1
              Conflicts: libnvidia-ifr1:i386
              Conflicts: nvidia-dkms-kernel
              Conflicts: nvidia-dkms-kernel:i386
              Conflicts: nvidia-persistenced
              Conflicts: xorg-driver-binary
              Recommends: libcuda1-340 but it is not going to be installed
              Recommends: nvidia-opencl-icd-340 but it is not going to be installed
 nvidia-compute-utils-390 : Conflicts: nvidia-persistenced
 nvidia-dkms-390 : Conflicts: nvidia-dkms-kernel
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.77-0ubuntu0.18.04.1) but it is not going to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.77-0ubuntu0.18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

Same as before :???:

I have no idea if this is at all relevant, irrelevant, or completely obvious, but the update manager (apologies; the proper name escapes me at the moment) has been giving me an error:

> An error occured (blah blah etc. etc.). The error is: "Error: BrokenCount > 0" This usually means your installed packages have unmet dependencies

Well, we've already determined before that there are dependency issues. Though before it was giving me this specific error (ie: yesterday), it was telling me something about how i should disable third party sources or something and try running an update again (I did not do this, as I was uncertain on how to do it, exactly). 

That's all the information I think I can give.

---

### Post by monkeybrain20122 on 2018-10-17
Maybe this? [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1768050](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1768050)

I don't know, I tried installing nvidia-340 and then removed it and installed 390 in a clean 18.04 install and didn't have any issue. Never use the autoinstall command though, I always checked with Nvidia to determine the driver for my card. Maybe you should just remove all the libnvidia stuffs and start over again.

---

### Post by Kymus on 2018-10-24
> **monkeybrain20122 said:**
> Maybe this? [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1768050](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1768050)

I don't know, I tried installing nvidia-340 and then removed it and installed 390 in a clean 18.04 install and didn't have any issue. Never use the autoinstall command though, I always checked with Nvidia to determine the driver for my card. Maybe you should just remove all the libnvidia stuffs and start over again.

So, after trying this (after days of procrastinating) my PC froze up midway through an update and I couldn't get back in due to some kernel error. I knew I'd likely need to do it eventually, so I just formatted and installed 18.10. I just ran *Divinity: Original Sin* as a test to see if the drivers were working properly and it seems they are (no errors this time).

Thank you for the help!

---

