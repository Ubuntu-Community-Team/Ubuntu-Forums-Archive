---
title: "Latest update freezes at boot: 2.6.15-25.43 k7 kernel"
date: 2006-07-02
forum: General Help
---

### Post by launchclearlaunch on 2006-07-02
I just updated the latest kernel update for k7 linux-image .deb package in Synaptic and when I rebooted it froze at a black screen. I rebooted manually since none of the keys worked and it froze at a white screen. I'm going to attempt a reinstallation of nvidia related drivers to see if this fixes it but why did this happen?

---

### Post by digimars on 2006-07-02
If you are running the nvidia drivers, then every time you install a new kernel or upgrade your current one, then you will have to reinstall your restricted kernel modules and the nvidia drivers.

---

### Post by launchclearlaunch on 2006-07-02
[QUOTE=digimars]If you are running the nvidia drivers, then every time you install a new kernel or upgrade your current one, then you will have to reinstall your restricted kernel modules and the nvidia drivers.[/QUOTE]

Usually when I've updated the kernel I'm presented with additional new nvidia packages to match for the kernel version and restricted kernel modules but this time I was not. There was no message cautioning me that I needed to reinstall these drivers and modules so I didn't know this.

Now I have booted to a previous kernel version so I can go online and reinstall these drivers/modules .deb files. Do I need to reboot and install them for the latest kernel again then since right now I'm using an older kernel? And when doing this when I reboot with the new kernel I have to reboot in the recovery mode and use the deb files I downloaded (drivers and modules) and manually reinstall them correct? I have a dial up internet connection so downloading them a second time isn't sane for me because it takes an hour or so to do.

So what would the apt command be to reinstall them seeing as I can't load X with the new kernel to reload them in Synaptic locally?

I know about apt-get install program but what commands do I use to reinstall with apt?

---

### Post by fordfan753 on 2006-07-02
Use Aptitude if you aren't sure of commands, it's a very good program.

---

