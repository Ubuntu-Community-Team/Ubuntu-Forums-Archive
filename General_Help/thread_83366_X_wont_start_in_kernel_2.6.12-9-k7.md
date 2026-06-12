---
title: "X wont start in kernel 2.6.12-9-k7"
date: 2005-10-28
forum: General Help
---

### Post by tHub on 2005-10-28
Full log: [http://www.eazyshare.com/user_uploads/Xorg.0.log.txt](http://www.eazyshare.com/user_uploads/Xorg.0.log.txt)
error part:
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
```
thats some stuff i think that could be related to the issue
```
th@ubuntu:~$ dpkg -l | grep nvidia
ii  nvidia-glx                            1.0.7667-0ubuntu25                 NVI DIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                  1.0.7667+1                         NVI DIA binary kernel module common files
ii  nvidia-settings                       1.0-3ubuntu6                       Too l of configuring the NVIDIA graphics driv
th@ubuntu:~$ dpkg -l | grep linux-headers
ii  linux-headers-2.6.12-9                2.6.12-9.23                        Hea der files related to Linux kernel version
ii  linux-headers-2.6.12-9-386            2.6.12-9.23                        Lin ux kernel headers 2.6.12 on 386
ii  linux-headers-2.6.12-9-k7             2.6.12-9.23                        Lin ux kernel headers 2.6.12 on AMD K7
th@ubuntu:~$ dpkg -l | grep restricted
ii  linux-restricted-modules-2.6.12-9-386 2.6.12.4-11                        Non -free Linux 2.6.12 modules on 386
ii  linux-restricted-modules-2.6.12-9-k7  2.6.12.4-11                        Non -free Linux 2.6.12 modules on AMD K7
ii  linux-restricted-modules-386          2.6.12.16                          Res tricted Linux modules on 386.
ii  linux-restricted-modules-common       2.6.12.4-11                        Non -free Linux 2.6.12 modules helper script
ii  linux-restricted-modules-k7           2.6.12.16                          Res tricted Linux modules on AMD K7.
```
I don't know why it isnt in the log but it was also saying that the NVIDIA kernel version was different from X server.
Everything is working perfectly in the 386 kernel

---

### Post by invalid on 2005-10-28
Make sure you have nvidia-kernel-common installed

Cb

Edit: Nevermind this post, I missed that in your printout.. sorry

---

### Post by Kyral on 2005-10-28
When you jump kernels (or heck even recompile the one you are using) you are going to have to either A) Recompile the NVidia Module if you are using the Official NVidia Driver package from NVidia.com or B) Reinstall NVidia-GLX (Might do it I don't know ;P)

---

### Post by tHub on 2005-10-28
[QUOTE=Kyral]When you jump kernels (or heck even recompile the one you are using) you are going to have to either A) Recompile the NVidia Module if you are using the Official NVidia Driver package from NVidia.com or B) Reinstall NVidia-GLX (Might do it I don't know ;P)[/QUOTE]
i've reinstalled nvidia-glx, nothing happened

---

### Post by tHub on 2005-10-29
bump

---

### Post by milstead on 2005-11-09
I had the same problem. Try:

sudo apt-get install linux-restricted-modules-2.6.12-9-k7

You need the nvidia module compiled for the k7.
I would consider this a bug. Surely apt should know that this is a dependency if both a k7 kernel and nvidia-glx are installed together on the same computer? Is there somewhere I should report it?

Timie Milie

---

### Post by tHub on 2005-11-13
ic, i dont know what i did to get it to work, maybe thats what i installed
not sure where you can report it

---

