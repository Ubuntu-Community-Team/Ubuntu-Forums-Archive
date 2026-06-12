---
title: "Boot failure perhaps broken video driver (nvidia), how to reinstall"
date: 2006-11-14
forum: General Help
---

### Post by Crakie on 2006-11-14
My Edgy system has been up and running for a couple of weeks, but yesterday, without any warning, it failed to boot properly. 

At boot, my screen goes blank after showing the initial Kubuntu logo with the progress bar gradually filling up. Ordinarily, the Nvidia beta-driver screen would flash and the login screen would show. Since it does respond to control-alt-del a couple of times (of course, it will reboot), the system doesn't hang. It just doesn't give any visual output.

I tried reinstalling my graphics driver, which appeared succesful, but it did not help. Can anyone help me out completely whiping xserver etc. and then reinstalling from the command line (accessible through single user mode in the Grub boot menu)?

---

### Post by catlett on 2006-11-14
This may help you get back into the system but it will be at the cost of your nvidia beta drivers. If you can get to a command line, you should be able to select 'recovery mode' from grub. Enter this command ```
sudo dpkg-reconfigure xserver-xorg
``` That will take you through the xserver setup. Basically it will go through your keyboard, mouse and more importantly your monitor and graphics card. When it lets you select the driver for your video card try "vesa". It is a generic choice and should allow you to boot without a problem IF the video card driver was the initial problem.

---

