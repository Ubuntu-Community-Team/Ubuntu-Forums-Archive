---
title: "Booting with kernel 4.10.0-32 and Nvidia."
date: 2018-02-18
forum: General Help
---

### Post by Hewjr100 on 2018-02-18
Question, is itpossible to boot with kernel 4.10.0-32 without installing Nvidiaproprietary drivers.  I am currently forced to boot with kernel4.10.0-28.  Did install Nvidia drivers, but when using a web browser,scrolling up and down cause the page to ripple.  Reinstalled Ubuntu16.04 in EFI mode.  Now I need help in getting Ubuntu to boot whiththe newer kernel.


Henry

---

### Post by Impavidus on 2018-02-18
Isn't the 4.10 kernel dead? Last month Ubuntu 16.04 with HWE switched to 4.13 after 4.10.0-42. You should be at 4.13.0-32 now. Or was that what you meant? But there was no 4.13.0-28.

Sorry, I don't know about nvidia.

---

### Post by cruzer001 on 2018-02-18
Perhaps you would be better off using the 4.4 kernel thats supported till 2021.  The 4.10 series reached end of life about a year ago.

---

### Post by Hewjr100 on 2018-02-18
That is why I need to be able to boot 4.13.x  Perhaps this will be fixed in Ubuntu 18.04.

Henry

---

### Post by Hewjr100 on 2018-02-19
BTW this was a fresh install which uses kernel 4.10.0-28  4.4 is not available.

Henry

---

### Post by Hewjr100 on 2018-02-19
After installing it updates to 4.13, which does not boot for me, unless I boot in recovery mode.  Recovery mode sucks because you are promted 2 times to continue...as if I don't know what I am doing.

Henry

---

### Post by cruzer001 on 2018-02-19
> **Hewjr100 said:**
> BTW this was a fresh install which uses kernel 4.10.0-28  4.4 is not available.

My install using 16.04 iso (16.04.1 iso will give same results):
```
~$ lsb_release -d && uname -r
Description:	Ubuntu 16.04.[COLOR="#FF0000"]3[/COLOR] LTS
[COLOR="#FF0000"]4.4.0-112-generic[/COLOR]
```

---

### Post by Hewjr100 on 2018-02-19
But not 16.04.3

```
lsb_release -d && uname -rDescription:    Ubuntu 16.04.3 LTS
4.13.0-32-generic
```

[ATTACH=CONFIG]278593[/ATTACH]

---

### Post by cruzer001 on 2018-02-19
I no longer understand this conversation :(

I think it better to wait for someone more knowledgeable to come along and help you.

Good luck

---

### Post by Impavidus on 2018-02-20
The install media for Ubuntu 16.04 and 16.04.1 come with the LTS kernel. That's kernel 4.4.0 and it will remain at that kernel for the full 5 years of support. The new kernels are pulled in by the package **linux-image-generic**.

The install media for Ubuntu 16.04.2, 16.04.3 and in the future 16.04.4 and 16.04.5 come with the HWE kernel. That's first kernel 4.8, then 4.10, 4.13 and I don't know what they will use for the last. It should be the same as in 18.04. The new kernels are pulled in by the package **linux-generic-hwe-16.04**.

If you want to switch to the 4.4 kernel, you can install linux-image-generic:```
sudo apt-get install linux-image-generic
```Or use any other interface to the package manager you like. Then reboot and use the grub menu, advanced options, to boot the 4.4 kernel. It won't be the default, as the latest kernel is automatically made the default. When that works satisfactory, you can uninstall the 4.10 and 4.13 kernels:```
sudo apt-get purge linux-generic-hwe-16.04
sudo apt-get autoremove --purge
```Make sure all 4.10 and 4.13 kernels are removed. That should make the 4.4 kernel the default.

I don't know about your problem with the 4.13 kernel. Something in your hardware doesn't like it, or there's something wrong with a proprietary drive. There may be a solution to get 4.13 working. Maybe somebody knows.

---

### Post by Hewjr100 on 2018-02-20
Sound like a plan.

Henry

---

### Post by Hewjr100 on 2018-02-20
Sorry for the long delay, but Did another fresh install of 16.04.3 and was able to pull in kernel 4.4 successfuly.  Thanks for your help.

Henry

---

