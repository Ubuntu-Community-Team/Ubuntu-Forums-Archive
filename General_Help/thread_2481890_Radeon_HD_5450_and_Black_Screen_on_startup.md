---
title: "Radeon HD 5450 and Black Screen on startup"
date: 2022-12-12
forum: General Help
---

### Post by johnster001 on 2022-12-12
Good Day,
I'm moving to Ubuntu from Windows 10 as my Daily Driver Workstation and am having some issues with the graphics.  The computer I'm using has embedded graphics as well as an HD 5450 PCIe graphics card.  When I first installed Ubuntu, it worked fine, but occasionally on reboot it would just go to a black screen. After searching I found I could get it to load a basic display if I added "nomodeset" to the boot string, but that really didn't help.  I didn't really make any changes and after a few reboots it would load fine and has been working for a few weeks (and multiple reboots) without issue.  Recently, the system froze while I was changing my VPN settings and I had to do a hard reboot, and since then it consistently goes to a black screen after the OS starts to load.  The nomodeset thing still works and I'm convinced the problem is that the system is using the onboard graphics instead of the add-on card.  There is no BIOS setting that will allow me to disable the onboard graphics and at the moment I can only access the system by using nomodeset and booting into 720x480 display. Can anyone assist?

Thanks.

*EDIT* :
To test my theory about the onboard graphics, I booted the system then plugged my monitors into the embedded graphics connectors, they were completely dead.  My guess is that the BIOS disables the onboard graphics when it detects the graphics card, which clarifies things but still leaves me with the original problem, the black screen.  Help?

Can anyone assist?

---

