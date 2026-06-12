---
title: "[ubuntu] Help installing Vulkan for AMD gpu"
date: 2017-01-24
forum: General Help
---

### Post by frostbuntu on 2017-01-24
Using the AMD ([http://support.amd.com/en-us/kb-articles/Pages/Install-LunarG-Vulkan-SDK.aspx](http://support.amd.com/en-us/kb-articles/Pages/Install-LunarG-Vulkan-SDK.aspx)) site, I download the vulkan sdk, I create the vulkan directory, and grant it permission to execute.

  
From there I execute the following lines as mentioned in the guide

  
I get to the step where I need to type "cp $HOME/Downloads/vulkansdk-linux-x86_64-version.run ./"

  
which returns the following:

  
codename@codename-desktop:~$ cp  $HOME/Downloads/vulkansdk-linux-x86_64-version.run ./ cp: cannot stat  '/home/codename/Downloads/vulkansdk-linux-x86_64-version.run': No such  file or directory

  
Ubuntu 16.04

  
RX 480

---

### Post by wildmanne39 on 2017-01-24
*Thread moved to **General Help**.*

---

### Post by QIII on 2017-01-24
"cannot stat" means it can't find the file by that name.  That means you have given a file name that does not exist.

You might want to cut and paste the name as it appears in the directory and insert it into the command where appropriate.  My guess is that will be "vulkansdk-linux-x86_64-1.0.30.0.run", not "vulkansdk-linux-x86_64-version.run".  The latter is an example, not an actual file name.

By the way, your 480X may be problematic under 16.04.  Just a warning.

---

