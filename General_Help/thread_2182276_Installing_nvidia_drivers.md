---
title: "Installing nvidia drivers"
date: 2013-10-20
forum: General Help
---

### Post by TimEnid on 2013-10-20
Can i use a live cd to install the drivers to my OS. I can't access it directly. I'm on 13.04.

---

### Post by buzzingrobot on 2013-10-20
I'm 99% certain the answer is "No". The Nvidia proprietary drivers are not incuded on the Ubuntu install images. They are available after installation via the "Additional Drivers" function, which downloads and installs the driver you select.

---

### Post by TimEnid on 2013-10-20
> **buzzingrobot said:**
> I'm 99% certain the answer is "No". The Nvidia proprietary drivers are not incuded on the Ubuntu install images. They are available after installation via the "Additional Drivers" function, which downloads and installs the driver you select.

Thanks. I am running 13.04, but can not log in and i believe it is a driver error. I get an all black screen, with no option to log in. I can not find a way to bring up a terminal so that i can install the driver. So, is there an alternative to installing the drivers on my system?

---

### Post by buzzingrobot on 2013-10-20
There are various parameters that can be passed to the kernel at boot time to cirumvent video card issues long enough to allow a proprietary driver to be installed. The most common of these is "nomodeset".

This is done by interrupting the boot process, editing the grub (bootloader) menu to add the 'nomodeset" parameter, then continuing the boot.  

You can find a lot of guidance about how to do this, but here is what I found: [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu).  This is for an older Ubuntu version , but the directions haven't changed. It tells you to hold the shfit key down after you see the BIOS boot screen.  Many people may not see that, so just hold down the *left* shift key as soon as the machine boots until the grub menu appears.

The kernel vesion number in 13.04 is diferent, but the editing instructions at the link are accurate. It's a very rudimentary editor, so don't expect much.

If nomodeset is successful, you will probably boot into a low resolution screen.  That's inconvenient, but the deal is that you take advantage of it to install the proprietary Nvida driver.

The simplet way to do that is via the "Additional Drivers" tab on the software & updates tool.  Failing that, there are other options.  This is a good outline: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html).

---

### Post by Frogs Hair on 2013-10-20
> **TimEnid said:**
> Thanks. I am running 13.04, but can not log in and i believe it is a driver error. I get an all black screen, with no option to log in. I can not find a way to bring up a terminal so that i can install the driver. So, is there an alternative to installing the drivers on my system?


To enter tty use Ctrl + Alt +F1 and Ctrl + Alt +F7 to back out . You can install from tty among other things .

---

