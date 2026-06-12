---
title: "[SOLVED] Custom compiled kernel and updates"
date: 2008-06-05
forum: General Help
---

### Post by Benjamin_Vedder on 2008-06-05
Hi

I have an creative x-fi xtreme gamer soundcard and i had to recompile my kernel in order to get it working with the alsa driver. Now a new update, linux-image-2.6.24-18-generic, is avaible. As far as i understand, thats a new version of the kernel. Should i install that update, or just ignore it to keep my soundcard working?

---

### Post by drs305 on 2008-06-05
Is your compiled kernel listed in synaptic (and not just the vanilla version)? If this is the case then adding the new kernel would simply add it automatically to grub's menu.lst as an option. 

You can check StartUp-Manager's settings to ensure that the menu will display at least 2 kernel options during boot. Adding a new kernel doesn't overwrite previous kernels, so you should be able to go back and use your compiled kernel should 18 not work out. The question becomes - how to you get back to your old kernel. I would make a backup copy of /boot/grub/menu.lst. You can restore that version if the new menu.lst or new kernel don't work out.

Finally, do you know of any advantage to using the latest kernel? Some would argue why fix something that isn't broken. But I'm a tinkerer so I don't usually follow that advice ;-)


Here are some commands that you might use:

Install StartUp-Manager:
```
sudo aptitude install startupmanager
```

Backup menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-`date +%F`
```

Read about grub boot options:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Benjamin_Vedder on 2008-06-05
I followed this (with full success):
 [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675") 
to recompile my kernel. I heard that using the driver for that card with the default kernel will result in a kernel panic when attempting start the computer, and if that is the case i wont be able to start my computer at all. Well, i will try to install the updates and if it messes my computer up i just have to boot with the live cd and restore my grub. I will report back when i have tried.

---

### Post by drs305 on 2008-06-05
Installing the new kernel won't mess up your grub menu other than your compiled version may no longer be missing (well, I guess nothing is guaranteed). I was more concerned that your compiled kernel will still be available, but it should be.

Let us know how it works, and mark solved if successful.

Good luck.

---

### Post by bodhi.zazen on 2008-06-05
> **Benjamin_Vedder said:**
> I followed this (with full success):
 [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675") 
to recompile my kernel. I heard that using the driver for that card with the default kernel will result in a kernel panic when attempting start the computer, and if that is the case i wont be able to start my computer at all. Well, i will try to install the updates and if it messes my computer up i just have to boot with the live cd and restore my grub. I will report back when i have tried.

That is what old kernels are for. Always keep at least one old, known working kernel. To boot the old kernel, select it from the grub menu.

---

### Post by Benjamin_Vedder on 2008-06-05
I installed the updates, and the new kernel appeared in /boot/grub/menu.lst, but it did NOT replace my custom kernel as the first choice, as the updates usually do. I tried booting with the new kernel, but as i suspected, the sound didnt work. Booting with the custom kernel still works as good as before.

---

### Post by drs305 on 2008-06-05
> **Benjamin_Vedder said:**
> I installed the updates, and the new kernel appeared in /boot/grub/menu.lst, but it did NOT replace my custom kernel as the first choice, as the updates usually do. I tried booting with the new kernel, but as i suspected, the sound didnt work. Booting with the custom kernel still works as good as before.

The default setup in StartUp-Manager must be set to not upate automatically to a new kernel as default. Sorry the new kernel didn't work out.

---

