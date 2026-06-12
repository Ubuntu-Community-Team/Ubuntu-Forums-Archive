---
title: "Accidentally created a new operating system???!!"
date: 2008-07-09
forum: General Help
---

### Post by antiderivative on 2008-07-09
Hello, I went to the terminal searching for a list of restricted modules, and installed this package:
linux-restricted-modules-2.6.24-19-386

After reboot, my internet drivers magically disappeared, and I couldn't find another reason behind than the new installed software. I rebooted several times, without luck, so I decided to remove it. Removing it did no good! Not only did my internet drivers not come back, but my NVIDIA drivers magically disappeared too! I restarted again, and realized on my boot list that an extra Ubuntu OS was on the selected list to boot from (this is in my BIOS). So I booted from the one below it, and everything on that one was just fine. In other words, my computer had created a new one (the one first on the boot list), and now I have to go below it to boot. I know, this may sound like a minor inconvenience, but I'm used to the BIOS just waiting 8 seconds to boot the first one, while I leave temporarily. I can't do this anymore. Does anyone have any suggestions to getting rid of this unwanted OS?

---

### Post by wannadumpwindows on 2008-07-09
All you did was install another kernel. You can remove it using synaptic package manager.

Just note the numbers of the one you want to remove, and search for it. Once you find it, just click the remove check box, and then hit apply.

On your next boot, everything should be back to normal.

---

### Post by kaola_linux on 2008-07-09
> **antiderivative said:**
> Hello, I went to the terminal searching for a list of restricted modules, and installed this package:
linux-restricted-modules-2.6.24-19-386

After reboot, my internet drivers magically disappeared, and I couldn't find another reason behind than the new installed software. I rebooted several times, without luck, so I decided to remove it. Removing it did no good! Not only did my internet drivers not come back, but my NVIDIA drivers magically disappeared too! I restarted again, and realized on my boot list that an extra Ubuntu OS was on the selected list to boot from (this is in my BIOS). So I booted from the one below it, and everything on that one was just fine. In other words, my computer had created a new one (the one first on the boot list), and now I have to go below it to boot. I know, this may sound like a minor inconvenience, but I'm used to the BIOS just waiting 8 seconds to boot the first one, while I leave temporarily. I can't do this anymore. Does anyone have any suggestions to getting rid of this unwanted OS?

Hi, it seems you had updated your Ubuntu Desktop including a new kernel just select the one with the latest Kernel version and it will be good..

If you want to remove the first two entries on grub simply type in the terminal:
```
sudo gedit /boot/grub/menu.list
sudo gedit /boot/grub/menu.lst
```

I'm not sure where is correct in this 2 just try one after the other if it works then that's it..

When you can access it already, just find the entries similar to the ones you saw on the GRUB menu then you can quote them in order for the entry to not appear using this "##" before there line..or simply erase and save...

Then do this: ```
sudo update-grub
``` and restart

Hope that helps :)

---

### Post by p_quarles on 2008-07-09
EDIT: When I wrote this, "above post" was wannadumpwindows'. :)

The above post is correct, but I wanted to add that you can easily edit the file that controls the startup menu you're talking about. 
```
sudo nano /boot/grub/menu.lst
```
will bring that file up in a text editor. The line that says "default" tells it which item (counting down and starting at zero) should be the default boot option (which will be selected if you do nothing). The "timeout" option sets the number of seconds to show the menu. 

Be careful when editing this file, but changing these two options to other values is safe.

---

### Post by Archmage on 2008-07-09
The list you are seeing is not from the BIOS it is from Grub that start before it starts to load the OS. There are the different version of the kernel listed the highest are the lastest and should be use.

I would suggest that you install the restricted drivers back, so that the newest one will work.

---

### Post by p_quarles on 2008-07-09
> **Archmage said:**
> I would suggest that you install the restricted drivers back, so that the newest one will work.
The restricted drivers should still be there and working fine  . . . it's just that they generally won't work with the i386 kernel. I'm fairly certain that's the only problem.

---

### Post by jocko on 2008-07-09
> **antiderivative said:**
> Hello, I went to the terminal searching for a list of restricted modules, and installed this package:
linux-restricted-modules-2.6.24-19**[COLOR=Red]-386[/COLOR]**

Any kernel related package that ends with **"-386"** is compiled specially for compatibility with ***very old*** processors (such as the intel 386, 486 and the first pentium "586" cpu or amd k5 and older cpus... i.e ~1995 or older).

If you have a modern cpu (pentium pro/amd k6 or newer processors, i.e newer than ~1995), you should use the **-generic** kernel instead.

So search synaptic for "linux-image" and uninstall any package that ends with "-386".
And install the meta package "linux", which will make sure you always have the latest generic kernel and restricted-modules.
**Don't bother about editing the grub menu.** Uninstall the kernel you don't need and it will be removed from the boot menu automagically...

---

