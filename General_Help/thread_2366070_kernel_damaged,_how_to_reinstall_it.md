---
title: "kernel damaged, how to reinstall it?"
date: 2017-07-13
forum: General Help
---

### Post by ubto66 on 2017-07-13
ubuntu 14.04 64bit
kernel 3.13.0 123
kernel 3.13.0 121

This may have happened. I turned off the notebook. No error messages. I turned on the notebook and booting [https://www.osdisc.com/products/linux/systemrescuecd?affiliate=sysresccd](https://www.osdisc.com/products/linux/systemrescuecd?affiliate=sysresccd) from a dvd.
I wrote command flashrom -p internal.
Got an error message. Then powered off the computer. Maybe the command damaged the system.
Starting the computer, the screen was full of technical text. One word was kernel error. The system would do nothing. Then I restarted and selected advanced options. I selected the previous kernel version. Then the computer booted ubuntu and works.

I think the newest and likely damaged kernel version is 3.13.0 123. The previous kernel version is 3.13.0 121. Can you tell how to reinstall the newest kernel?
Thanks.

---

### Post by efflandt on 2017-07-13
By "I turned off the notebook." did you do a proper shutdown, or simply turn it off with power button? You should avoid shutting off with the power button unless all else fails.

If you interrupted installation of most recent kernel, you should be able to fix that by booting a kernel that works, and assuming that you do not have a separate too small /boot partition that is full, should be able to fix it with:```
sudo apt-get update
sudo apt-get install -f
```That should attempt to fix any broken packages.

---

### Post by ubto66 on 2017-07-14
Thank you. > turned off the notebook."
I wrote poweroff.

```
sudo apt-get update
sudo apt-get install -f
```

It did not work.

If the computer is powered on, this text and a lot more displays:
kernel panic not syncing no working init found try passing init= option to kernel see linux documentation/init.txt.
cpu 1 pid: comm: swapper/0 not tainted 3.13.0-123-generic # 172-ubuntu

Pressing the power off button, I turn off the computer. Restart. Then the grub version 2.02 options display. I select 'advanced options'. Then selecting ubuntu 3.13.0 121. Ubuntu starts and works.

In synaptic package manager I have done a complete removal of 3.13.0 123. It did not solve the kernel error. Solutions?

---

