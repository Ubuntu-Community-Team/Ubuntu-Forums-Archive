---
title: "Intel Graphics Issue"
date: 2016-02-01
forum: General Help
---

### Post by karan-kalyani786 on 2016-02-01
Hi Guys, This is Karan.
I'm running on Ubuntu 15.10 Willy Werewolf, ASRock H81 PRO BTC Mobo, Intel Pentium G3258 4th Generation Haswell Processor that claims to bundle 4th Gen. Intel Extreme Graphics. I'm dual booting Ubuntu 15.10 with Windows 10 both on separate HDDs. I'm playing graphics intensive games on Windows and I've installed Intel Graphics from Intel's own website leading to Intel Graphics Installer for Linux. 
After taking much time, the app displayed success message and asked a reboot. I did reboot and initial boot screen display was at about 640x480 resolution and then switched back to original 1024x768 resolution during boot and logged in as usually. I didn't noticed anything different from Ubuntu without Intel Graphics and/or with Intel Graphics.
Next I ran, VMWare Workstation 12 and Installed Windows 8.1 x86 guest OS in it. I enabled 3D Support in settings but when I booted the VM, it displayed and error message that No 3D Support is available from Host OS... Did I did anything wrong installing graphics driver ??

---

### Post by Nuno_Abreu on 2016-02-01
Intel drivers don't need to be installed usually. Did the computer work well without them? Probably it did better.

---

### Post by grahammechanical on 2016-02-01
Are you asking about an Intel graphics problem or a virtual machine problem?

> initial boot screen display was at about 640x480 resolution and then switched back to original 1024x768 resolution during boot

The motherboard has its own limited video settings and that is what is used during the initial part of the boot process. Then as the OS is loaded the video driver is activated. And that is what is happening. It is not an indication of a problem. It is just the way things work. Which you might not have noticed before.

Linux usually has Intel drivers as standard. So, we do not usually need to install an Intel video driver like we do with Nvidia & AMD. So, I am not surprised that after installing an Intel driver from the web site that you did not notice any improvement. You have actually been using Intel graphic drivers from the first re-start after the installation of Ubuntu was finished.

As regards the VM problem, I have little experience of this but you might need to install something called guest extensions, or something like that, to get 3D in a guest OS in a VM. I cannot be sure. But I do think that this problem is related to the installation of an Intel graphic driver.

Regards.

P.S. It is Guest Additions

> While the virtual graphics card which VirtualBox emulates             for any guest operating system provides all the basic features,             the custom video drivers that are installed with the Guest             Additions provide you with extra high and non-standard video modes             as well as accelerated video performance.

[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

---

### Post by karan-kalyani786 on 2016-02-02
> **Nuno_Abreu said:**
> Intel drivers don't need to be installed usually. Did the computer work well without them? Probably it did better.

Can't say anything on this, because I haven't noticed any noticeable difference in computing/graphics performance of PC. But the performance in guest OS i.e. Windows 8.1 is sluggish, as if i'm using windows basic display driver on either nvidia or amd card. I'm using VMware Workstation not Oracel VM Virtualbox..

---

### Post by karan-kalyani786 on 2016-02-02
> **grahammechanical said:**
> Are you asking about an Intel graphics problem or a virtual machine problem?



The motherboard has its own limited video settings and that is what is used during the initial part of the boot process. Then as the OS is loaded the video driver is activated. And that is what is happening. It is not an indication of a problem. It is just the way things work. Which you might not have noticed before.

Linux usually has Intel drivers as standard. So, we do not usually need to install an Intel video driver like we do with Nvidia & AMD. So, I am not surprised that after installing an Intel driver from the web site that you did not notice any improvement. You have actually been using Intel graphic drivers from the first re-start after the installation of Ubuntu was finished.

As regards the VM problem, I have little experience of this but you might need to install something called guest extensions, or something like that, to get 3D in a guest OS in a VM. I cannot be sure. But I do think that this problem is related to the installation of an Intel graphic driver.

Regards.

P.S. It is Guest Additions



[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

Sir, that 640x480 resolution switching problem was with Ubuntu itself not the VM. I've already installed VMware tools that act as additional drivers in guest os installed on VMware Workstation.. I'm attaching a screen shot of this issue.. 

[ATTACH=CONFIG]267071[/ATTACH]

---

