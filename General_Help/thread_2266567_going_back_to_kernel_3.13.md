---
title: "going back to kernel 3.13?"
date: 2015-02-23
forum: General Help
---

### Post by grier-devon on 2015-02-23
I had upgraded to kernel 3.16, I am having graphic problems with games freezing and weird flashing in Minecraft. How can I downgrade to kernel 3.13 for Ubuntu 14.04.2.

---

### Post by dino99 on 2015-02-24
you might have some issue with the graphic driver, not the kernel. Logs should bring you some usefull warnings/errors to fix first.

---

### Post by Bucky Ball on 2015-02-24
Unless you uninstalled the 3.13 kernel it is still there. You can reboot and choose the previous kernel from the grub menu. If you machine boots directly to Ubuntu, hold down the shift key at boot. That should bring the menu up and list all your kernels (choose Advanced and the previous kernels should be there).

As mentioned, you may not have the appropriate drivers for graphics installed in the new kernel. Was there a specific reason you installed the 3.16 kernel? Presuming you are using 14.04 LTS?

---

### Post by sticksabuser on 2015-03-23
I'd like to do the same thing. I upgraded to the "Hardware Enablement Kernel" for 14.04 (so kernel 3.13 to 3.16 using the commands indicated here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) and I've had issues with freezes and HID inputs not working properly. I just want to revert back to the 3.13 kernel, and have not been able to do so without almost ruining my ubuntu instance. 

So basically, if someone knows the proper way of doing so, and has already done so successfully, that would be VERY HELPFUL. 

I do NOT need someone to debug the issues I'm having with 3.16.

Thanks in advance.

PS: I do believe that the old kernel and the Xorg stuff is removed in the process of upgrading to 3.16 using the process indicated in the url above.

---

