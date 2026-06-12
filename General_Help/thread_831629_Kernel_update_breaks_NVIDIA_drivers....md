---
title: "Kernel update breaks NVIDIA drivers..."
date: 2008-06-17
forum: General Help
---

### Post by MJBoa on 2008-06-17
So I really love Ubuntu but this is frustrating me to no end, an ubuntu update completely breaking the system really shouldn't happen.
I just installed the latest kernel packages but now when I boot to the new kernel, the nvidia driver doesnt seem to work at all. It starts ubuntu then goes to the screen where it shows what it's doing at Running Local Boot Scripts. The screen flashes on and off then says something about low graphics mode then the screen shuts off and the computer doesn't respond at all. I tried Ctrl+Alt+F1 but it still turns off no matter what.
Now the same thing seems to be happening to the old kernel too. I tried recovery mode and installed the newest version of the driver but it didn't change anything.
What can I do? I don't want to lose everything I had set up...

---

### Post by jespdj on 2008-06-17
How did you install the nVidia driver? Did you install it the Ubuntu way (with the restricted drivers manager) or did you install it yourself, or with an unofficial script such as Envy?

I'm using the official Ubuntu version of the nVidia driver and don't have any problems.

Did you try reinstalling the driver?

---

### Post by cocopuffz on 2008-06-17
Yeah, I think you pretty much have to reinstall everytime the new kernel updates occur if you've got the drivers directly from the Nvidia site, unless the new Nvidia drivers are in the repos now? I don't think they are... then if you've got any other thing like Virtual box(not ose), you're gonna have to repair that too hehe. Sa'll part of the fun right?

I'm not gonna update my Kernel until the weekend when I have some time to mess around with it.

I'm not sure what you can do if you can't even get to a command line. That happened to me a while back, but I was able to use recovery mode then just reinstall the nvidia drivers after exiting X...

---

### Post by MJBoa on 2008-06-17
I used the latest NVIDIA drivers from their site. And I mean that's fine about reinstalling but notice what I said, the computer eventually stops responding or at least showing any kind of response. So what do I do?

---

### Post by kpkeerthi on 2008-06-17
> **MJBoa said:**
> I used the latest NVIDIA drivers from their site. And I mean that's fine about reinstalling but notice what I said, the computer eventually stops responding or at least showing any kind of response. So what do I do?

Boot with the "Recovery Mode" (make sure the latest kernel line is selected) from GRUB and reinstall the drivers.

---

### Post by MJBoa on 2008-06-17
Like I said in the post, I already tried that. I had added nv to /etc/default/linux-restricted-modules-common and removed that from there. I wonder but maybe it had something to do with removing the linux-restricted-modules package? I figured it didn't matter since I used NVIDIA's driver.

---

### Post by mvavrik on 2008-06-18
I'm having the exact same issue.  I also tried booting into recovery mode, dropping to root, and installing the nvidia drivers (64-bit).  I'm being told that there is no "kernel interface" and one cannot be compiled. Here is the output from the nvidia driver installer. 

[I]No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;this means that the installer will need to compile a kernel interface for your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.[/I]


I installed the libc development package and attempted to reinstall the Nvidia drivers and still no success.

---

