---
title: "GPIO - allowing permissions"
date: 2015-04-17
forum: General Help
---

### Post by carr3 on 2015-04-17
Hi,

I have a program that uses the GPIO of a NVIDIA Jetson TK1 (ubuntu 14.04).  I have no problem running the program while using sudo, but I run into problems when I try running the program without sudo or as a user other than root.  I get the following errors:

gpio/direction: permission denied 
gpio/export: permission denied

Is there a way to allow permissions to the GPIO so that any user can access them.  I have tried using: chmod s+u sys/class/GPIO, but I still get the errors listed above.

Any help would be appreciated.

Thanks,
Carr

---

### Post by carr3 on 2015-04-18
I've tried adding permissions using chmod +x [filename] to the executable as well as the .cpp and recompiled it (and reapplied permission changes) but it still cannot change the GPIO values. 

Any ideas? 

Thanks,
Carr

---

### Post by ktaye on 2015-07-19
Hello Carr,
Did you figure out how to allow GPIO access without using sudo? I am having the same problem. Please let me know if you figure out the issue.
If you are interested in accessing I2C without sudo, you can check out here : [http://devtalk.nvidia.com/default/topic/856949/?comment=4607307]("http://But accessing I2C is fine. If you would like to know, you can check here ; https://devtalk.nvidia.com/default/topic/856949/?comment=4607307")
Thank you
kt

---

