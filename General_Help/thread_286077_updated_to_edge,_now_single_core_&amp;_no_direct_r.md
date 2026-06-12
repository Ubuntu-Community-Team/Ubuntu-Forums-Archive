---
title: "updated to edge, now single core &amp; no direct rendering"
date: 2006-10-27
forum: General Help
---

### Post by mega on 2006-10-27
I just updated to edgy

now I have a single core cpu, and direct rendering wont work

mega@mainpc:~$ uname -a
Linux mainpc 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux


mega@mainpc:~$ lsmod | grep nvidia
nvidia               4713396  32 
i2c_core               22288  2 i2c_ec,nvidia
agpgart                33456  2 nvidia,intel_agp


glxinfo..
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4


anyone have any ideas?

---

### Post by chudder on 2006-10-27
By now do you have "a single core" do you mean you had a duo core?  If so and you want to get ubuntu to read both processors you need to get SMP (686 I think) through synaptic.  This stands for Symmetric Multi-Processing.  Does this answer one of your questions?  I don't know about rendering.  Sorry

---

### Post by mega on 2006-10-27
I have a core duo, it was working fine with the smp kernel

now it wont work, and the nvidia drivers are not working properly

so far that's the only thing I've found edgy broke

---

### Post by WakkiTabakki on 2006-10-27
Install the 2.6.17-10-generic to get the proper kernel, and the nvidia driver (and the restricted modules ofcourse)

/N

---

### Post by mega on 2006-10-27
mega@mainpc:/etc/X11$ sudo apt-get install 2.6.17-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.17-10-generic


what is the package name?

---

### Post by ejket on 2006-10-27
```
sudo apt-cache search linux-image-2.6.17
```

---

### Post by mega on 2006-10-27
it says it's installed

---

### Post by jocko on 2006-10-27
There is a metapackage named "linux-generic". If you install that, it will make sure you always have the newest "linux-image-generic" and "linux-restricted-modules-generic" packages installed (these are also metapackages).

---

### Post by mega on 2006-10-27
something's not right

mega@mainpc:~$ sudo apt-get install linux-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
mega@mainpc:~$ uname -a
Linux mainpc 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

---

### Post by hotani on 2006-10-27
You are [not alone](http://www.ubuntuforums.org/showthread.php?t=285272).

---

### Post by jocko on 2006-10-27
Looks like you probably have both kernels installed. Have you checked which kernels are listed in '/boot/grub/menu.lst'? If both are listed, just reboot, hit 'Esc' when grub is loading and you get a boot menu where you can choose which kernel to boot. If the -generic kernel works, then just remove the -386 kernel through synaptic.

---

### Post by mega on 2006-10-27
I found generic in grub

but my machine wont even boot with that kernel, it says somethign about detecting the 2 cpu's and hangs until I reset it


this is wonderful

please tell me there will be a proper i686 smp kernel again?

---

### Post by ejket on 2006-10-27
Is it really there?

```
ls /boot/vmlinuz*
/boot/vmlinuz-2.6.17-10-generic
```

Are you actually booting it?  Check /boot/grub/menu.lst to make sure you are.

edit:
Oops, I see there are other problems that are not so easily addressed ... you have to post fast around here I see :eek:

---

### Post by hotani on 2006-10-27
mega: post your hardware here or in the [other thread on this topic](http://www.ubuntuforums.org/showthread.php?t=285272) so we can see if we're all dealing with the same issue.

I'm suspecting it has something to do with the nvidia drivers and/or something in fstab not playing nice with the generic kernel. Either way, it blows - and I have the option of A. booting with 1 core (cpu is a 3800+ X2 dual core) and virtually no GPU acceleration (glxgears uses 100% CPU), or B. Not booting at all. Attempting to load the generic core from the grub menu results in no bootsplash and a hung system.

---

### Post by mega on 2006-10-27
mega@mainpc:~$ ls /boot/vmlinuz*
/boot/vmlinuz-2.6.15-18-386  /boot/vmlinuz-2.6.15-23-686
/boot/vmlinuz-2.6.15-19-386  /boot/vmlinuz-2.6.15-25-386
/boot/vmlinuz-2.6.15-19-686  /boot/vmlinuz-2.6.15-25-686
/boot/vmlinuz-2.6.15-20-386  /boot/vmlinuz-2.6.15-26-386
/boot/vmlinuz-2.6.15-20-686  /boot/vmlinuz-2.6.15-26-686
/boot/vmlinuz-2.6.15-21-386  /boot/vmlinuz-2.6.15-27-386
/boot/vmlinuz-2.6.15-21-686  /boot/vmlinuz-2.6.15-27-686
/boot/vmlinuz-2.6.15-22-386  /boot/vmlinuz-2.6.17-10-386
/boot/vmlinuz-2.6.15-22-686  /boot/vmlinuz-2.6.17-10-generic
/boot/vmlinuz-2.6.15-23-386

it's there, it boots and errors with this 
error
[IMG]http://freddy.geekopolis.com/gallery2/d/4818-2/DSC_1164.JPG[/IMG]

---

