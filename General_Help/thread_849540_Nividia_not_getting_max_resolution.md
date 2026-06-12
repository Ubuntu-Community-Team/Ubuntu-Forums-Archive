---
title: "Nividia not getting max resolution"
date: 2008-07-04
forum: General Help
---

### Post by rcullan on 2008-07-04
Before anyone replies, 
I know good and well there are TONS of posts on this, I have tried everyone of them I have found and I can NOT figure this damn thing out.
I have a NVIDIA GeForce 5200 FX, and am on a fresh install of Ubuntu 8.04 (updated to current)

I have also enabled the NVIDIA accelerated graphics driver through System>Administration>Hardware Drivers

My problem is I am still stuck at 1024x768 reolution, and I need 1280x1024!
I use this in windows and not having it in Ubuntu is driving me absolutely bonkers.

What is the solution to this? Do I need to edit xorg.conf?

Thanks in advance.

---

### Post by ellgor on 2008-07-05
Try this if you haven't already,

In a terminal type in [ gksudo nvidia-settings ] press enter and a new window will open with the nvidida settings for you to play with, adjust as necessary (if the settings box is blank, play around with the controls until the settings are shown), hope this helps.

Regards, Ellgor.

---

### Post by rdchin on 2008-07-08
I had the same problem on my new install but I solved it differently. I was running 7.10 then reformatted that partition and did a fresh new install of 8.04.1 LTS.

Issue: Using the tool included in 8.04.1 LTS did not work. Namely, System > Administration > Hardware Drivers > NVIDIA accelerated graphics drivers. Interestingly enough the tool worked for me when I used 7.10.

I used System > Administration > Synaptic Package Manager and searched for "nvidia" to get a list of all nvidia packages. Then used trial and error until I found compatible packages which worked.

When I tried to use Applications > System Tools > EnvyNG apparently this did not work at first, I'm not sure why. It may have been because I had not yet installed nvidia-glx-new-envy.

After installing the packages, a new menu entry showed up, System > Administration > NVIDIA X Server Settings. This is the tool that gave me all the high-resolution screens.

I'm not sure that I need Envy, but I'm not changing anything now that I got it working. Also under System > Administration > Hardware Drivers, the NVidia drivers are still not used with this tool because this tool will load the nvidia-glx-new and not the one that works nvidia-glx-new-envy.

Hope this helps someone.

What did not work:
nvidia-glx-new (version 169.12+2.6.24.13-19.44)
nvidia-kernel-common (version 20051028+1ubuntu8)
nvidia-settings

What did work:
nvidia-glx-new-envy (version 173.14.05+2.6.24.501-501.30)
nvidia-kernel-common (version 20051028+1ubuntu8)
nvidia-settings
envy-ng-core
envy-ng-gtk
jockey-common
jockey-gtk

---

