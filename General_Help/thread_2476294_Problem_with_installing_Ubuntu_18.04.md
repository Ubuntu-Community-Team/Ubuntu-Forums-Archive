---
title: "Problem with installing Ubuntu 18.04"
date: 2022-06-22
forum: General Help
---

### Post by viadoloris on 2022-06-22
[COLOR=#000000][FONT=verdana]I install Ubuntu 18.04 from a flash drive on an hp laptop (intel i5, nvidia).The problem is that at the stages of choosing installation parameters, the transition to the next stage takes too long, when it reached the directory selection, waited more than an hour for the window to open, then everything completely hung up, but the flash drive started flashing. Before installation, the SSD on which I am trying to install was formatted.
The situation does not change when I prescribe nomodeset before installation, because many said that there could be a problem due to the video card.
I created the image through Rufus, chose MBR.

Maybe someone had such a problem, how can I solve it?
[/FONT][/COLOR]

---

### Post by TheFu on 2022-06-22
I've never seen this issue.  But standard, free, support for 18.04 server ends next April.  At this stage, it is time to choose a new LTS.  

If you are doing a desktop install, unless it is Gnome3 DE, support has already ended.  Standard support for gnome3 ends next April too.

Some flash drive don't work well (and probably never will) and some SSDs need firmware updates (and motherboard BIOS updates) to work.  I'd check for MB bios updates and new SSD firmware to be installed first.
Then I'd try a different flash drive and try different USB2 ports on the system.

BTW, these days, GPT is preferred over MBR for many reasons. I doubt that's the issue.

Does the flash drive work in "try ubuntu" mode?

---

### Post by oldfred on 2022-06-22
The newest versions of Ubuntu also allow you to select safe boot and choose optional restricted drivers, so the nVidia chip is correctly configured.

What model HP?

HP Elitebook 850 BootDevice Not Found,  then changed HP's boot mode options to "UEFI Native (without CSM)"
[https://ubuntuforums.org/showthread.php?t=2476147](https://ubuntuforums.org/showthread.php?t=2476147)
 HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790)
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)

---

### Post by yancek on 2022-06-22
Did you create partitions and format with a LInux filesystem prior to beginning the install?
Does this computer have any other OS on it?
Is it a GPT drive or MSDOS?

---

### Post by grahammechanical on 2022-06-22
Was this the Ubuntu 18.04 ISO image or the Ubuntu 18.04.6 ISO image? If your hardware is less than 5 years old then the original 18.04 ISO image may not have the hardware drivers for you hardware. Whereas, the 18.04.6 ISO image will have more up to date hardware drivers.

Otherwise I agree with the above suggestion to install either 20.04 or 22.04 rather than 18.04.

Regards

---

