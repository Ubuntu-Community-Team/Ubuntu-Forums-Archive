---
title: "Upgrade from Gutsy to Heron?"
date: 2008-04-26
forum: General Help
---

### Post by GordonFreeman on 2008-04-26
Hello,

is it possible to upgrade from Gutsy to Heron? On the normal installation CD I couldn't find such an option.


Gordon.

---

### Post by smoker on 2008-04-26
hi, you don't need the install cd to upgrade, have a look here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

best of luck

---

### Post by GordonFreeman on 2008-04-26
Ah thank you :-)


If I have problems with 8.04 is there a way to downgrade back to my old system?

---

### Post by smoker on 2008-04-26
that, i am not sure about, though, as you have the cd, you could run the live-cd and see how it goes, if it runs ok from the live cd, then i think it will be the same with an upgrade!

---

### Post by grossaffe on 2008-04-26
I upgraded from gutsy 64-bit to hardy, and I'm just curious if its normal that i now have two versions of hardy available in grub.

they are kernal versions
2.6.22-14 and
2.6.22-16 (i think).

2.6.22-16 seemed to be normal, it had my restricted nvidia driver already installed and what-not, but when i tried 2.6.22-14, i am now in low-graphics mode.  just curious about what this all means, why i have two kernals, and what the difference is between them.

---

### Post by p_quarles on 2008-04-26
> **grossaffe said:**
> I upgraded from gutsy 64-bit to hardy, and I'm just curious if its normal that i now have two versions of hardy available in grub.

they are kernal versions
2.6.22-14 and
2.6.22-16 (i think).

2.6.22-16 seemed to be normal, it had my restricted nvidia driver already installed and what-not, but when i tried 2.6.22-14, i am now in low-graphics mode.  just curious about what this all means, why i have two kernals, and what the difference is between them.
When you upgrade to the new version, it installs the new version of the Linux kernel, which is 2.6.24-16. Installing the new kernel, however, does not remove the earlier installed versions. You can do that manually, of course. 

As for the nVidia problem, can you double check which kernel version it works with?

---

### Post by natrixgli on 2008-04-26
You should be able to do 'sudo apt-get autoremove' to get rid of old kernels. The old kernel won't work with your nvidia driver most likely because the 2.6.24-14 nvidia modules are no longer installed.


Cheers,

-n8

---

### Post by grossaffe on 2008-04-26
> **natrixgli said:**
> You should be able to do 'sudo apt-get autoremove' to get rid of old kernels. The old kernel won't work with your nvidia driver most likely because the 2.6.24-14 nvidia modules are no longer installed.


Cheers,

-n8

oh ok, that makes sense.  so 2.6.22-14 was gutsy gibbon, and when it was prepping to upgrade it uninstalled "outdated" packages such as the old nVidia driver that gutsy used.  thanks for the tip.

---

### Post by p_quarles on 2008-04-26
> **natrixgli said:**
> You should be able to do 'sudo apt-get autoremove' to get rid of old kernels. The old kernel won't work with your nvidia driver most likely because the 2.6.24-14 nvidia modules are no longer installed.


Cheers,

-n8
No, autoremove won't get rid of the old kernel. That needs to be done manually:
```
sudo apt-get remove linux-image-2.6.22-14-generic
```
With "generic" possibly needing to be replaced by any specific kernel architecture that you are using. 

My advice is to leave the old kernel in for a while, until you are certain that everything is working as it should.

---

### Post by fragos on 2008-04-26
delete the old kernel with synaptic and it will take care of grub as well.

---

