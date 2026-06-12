---
title: "How do I force building of Nvidia kernel module?"
date: 2014-05-09
forum: General Help
---

### Post by halfbeing on 2014-05-09
Hello

Since upgrading to Trusty on one of my machines my video no longer works properly and I get 1024x768 resolution on the full HD TV I use as a monitor. I have an Asus-branded Nvidia EN210 Silent video card. I can't see any trace of the driver in /lib/modules, so I presume that means that it hasn't been built for the current kernel. How can I force my system to build and install the module, if that is indeed the problem?

Thanks in advance.

---

### Post by kc1di on 2014-05-09
It should work with the nvidia 331 driver that's in the Repository.  you can install it by typing in a terminal ```
sudo apt-get install nvidia-331
```
Nvidia lists a newer driver that is beta as 337.19 which may be better. you can download it from the Nvidia site [here.]("http://www.geforce.com/drivers")

If you want to try that one down load the file to your /home/<your user name> directory Hit alt,crtl,f1 to get to a terminal and exicute the .run file.  
follow the instructions.

---

### Post by halfbeing on 2014-05-09
Thanks for replying :)

I do have the nvidia-331 package from the repository installed (I even tried reinstalling it), and the source code appears in /usr/src/, along with a .o file, which I presume is the built module, but I see no sign of the module in /lib/modules and certainly no sign of it when I run lsmod. If I have to I will try to get the module straight from Nvidia, but my system is obviously messed up enough as it is and I don't want to make it even more complicated by going outside the repositories if I can avoid it.

---

### Post by kc1di on 2014-05-09
Check for the nvidia module with this command ```
lsmod | grep nvidia
```  It should retrun an output looking something like this ```
nvidia              11334886  30 
``` the numbers will be different than mine.  If it does not you do not have nvidia driver in place. If it does and it's not working you may need to remove the opensource nouveau driver as it will conflict with the nvidia driver.  you do that with this command ```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```  if all that fails completely purge the  nvidia drivers you have installed and re-installing it.  if that fails download the driver from Nvidia and install it.

---

### Post by drac-noc on 2014-05-10
I thought the nvidia drivers used dkms to build automatically for each new kernel update. Is something awry there?

---

