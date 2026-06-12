---
title: "Kernel update xorg could not connect acpi daemon?"
date: 2015-06-06
forum: General Help
---

### Post by einstein**-7 on 2015-06-06
Hi there I'm running ubuntu 14.04 with kernel 3.13.0-43 and manually installed Nvidia 340.58.

Problem is Just updated the kernel to 3.13.0-53 and manually removed the nvidia driver and rebuilt it for the new kernel but xorg.log is saying something about not being able to connect to the acpi daemon? 
Even more odd is I have the exact same kernel version and nvidia driver on a USB system and it updated and worked fine - didn't even have to rebuild the nvidia driver.....???? 

The main system works fine with the driver built for the older kernel version but I would like to have everything updated and working.
 
Below is some logs from the system...

---

### Post by einstein**-7 on 2015-06-06
Ok just rebooted the system so I could build the Nvidia drivers for the new kernel version and get fresh error logs. However after installing the driver and starting lightdm the system worked fine and logged into the desktop with everything cool.  
After rebooting the system It failed to get the unity-greeter screen up just hung at the ubuntu loading screen..  I then repeated the above procedure but this time suspecting some kind of authorizations failure since it worked before but not after the reboot--  I ran a ```
sudo chown -R $USER:$USER $HOME
``` since I've had problems before with my user getting root admin access changed due to running sudo commands from within the HOME directory which in this case was the Downloads folder where the nvidia driver resides.. 
This seemed to fix the problem and after rebooting the system loads up fine.:lolflag:
Weird thing is I ran the same commands from the usb system and no authorization changes/problems:rolleyes:

---

### Post by einstein**-7 on 2015-06-08
More problems..  after rebooting a second time the system refused to go past the ubuntu loading screen again.
I removed the new kernel and headers and completely purged the related files and system worked fine on older kernel. Then reinstalled them thinking maybe something went wrong during the install but same thing no luck.

The one way I can get the new kernel to load and bring up the working unity-greeter screen is to select advanced options in grub , select recovery mode, then resume normal boot from there and all works???? 
Anyone know what could be causing this or how to diagnose it?

---

### Post by einstein**-7 on 2015-06-08
Also found that is I change the mode from ro to rw in the boot options it boots and works fine? Which is the same thing as the recovery menu which also mounts in rw mode and thus the success but I'm wondering why it wont boot in read only mode like all the previous kernels and also I have the same kernel on a usb as mentioned above and that on boots fine in ro mode.  For now I'm going to edit the etc/default/grub to change the read write mode but I would still love the have the system boot normally with no workarounds.
Any insight into the cause would be great.

---

