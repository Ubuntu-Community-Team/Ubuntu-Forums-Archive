---
title: "[Given up due to hardware change] 13.04 slow"
date: 2013-09-06
forum: General Help
---

### Post by julien-dal-col on 2013-09-06
Hello everyone,

I just installed 13.04 (32bits) on a (very) old machine. I didn't check the minimal requirements, but I thought it would be OK... The result is so bad (extremely slow UI) that I don't know whether this is due to the hardware or a config problem.
Here is what I did.

The machine is:
MB: Asus P4P800 (intel 865PE chipset)
CPU: pentium 4 HT (32bits) 3.0GHz
RAM: 3GB DDR 400 (PC-3200)
HDD: RAID0, 2x 80GB sATA2 (2x 8GB of swap space + around 145GB, formatted as ext4, before install, 130GB after)
Note: I used the 13.04 Server install disk to setup the RAID0 array
GPU: ATI radeon 9200SE, AGP 8x, 128MB DDR, DirectX 8.1

I am not sure the GPU is recognized correctly since it says: "R200 (RV280 5961) x86/MMX/SSE2 TCL DRI2" in system settings->details

After installing ubuntu-desktop and login into the system I could only see the wallpaper. No sidebar, no taskbar...
I thus installed compizconfig-settings-manager [FONT=verdana]and enabled the ubuntu unity plugin as recommended here : [/FONT]http://askubuntu.com/questions/285779/after-upgrading-to-13-04-unity-interface-is-not-showing
This brought back the normal desktop...

Is there anything I could do to have a usable system? Disable some graphic effects maybe. I need a desktop, but a very basic one would be enough...

I am surprised since this machine runs WinXP like a charm...

Maybe the problem does not come from the outdated GPU... Any ideas?

Thank you very much in advance for your help.
Best,
-a-


EDIT:
I don't know if this is related but the Software Updater keeps on appearing in the sidebar with a blue (not white) arrowhead on its left. When I click on it it says the software is up to date... ???

---

### Post by Paulgirardin on 2013-09-06
I have recently seen some installs using Unity on older machines run very slow.
In both cases I installed xubuntu-desktop and that gave a huge improvement in performance.
gnome shell also runs better on low power systems.Search gnome in the software center.
Both can be installed from the software center.

---

### Post by julien-dal-col on 2013-09-06
I tried LXDE... It's a bit better...
I ran the system testing thing and the graphic test failed...
There must be something I should do about my GPU I guess...

---

### Post by mörgæs on 2013-09-07
Could you please post the results from the test?

---

### Post by grahammechanical on 2013-09-07
An AGP graphic card is indeed a very old technology. Dispite it being called Acelerated Graphic Port and 128MB memory will make the modern user interface run slow. So, the machine runs XP fine. It will run Ubuntu 10.04 fine as well but not 13.04. In my opinion a person would need 4 x the video memory that you have in order to get close to a good user experience with Ubuntu Unity on 13.04.

The reason it seems that the graphic card is not recognised correctly is that it is running the Nouveau open source video driver. RV280 5961 is the manufacturer's code name for that graphic card and it is what is shown in the details page when we run Nouveau. My Details page says Gallium 0.4 on NVA5.  Gallium = Nouveau and NVA5 = manufacturer's code name for Nvidia GT210/GT220.

You may also be running a subset of Nouveau called llvmpipe. It is used as fall-back for low specification hardware. Its purpose to give the user a Unity 3D desktop even if the hardware does not support 3D desktops. There is a noticable difference even on hardware that is better specified if we fall-back to llvmpipe. Which is what happens if we select Recovery Mode>Resume.

So, I would say the problem most definitely comes from outdated hardware or running a distribution that has advanced beyond the hardware.

Regards.

---

### Post by 3rdalbum on 2013-09-07
Grahammechanical's advice is usually good, but this time it's a bit off.

The main issue with your graphics card is that it is no longer supported by its own manufacturer, and there's no longer a high-quality driver for it on Ubuntu. There is an open-source reverse-engineered driver ("radeon") which is already in use, unfortunately the Unity desktop in 13.04 requires 3D acceleration and the capabilities of that driver are not sufficient to give you decent 3D performance. That's why the Unity desktop is slow on your system.

Using llvmpipe will probably not improve things. It'll shift the load from the GPU to the CPU, but that's not abundantly powerful either.

You're not using Nouveau, that's for Nvidia cards and from the numbers you posted that's definitely an ATI. The fact that you actually have anything displayed on your screen confirms that Ubuntu has correctly detected the card as an ATI.

There's a few solutions for your problem:

1. Use Ubuntu 12.04 instead of 13.04. There actually haven't been many changes between 12.04 and 13.04, but one of the major differences was that 12.04 was the last version of Ubuntu to come with the "Unity 2D" desktop, perfect for just your situation. It should run acceptably fast.
2. Turn down the graphical bling of the Unity desktop in 13.04; this will change Unity's performance from "unusably slow" to "usable but slow": [http://www.ubuntuvibes.com/2012/10/make-unity-more-responsive-in-ubuntu.html](http://www.ubuntuvibes.com/2012/10/make-unity-more-responsive-in-ubuntu.html)
3. Use a different desktop environment. It looks like you've chosen Lubuntu (the LXDE desktop) which is a fine choice for lower hardware. It doesn't require 3D acceleration.
4. Install a modern graphics card into your computer. Most graphics cards these days will be PCI-E and unsuitable for your computer, however I believe there are a small number of modern graphics cards that are made in regular PCI versions. If you can grab a recent one (I'd recommend one using an Nvidia chip) it should be able to give you some passable 3D performance, enough to run Unity and play HD video. Here's a link, actually: [http://techreport.com/news/21724/zotac-slaps-pci-connector-on-geforce-gt-520](http://techreport.com/news/21724/zotac-slaps-pci-connector-on-geforce-gt-520)

---

### Post by julien-dal-col on 2013-09-15
Thank you very much to all of you for all this information :)
However, I took the lazy path since I recently had the opportunity to get more recent (2008-ish) hardware (MB, RAM, CPU and GPU) for free. With the new hardware 13.04 x64 is running fine now.

Thanks again for everything. At least it helped me understand a bit better what was going on.
Best,
-J-

---

