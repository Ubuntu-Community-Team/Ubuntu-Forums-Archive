---
title: "why no 4.13 update kernel on some computers"
date: 2018-02-13
forum: General Help
---

### Post by missmoondog on 2018-02-13
i have 1 computer that received the 4.13 kernel right after it's release. several other computers/laptops have never received it although i have seen variations of it in the section under new in repository using synaptic. i'm using lubuntu 16.04 on all machines. have a combination of 32bit and 64bit machines.

nothing really radically different in specs between any of the machines, so why is this happening?

thank you

---

### Post by #&amp;thj^% on 2018-02-13
Is it the 32bit computers that are not seeing the newer kernel?

---

### Post by missmoondog on 2018-02-13
both 32bit and 64bit are not seeing it on computers that don't have it.

the 1 machine that got it is a 64bit.

---

### Post by #&amp;thj^% on 2018-02-13
The 16.04 HWE Stacks will follow a new Rolling Update Model as documented at the following location:

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

It is highly recommended to read the above documentation before executing the following commands, as the HWE model has changed in 16.04. 
Kernel EOL's [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support)

---

### Post by cruzer001 on 2018-02-13
This can depend on how you originally installed Ubuntu.

If the installation used the original 16.04 or the first point release (16.04.1) then those two releases will continue to use the 4.4 kernel.  The 4.4 kernel is supported for 5 years.

If you installed 16.04.2 or later then these point releases uses HWE and will continue to upgrade the kernel.  The newer HWE kernels are upgraded to the next version every 6 months.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

Ninja'ed by 1fallen :)

---

### Post by Impavidus on 2018-02-13
If the hardware enablement (hwe) stack has been installed (usually via the package linux-image-generic-hwe-16.04), kernel 4.13 should be pulled in automatically. This should be the case if (L/X/K-)Ubuntu was installed using the live disk version 16.04.2 or later. If the system was upgraded from a release before 16.04 or was installed using 16.04 or 16.04.1, the hwe stack was not installed by default and the system should use kernel 4.4. From a security standpoint it doesn't matter, 4.4 is still fully supported on (L/X/K-)Ubuntu 16.04.

If the system uses neither 4.4 nor 4.13, there's a problem.

(When I click reply, I should type and click post at once. Not first read some other things...)

---

### Post by missmoondog on 2018-02-13
> **cruzer001 said:**
> This can depend on how you originally installed Ubuntu.

If the installation used the original 16.04 or the first point release (16.04.1) then those two releases will continue to use the 4.4 kernel.  The 4.4 kernel is supported for 5 years.

If you installed 16.04.2 or later then these point releases uses HWE and will continue to upgrade the kernel.  The newer HWE kernels are upgraded to the next version every 6 months.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

Ninja'ed by 1fallen :)

that explains it then. all machines but the one that got that update were installed using original 16.04 release. the one that received it used the 16.04.3 release.

thank you :)

thank you also for those links 1fallen

edit:
thank you also Impavidus. your reply came through as i was entering mine :)

---

