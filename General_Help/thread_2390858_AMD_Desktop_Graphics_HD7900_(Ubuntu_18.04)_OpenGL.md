---
title: "AMD Desktop Graphics HD7900 (Ubuntu 18.04) OpenGL"
date: 2018-05-03
forum: General Help
---

### Post by jonesyp on 2018-05-03
I always seem to struggle with graphics cards on Linux.

I'm using a desktop PC with an AMD HD7900 graphics card.  I understand that the AMD open drivers are included by default.

The issue I am having is that if I run visualisation software such as VMWare Player (So I can run Windows in a VM), I get a message to say that OpenGL is not enabled.

I did some research before asking here, and tried installing mesa-utils, but it did not seem to make any difference.

Is there a place to go for up-to date graphic card information and what to do in each situation?

I'm trying finally to make the swap from Windows to Ubuntu as my daily driver, but need to run certain Windows applications natively.

Thanks in advance.

Peter

---

### Post by Claus7 on 2018-05-03
Hello,

I was not aware that VMWare Player is a hypervisor like VirtualBox. My card is an ATI Radeon HD 5670, which I suppose is similar to your case.

In order to check your OpenGL version type:
glxinfo | grep "OpenGL version"

and I get:
OpenGL version string: 3.0 Mesa 18.0.0-rc5

and using VirtualBox I have no complaints. 

So you could check if openGL is enabled in general, then you could use VirtualBox without complaints. Since you are aware about the opensource amd drivers, then you should be aware that 14.04 (if I'm not mistaken) is the last version of ubuntu supporting the closed source ones, so you might concider going back to 14.04.

In addition you could check this option as well:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Regards!

---

### Post by jonesyp on 2018-05-03
Hello and thanks for the quick reply. Are you on a fresh install of 18.04 Final, and have you installed anything else such as mesa-utils, or did you just install VirtualBox and it worked?

Thanks also for the link. I will read through that when I'm back home.

Thank you.

---

### Post by Claus7 on 2018-05-03
Hello,

no, it's not a fresh install. I have been upgrading from 14.04. VirtualBox did not work initially out of the box (when I upgraded 18.04 was still in alpha version). I had to uninstall the version of VB I had at that time and during the beta phase of 18.04, I installed version 5.2.8 and it worked as it used to.

I did not install anything inbetween, appart from what the updates required. Checking my history from synaptics I can see the following:
i) mesa-utils were installed way back using 14.04
ii) there was an upgrade from mesa-utils (8.3.0-5) to 8.4.0-1 during the upgrade to 18.04 (this February).

Hope it helps,
Regards!

---

### Post by jonesyp on 2018-05-03
OK, so I installed the PPA and did a sudo apt-get update and a sudo apt-get install mesa-utils. OpenGL version is 18.2.0-devel.

However from my visualisation software I still get No 3D support available on host and hardware graphics acceleration is not available. I was a bit confused with the PPA instructions, am I supposed to install something extra to make things talk? Thanks in advance.

---

### Post by Claus7 on 2018-05-03
Hello,

it seems that is vmware issue then. How about this link?
[https://ubuntuforums.org/showthread.php?t=2368057](https://ubuntuforums.org/showthread.php?t=2368057)

Regards!

---

### Post by jonesyp on 2018-05-04
Thank you Claus, I think you may have hit gold there!  I will try this over the weekend and report back.

---

