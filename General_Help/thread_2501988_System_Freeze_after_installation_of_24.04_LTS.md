---
title: "System Freeze after installation of 24.04 LTS"
date: 2024-10-29
forum: General Help
---

### Post by milspec91 on 2024-10-29
So I’ve dual-booted Windows 11 and Ubuntu 24.04 LTS on my older ASUS ROG G75VW (base specs).
I am able to log into the environment just fine, but seemingly after a minute or two, it just hangs and freezes. No response from the mouse, the keyboard does still adjust backlight of the screen and keyboard itself, along with volume which does play through the speakers (though Ubuntu does not acknowledge the change in display brightness or volume level).

I’ve tried booting in “safe mode” and repairing packages, but that didn’t seem to help. I unplugged my USB Logitech Media keyboard, leaving only OEM peripherals.

Help?

---

### Post by dwaynelucas on 2024-10-29
Update drivers, especially GPU. Check logs (dmesg or /var/log/syslog) via Ctrl + Alt + F3. Try switching NVIDIA drivers or boot with nomodeset or acpi=off. Test with an older kernel if needed

---

### Post by grahammechanical on 2024-10-29
These "base specs" what are they? How much system memory? How much video card memory? Open System Monitor and look at the Resources tab and then use the Processes tab to see what is using either the CPU and/or memory. Some process may be sucking up memory.

Is the operating system in its default state? Have you installed additional applications? If so, which ones?

When at the Grub boot menu select Advanced options for Ubuntu and then select a Linux kernel with a recovery option. That should load a menu. Select Resume. That will load the desktop using an open source video driver. Does the system work better using an open source video driver.

Use Software & Updates>Additional drivers tab to disable the proprietary video driver or select a another proprietary video driver.

Regards


Regards

---

### Post by milspec91 on 2024-10-29
> **dwaynelucas said:**
> Update drivers, especially GPU. Check logs (dmesg or /var/log/syslog) via Ctrl + Alt + F3. Try switching NVIDIA drivers or boot with nomodeset or acpi=off. Test with an older kernel if needed

How would one update the NVIDIA drivers? And downgrade to 23 instead of 24?

> **grahammechanical said:**
> These "base specs" what are they? How much system memory? How much video card memory? Open System Monitor and look at the Resources tab and then use the Processes tab to see what is using either the CPU and/or memory. Some process may be sucking up memory.

Is the operating system in its default state? Have you installed additional applications? If so, which ones?

When at the Grub boot menu select Advanced options for Ubuntu and then select a Linux kernel with a recovery option. That should load a menu. Select Resume. That will load the desktop using an open source video driver. Does the system work better using an open source video driver.

Use Software & Updates>Additional drivers tab to disable the proprietary video driver or select a another proprietary video driver.

Regards


Regards

I’ll give this a go!

Specs are as follows:
Intel Core i7 3610QM @ 2.3GHz
NVIDIA GeForce 670M w/3GB Dedicated VRAM
16GB DDR3 - 1600MHz
500GB HDD

The OS is in a default state - a complete fresh and indicated successful install from a bootable USB drive. The standard “Try and Install Ubuntu” froze/hung the same way. I couldn’t get the environment to start the install, so I opted for the second option along the lines of “something’safe,’” which allowed me to fully install 24.04.

I wasn’t sure if accessing the internet was a factor, each time it froze it was usually after opening a window - any window. First it was the first boot welcome screen then it froze, second after a force power off was settings, third after a 2nd force power off was the App Store.

At that point I gave up.

---

### Post by milspec91 on 2024-10-29
I booted into Recovery and the system ran fine. The aspect ratio and resolution were off and were not changeable.

Going into Software & Updates/Additional Drivers yielded no other drivers found.

I booted back into the environment without Recovery Mode and quickly went to Software & Updates/Additional Drivers and found it was using the “Open Source” driver, I changed it to the proprietary NVIDIA one and applied, it failed.

I’ve also tried downloading a “.run” file downloaded from NVIDIA for my graphics card, ran it using sudo sh ./[file name].run which yielded some promising results. However it says that my X server is running. Doing some research on that people said to push Cmd+Alt+F1 to open the terminal at the login screen — I don’t see it.

Now I’m back to square 1.

Any thoughts or suggestions would be greatly appreciated!

---

### Post by yancek on 2024-10-29
Did you follow the instructions at the Nvidia site at the link below?  The first paragraph states "Before you begin the installation, exit the X server" so do that before running the script.

 [https://download.nvidia.com/XFree86/Linux-x86_64/304.137/README/installdriver.html](https://download.nvidia.com/XFree86/Linux-x86_64/304.137/README/installdriver.html)

> Cmd+Alt+F1 to open the terminal at the login screen — I don’t see it.
 

I expect they mean to hold down those keys simultaneously at the login screen.

---

### Post by milspec91 on 2024-10-29
> **yancek said:**
> Did you follow the instructions at the Nvidia site at the link below?  The first paragraph states "Before you begin the installation, exit the X server" so do that before running the script.

 [https://download.nvidia.com/XFree86/Linux-x86_64/304.137/README/installdriver.html](https://download.nvidia.com/XFree86/Linux-x86_64/304.137/README/installdriver.html)



I expect they mean to hold down those keys simultaneously at the login screen.

I do not see anything change when holding cmd+alt+F1 on both keyboards at the login screen.

---

### Post by bobunderwood99 on 2024-10-29
Not _cmd_+alt+F1

**Ctrl+Alt+F1**

---

### Post by vmpx on 2024-10-31
Try nomodeset parameter in GRUB.

---

