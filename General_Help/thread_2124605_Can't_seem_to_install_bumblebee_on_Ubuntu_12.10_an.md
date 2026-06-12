---
title: "Can't seem to install bumblebee on Ubuntu 12.10 any way possible, can anyone help?"
date: 2013-03-11
forum: General Help
---

### Post by HasnainRaza on 2013-03-11
Hello to all the Ubuntu Users!

I am a new Ubuntu user, and I have a Dell Inspiron n5110 laptop with the following specs:
1. Core i5-2430M
2. NVIDIA GeForce GT525m + Intel HD3000 (hybrid graphics, Optimus technology)
3. 4GB of RAM
4. Using Ubuntu 12.10 64-bit.

For the past day, I've been trying to get Bumblebee to run, since the NVIDIA card runs for no reason, generates heat and drains the battery rapidly. But I have been unsuccessful in doing so, after installing bumblebee and rebooting, after logging in, there is no sidebar no nothing on the screen, all I see is the wallpaper and the right-click menu works too. Here is what I have culminated by breaking and re-installing Ubuntu 8 times in hopes of getting bumblebee to run:
1. Install Ubuntu 12.10 64-bit
2. open up terminal and type "sudo apt-get update"
3. "sudo apt-get upgrade" (at this point I assume the linux kernel is also upgraded from  version 3.5.0.17 to 3.5.0.25)
reboot system
4. "sudo apt-get install linux-headers-generic" (required for NVIDIA driver installation)
5. "sudo apt-get install linux-source" (from my failed installation experiences I learned that the driver compilation fails and requires the kernel source files so I added this step too)
reboot system
6. "sudo add-apt-repository ppa:bumblebee/stable"
7. "sudo apt-get update"
8. "sudo apt-get install bumblebee bumblebee-nvidia" (During the installation, it generates an error that Nauveu is still running, so to avoid this I do the following)
9. CTRL+ALT+F1 into shell and login
10. "sudo service lightdm stop"
11. "sudo apt-get install bumblebee bumblebee-nvidia" (This time the installation finishes)
12. "sudo service lightdm start" (Takes me to the login screen)
13. I login, and voila, no unity, no Compiz, all I see on the screen is my wallpaper and the right-click menu works too.
14. so I CTRL+ALT+T to open up a terminal window.
15. Type "sudo nvidia-xconfig" and it tells me no such command exists.
16. In a last ditch effort, I try and do this: "sudo dpkg-reconfigure nvidia-current" but this does not have any effect and a reboot at this point doesn't seem to help either.

I have already re-installed Ubuntu 8 times, please someone tell me what am I messing up that unity and compiz always break? all I'm left with is the desktop wallpaper

---

### Post by HasnainRaza on 2013-03-12
Bump.

---

### Post by HasnainRaza on 2013-03-13
Jesus H. Christ! Is there no one who can help?

---

### Post by HasnainRaza on 2013-03-13
Alright, So I managed to fix my problem, Turns out everything I did was correct, there was some stupid problem during bumblebee installation in which it removed the "ubuntu-desktop" package. After following the same procedure as above, my Ubuntu was broken (again, no titlebars, sidbars etc) so I opened up terminal shell through CTRL+ALT+F1, logged in and did "sudo apt-get install ubuntu-desktop". Restarted the computer and voila, everything works, unity loads up fine, glxspheres giving 130 fps with optirun, the graphic card is running much cooler now. For anyone else with this specific problem, this is the solution I guess.

---

