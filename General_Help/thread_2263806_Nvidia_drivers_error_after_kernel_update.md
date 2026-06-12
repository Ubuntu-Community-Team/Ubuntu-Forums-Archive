---
title: "Nvidia drivers error after kernel update"
date: 2015-02-03
forum: General Help
---

### Post by user9992 on 2015-02-03
Hello,

I installed updates yesterday (Ubuntu 14.04), and there was a kernel update. I got a popup saying that something went wrong with the nvidia drivers (unfortunately, I closed the popup, so I don't remember the exact error message) and the following page opened in my browser: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257)

I haven't rebooted since then. 
Is there a risk I can't access the GUI when I reboot?

What can I do to prevent this?

EDIT:

The following files don't end with an error:
/var/lib/dkms/nvidia-331/331.113/3.13.0-45-generic/x86_64/log/make.log
/var/lib/dkms/nvidia-331-uvm/331.113/3.13.0-45-generic/x86_64/log/make.log

There aren't any errors in /var/log/apt/history.log either.

How can I check what the error was?

EDIT2:

I found something in /var/log/apt/term.log
> Error! Bad return status for module build on kernel: 3.13.0-45-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.113/build/make.log for more information.
However /var/lib/dkms/nvidia-331/331.113/build/make.log does not exist.

---

### Post by user9992 on 2015-02-04
I didn't actually encounter any problems after rebooting. The selected driver is still the Nvidia proprietary driver.

---

### Post by SeijiSensei on 2015-02-04
A note of reassurance:  If the kernel is modified, Ubuntu will retain the previous kernel.  You can then revert to the older kernel at boot when the bootup menu appears.

---

### Post by heliboy on 2015-04-12
Doesn't this error prevent the completion of the kernel update?  If so, isn't this a rather bad bug?  Sounds like an update to nvidia from 331 to 340 is necessary([bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268257"))?  If so, how is that accomplished in 14.04?

edit:  This looks promising:  [nvidia_update]("http://ubuntuguide.net/install-nvidia-proprietary-drivers-in-ubuntu-14-04")

---

