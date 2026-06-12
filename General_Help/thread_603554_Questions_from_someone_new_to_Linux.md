---
title: "Questions from someone new to Linux"
date: 2007-11-05
forum: General Help
---

### Post by JimmyK377 on 2007-11-05
Successfully set-up dual boot with a pre-installed copy of vista on Acer Aspire 5920g at long last :) thanks for people here's help.

Now just a few questions to clear up where to go from here.

1. I was unable to set up the internet until after i installed ubuntu, hence it couldn't connect to security.ubuntu.com during the installation, how do I set up the security updates now I have a connection?
2. I want to enable the enhanced graphics, but it says that I need to enable drivers, which it doesn't seem to have. My card is a GeForce 8600M GT.

---

### Post by jespdj on 2007-11-05
Which version of Ubuntu did you install?

Note that the nVidia 8600M GT is a very new video card; if you installed a version of Ubuntu older than the most recent (7.10) then a driver might not be included.

My laptop has an nVidia 8400M GS, which is the "smaller brother" of your 8600M GT. After installing Ubuntu 7.10 I got a message to enable the restricted driver, which I did with a few mouse clicks. The driver is for all Gefore 8 series cards, so it should work without a problem with your video card too. What exactly do you see, and do you get an error message, if so, then what's the exact error message?

---

### Post by JimmyK377 on 2007-11-05
The software source for the package
nvidia-glx-new
is not enabled.

is the message I get after trying to turn on the enhanced visuals, then clicking 'enable' for the driver.

---

### Post by JimmyK377 on 2007-11-05
and I'm running Gutsy I forgot to mention

does anyone have any advice about the drivers or the security stuff?

---

### Post by mig5 on 2007-11-05
Go to start -> System -> Software Sources
Once you have typed in your password and the program has loaded, tick the 'restricted' box in the Ubuntu Software tab.  Press reload when you are prompted on closing the program.
You should now be able to install the nvidia drivers via the restricted drivers manager.

---

### Post by mig5 on 2007-11-05
For the security updates, you should be able to get them by going to System -> Update Manager.

---

### Post by JimmyK377 on 2007-11-05
Rightho, that's all sorted thanks :)

My only other issue is that I adjusted the screen and graphics settings since they weren't spot on. and now the login screen displays at a lower resolution than after I've logged in. The sudden change seems to wrong foot the desktop as it liberally spreads some buttons across the top and bottom panels. Any ideas how to stop this?

EDIT: Actually I think that's probably here:
[http://ubuntuforums.org/showthread.php?t=595073](http://ubuntuforums.org/showthread.php?t=595073)

---

