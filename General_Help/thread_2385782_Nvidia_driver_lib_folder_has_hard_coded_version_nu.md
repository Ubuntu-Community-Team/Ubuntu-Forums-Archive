---
title: "Nvidia driver lib folder has hard coded version number"
date: 2018-02-24
forum: General Help
---

### Post by monkeybrain20122 on 2018-02-24
In my laptop the libraries for the Nvidia driver is installed in a folder stupidly named /usr/lib/nvidia-390 Since this is not in system's path I need to export LD_LIBRARY_PATH when I want the system to see it. Normally I can just put 
```
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/lib/nvidia-390"
``` in my .profile or .bashrc but since its version number is hard coded this means I have to change this everytime the driver update.  I thought of symlinking to something like /usr/local/lib but this doesn't solve the problem since I would then have to update my symlink everytime the driver update, which is potentially even more messy.


Is there a more elegant way?
Thanks.

---

