---
title: "nVidia drivers remove the sidebar"
date: 2013-04-27
forum: General Help
---

### Post by PureTryOut on 2013-04-27
I've just installed a fresh copy of Ubuntu 13.04, it's the only OS on this Laptop.
I just got it back from repairs, and I was installing everything I need in Ubuntu.

Everything worked correctly, until I tried to install the nVidia GeForce drivers.
I have a GeForce GT 540M and I tried installing driver version 310.44 64-bit, UK edition.

I correctly installed it via text mode, and I rebooted fine. Then, after I entered my password, the desktop shows up, but not the sidebar and the topbar.
I can do everything I normally do on the desktop, but the sidebar is just not showing up, which means I can not launch any applications (not even a terminal).
Also the top bar is missing, which means I have to force restart my laptop by pressing the power button or use "sudo shutdown -r now" via text mode.

What is going wrong here? When booting into text mode, and starting Unity via the command "sudo unity", it said it failed to load OpenGL plugin or something.
In the install nVidia asked me if I wanted to install 32-bit OpenGL librairies (or something, I can't really remember), and I just answered yes. Is that the problem?

Thanks in advance.


**Edit: **Fixed
Since the GT540M is an Optimus card, I had to install Bumblebee. Later on I found a package called nvidia-prime, which works even better, I suggest you should try that if you have the same problem.

---

### Post by pqwoerituytrueiwoq on 2013-04-27
the current 3.8.0-19-generic kernel does not like nvidia, i suggest using the mainline kernel until it is fixed
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

sounds like you installed the driver from nvidia's website, after a kernel upgrade you will have to reinstall it every time
to remove it run [FONT=courier new]sudo nvidia-installer --uninstall[/FONT] to install the driver so it does not require reinstalling run [FONT=courier new]sudo apt-get install nvidia-313-updates[/FONT]

---

### Post by PureTryOut on 2013-04-27
I guess I just installed the kernel you suggested, how can I check I actually installed it? Is there some kind of command I can run?
I want to make sure everything goes right so I don't have to reinstall Ubuntu again.

---

### Post by pqwoerituytrueiwoq on 2013-04-27
[FONT=courier new]uname -r[/FONT] will tell you what kernel is running, the system default is the highest version number installed, selected at boot

---

### Post by PureTryOut on 2013-04-27
[FONT=arial]OK so that did not work, I installed the new kernel, rebooted, checked the version using "uname -r", it was a different (and a newer) version of the kernel before the update.
Then i've ran "sudo apt-get install nvidia-313-updates", rebooted, and again the same bug, but this time, even the resolution was low.

I really need the graphics card to work :/
Had to reinstall Ubuntu, because uninstalling the graphics driver didn't work. Also, your command to uninstall didn't work because "nvidia-installer" was not installed? Tried installing it, but Ubuntu was not able to find the package.
[/FONT]

---

### Post by Giantmundo on 2013-04-29
I had the similar problem and found a suggestion that worked for me.

Open a terminal (ctrl alt t) and execute ccsm. This will bring up the Compiz Config Settings Manager. Scroll down till you see the Ubuntu Unity Plugin. Click on it and then disbale it by unticking the Enable Ubuntu Unity Plugin checkbox to the left. Then re-enable it and you should get a series of conflicts resolve. Answer the questions so that Unity gets what it needs and then you should be OK. You may have to logout and in again.

---

