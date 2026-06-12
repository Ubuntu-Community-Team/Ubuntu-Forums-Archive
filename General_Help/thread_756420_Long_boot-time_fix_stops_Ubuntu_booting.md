---
title: "Long boot-time fix stops Ubuntu booting"
date: 2008-04-15
forum: General Help
---

### Post by webplus on 2008-04-15
I had Ubuntu 7.10 installed on my VAIO laptop, and had a long boot-time problem, so I  followed these instructions ([http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html](http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html)) which fixed the problem.

I've now set up a dual-boot system running Ubuntu 7.10 on the 1st partition and Linux Mint 4.10 on the 2nd partition.  I was having the Ubuntu long boot-time issue again so I applied the above fix again.  This time, when Ubuntu tries to load, I get text on screen that says 'Loading, please wait...' and it just sits there and never boots.  Linux Mint is the default boot and bootloader in use at the moment and that still loads without any problems.

I managed to change the menu.lst back to how it was before and retried, but the same thing happens.  If I try to boot the Ubuntu recovery mode it hangs when trying to load the file system.

I think the problem might be the command:  sudo update-initramfs -u -k `uname -r`  

I was unable to run this again after switching back to the backup of menu.lst because I think it needs to be run within an Ubuntu login and not the Linux Mint login, but I can't get Ubuntu to load or provide a login to run this from the Ubuntu installation.

Is it all messed up? Should I reinstall everything again?

Thanks in advance.

---

### Post by gsmanners on 2008-04-16
If you're in another OS or a live CD, you'll need to chroot to do that properly. Something like:

sudo mount /dev/hdax /mnt
sudo chroot /mnt update-initramfs -u
sudo umount /mnt

Not sure if that will work specifically, but something like that.

---

