---
title: "[SOLVED] Nvidia driver issues"
date: 2008-05-24
forum: General Help
---

### Post by overdrank on 2008-05-24
Ok I have the nvidia drivers installed on my system with  a leadtedk 6800 agp graphics card and hardy. I also have another system with onboard nvidia graphics 6100. No issues what so ever but with my son's system MSI motherboard, AMD 3500, Leadtek 6800 PCI x I can not get the drivers to work. I have tried everything under the sun as uninstall and reinstall, Envy and I mean everything. Gutsy will load and the drivers and all works great. If you have any suggestion please post. As I have said I have tried reconfiguring and everything else under the sun and I fancy myself pretty good with the graphics on Ubuntu. Thanks.

---

### Post by RATM_Owns on 2008-05-24
sudo aptitude install nvidia-glx-new

Should be like that. I forget. Can't use Synaptic now as I'm using it for adding KDE4 to my sessions list.

---

### Post by overdrank on 2008-05-24
> **RATM_Owns said:**
> sudo aptitude install nvidia-glx-new

Should be like that. I forget. Can't use Synaptic now as I'm using it for adding KDE4 to my sessions list.

Hi and yea I tried installing the glx-new after removing. And the drivers would install but resolution would be only at 640
And more info when I would reinstall the linux restricted then I would loose sound.

---

### Post by overdrank on 2008-05-26
Just a bump to get more ideas. :)

---

### Post by overdrank on 2008-06-07
HI and I solved my issues on two systems with nvidia drivers and installed the latest driver from nvidia on one system with gutsy. Believe it or not this issue happened in a existing system.
I removed the nvidia drivers then used envy along with PmDematagoda suggestion 
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
Found here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)
Now I have not tried on the system that the post was originally about but I am sure it will work cause as I said it worked on a clean install of Hardy and a existing system with Gutsy and it has the new nvidia driver. good luck

---

