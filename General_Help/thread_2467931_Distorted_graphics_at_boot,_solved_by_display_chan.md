---
title: "Distorted graphics at boot, solved by display change"
date: 2021-10-13
forum: General Help
---

### Post by Happy Prancer on 2021-10-13
I have a brand new installation of Ubuntu 20.04. After booting the computer, the graphics and colours are distorted (see photo). The problem is already present on the login screen and persists after logging in. It can be solved by changing any of the display settings, and hitting apply. After the settings are changed, usually the graphics are normal. If I select "Revert settings" after that, it is still normal after reverting. I think the default display settings are okay, but there is some problem that gets fixed in the process of changing settings. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289273&stc=1[/IMG]

The Ubuntu installation USB did not have this problem.

The system has Intel HD Graphics and I'm using the Displayport on the main board to an HDMI TV using an active DP/HDMI adaptor. I had to put the TV into a non-HDR mode to see the BIOS display during set up, in case that's relevant.

I would like to make it so that the display is normal at boot so that I do not have to fix it every time I boot the computer.

Thanks!

[Edit: If the "blank screen" power saving mode is triggered, the problem comes  back and has to be reset by changing the display settings.]

---

### Post by axelmasok on 2021-10-13
You didn't mention that this exact pc+cabling+display setup works perfectly for months with xxxx.  Is this the case maybe?  I'd suggest you have to find a working baseline with any distro or OS even first and work out the difference from there.

---

### Post by Happy Prancer on 2021-10-13
> **axelmasok said:**
> You didn't mention that this exact pc+cabling+display setup works perfectly for months with xxxx.  Is this the case maybe?  I'd suggest you have to find a working baseline with any distro or OS even first and work out the difference from there.

The Adapter/cable/TV setup has worked for two years with a previous computer running Ubuntu 20.04. The computer was replaced and this is the result. 

So, the difference is the computer and there wasn't a display problem with the Windows setup screen, the BIOS screen, or the Ubuntu installation USB.

---

### Post by axelmasok on 2021-10-17
OK the key there is Ununtu Live setup works fine. So now you are chasing something with Xorg detection differs between the Live Setup and the final install. Boot the Live Setup and study the resolution and colour depth etc. Also grab a copy of the Xorg0.log so you can read through that too. Compare with your running install.

---

