---
title: "kernel unable to mount partitions, after turning off system."
date: 2019-01-22
forum: General Help
---

### Post by tom+n0 on 2019-01-22
my system runs in ubuntu-studio, but with plasma desktop.
i was using a nvidia driver without problems.

i updated the kernel to 4.16-18 and was working ok until i turned off the pc. i tried restarting with other kernels, but the result is the same "bug" (systemctl point kernel cant load modules or mount partitions)
i usually suspend to ram to avoid a minor problem with grub i havent be able to solve (sometimes its not detected, so pc wont boot, or will boot directly to windows, but after rebooting from windows i can use again grub to enter ubuntu)

systemctl from a liveusb reports things like:

dependency failed
unble to load kernel modules
unable to mount partitions

i will try to describe with more detail the problems listed from another computer.
i dont want to reset the whole thing, im i think i read similar problems have happened to other users after updating kernel with systems with many partitons, and also  have been solved.

Also, how can i input my user name and password from a livecd to mount "home" and also move easily other files without changing permissions?

boot-info doesnt show those problems
[http://paste.ubuntu.com/p/Nhsk2FDHdH/](http://paste.ubuntu.com/p/Nhsk2FDHdH/)

i also dont want to try to fix the grub problem before i know the system can start again properly.

thanks for any information.

---

### Post by oldfred on 2019-01-22
Do not run Boot-Repair, you will have to use chroot.
Boot-Repair recognizes separate /boot & /home partitions but not all the other varieties of separate partitions for various system folders.
Standard Ubuntu install is now just / (root) partition and an ESP if UEFI. All other partitions are optional.

How did you install nVidia driver? 
If you used .run directly from nVidia, then you have to reinstall with every kernel update.

Can you boot using recovery mode?

Generally better not to have separate /boot & /var partitions for standard desktop installs.
And you have lots of old kernels, best to houseclean those out, once system is working.
       [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 
            #current install:b_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

