---
title: "[SOLVED] Copy image to another PC"
date: 2008-04-16
forum: General Help
---

### Post by Kandinsky on 2008-04-16
Hello,

I have a question concerning coping a Wubi disk image to another machine.

i have installed Ubuntu Daily build on my laptop A and configured the new system. Everything worked perfect! The system on laptop A boots without any additional kernel parameters.

I copied the configured image (the ubuntu directory) to another laptop B, installed the grub4dos boot loader and changed the menu.lst entries to match the kernel and initrd locations. 

The system boots but hangs after clocksource unstable. 
I thought I can fix the problem by using different kernel parameters like noscsi, acpi=off noadm,etc.
I was not able to boot the copied image on laptop B

I deleted the image and reinstalled Ubuntu with Wubi.
After reinstalling the image, Ubuntu boots fine on laptop B.
No kernel parameters are required to boot the system on laptop B.

Do you know  why I cannot boot the copied image?
Could it be a problem with the root UUID kernel parameter?
How can I generate a new root uuid?

Many thanks for your help & the excellent Wubi

Kind regards,

Kandinsky

---

### Post by ago on 2008-04-16
Yes, UUID will change
That is a unique number associated to each partition, if you use the same installation to a different partition the UUID will have to be changed.
You can use a generic device notation such as /dev/sda2

UUID are also used in /etc/fstab
Note also that Wubi/Ubuntu do some hardware detection/configuration. So if the 2 machines are different, the copied installation might have suboptimal (or outriwght wrong) hardware configuration.

---

### Post by Kandinsky on 2008-04-16
Hello Ago,

thank you very much for your quick reply.

Both laptops are different brand and model.

Is it possible to run the hardware detection/configuration on laptop B?
In case this is not possible, I could mount the image from laptop A and cp all settings. 

Do you know which directories I would need to cp to get all the synaptic packages, installations and desktop settings?

Many thanks,

Kandinsky

---

### Post by ago on 2008-04-16
System settings are in /etc   (careful with fstab, X11, and networking settings)
User settings are in /home
For a "replaying" a list of packages use dpkg get/set-selections ([http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html))

It is fine to copy over /home 
I do not suggest copying over all of /etc  (just import individual settings as needed)
dpkg get/set-selections  is great

---

### Post by Kandinsky on 2008-04-16
Thanks you for you competent reply ago.

---

