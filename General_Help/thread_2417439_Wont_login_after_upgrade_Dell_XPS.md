---
title: "Wont login after upgrade Dell XPS"
date: 2019-04-23
forum: General Help
---

### Post by andrew80 on 2019-04-23
Hi All,

I'm not a power user so looking for some help, I have a Dell XPS 13 9370 which came installed with Ubuntu LTS, however I have upgraded it several times with the non-LTS versions. Today I have done the upgrade from 18.10 to 19.04 through the software updater.

Now it gets as far as the login screen, enter password and enter then the screen goes black and then comes back to the login screen.

Graphics card is Intel UHD 620 and its the Intel core i7 version. 

Anybody help me to get back into my laptop?

---

### Post by andrew80 on 2019-04-23
Have tried installing LightDM and using that instead, that still doesn't work.

---

### Post by oldfred on 2019-04-23
Not sure if this would help?
        i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer 
    
Or this which was for older version of Ubuntu.
       Dell XPS 13 What to fix with the fresh factory Ubuntu 16.04 April 2017 Updated to 18.04
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)

Is UEFI latest version from Dell?
Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)

---

### Post by andrew80 on 2019-04-23
Turns out its my user account that is knackered, created a new user account from terminal and that works fine. 

Any idea how to force my old user account to use the same settings as new user account to allow it to login?

---

