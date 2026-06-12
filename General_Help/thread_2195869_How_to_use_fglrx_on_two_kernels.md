---
title: "How to use fglrx on two kernels"
date: 2013-12-26
forum: General Help
---

### Post by yoreei.grigorov on 2013-12-26
Hi!
I am using two kernels. A generic 3.8 kernel and an older one (3.2.0-25) which is built for PHC(undervolting stuff). When I install the proprietary driver for my Radeon HD 6xxx on one of those kernels and then boot the other and install it there, when I switch back to the first kernel, I have to install it again. I suppose fglrx removes other fglrx installations before installing. Is there a way to use the proprietary driver on both kernels?

---

### Post by yoreei.grigorov on 2013-12-27
Solved it! It is interesting how there is no information on the Internet on how to do this. The only thing I could find was a thread on which someone was asking the same thing. He never got an answer.
That's why I will tell you how I did it. Not because it's hard for someone to come with a solution but because there is ABSOLUTELY NO information on Google.

Replace kernel_A and kernel_B with the kernels you want fglrx on. In my case I replaced kernel_A with 3.2.0-25-generic-phc and kernel_B with 3.8.0-34-generic

1)Run amd-catalyst-13.12-linux-x86.x86_64.run on kernel_A #or whichever version of catalyst you choose to install
2)Copy /lib/modules/kernel_A/updates/dkms/fglrx.ko to ~/Desktop/ 
3)Reboot and select kernel_B
4)Run amd-catalyst-13.12-linux-x86.x86_64.run again
The installer automatically deletes the fglrx module from kernel_A. However, we have previously copied it to the Desktop. Now we can put it in place again
5)Move  ~/Desktop/fglrx.ko to /lib/modules/kernel_A/updates/dkms/fglrx.ko
**If you boot kernel_A now, it won't load the fglrx module. This is because modprobe doesn't know how to load it correctly!**
6)Boot kernel_A
7)```
sudo depmod -a
``` this will tell modprobe how to load the module
8)reboot
Now you have fglrx on both kernels.

I hope this will help you all who have faced this trouble.

---

