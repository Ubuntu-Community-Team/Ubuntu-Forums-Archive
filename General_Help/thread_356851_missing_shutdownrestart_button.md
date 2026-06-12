---
title: "missing shutdown/restart button"
date: 2007-02-08
forum: General Help
---

### Post by spartan777 on 2007-02-08
I have no shutdown or restart buttons. I can click the power button at the top right of the taskbar, but I can only log-off, lock screen, sw user, hibernate, or suspend. I reboot now by using the prompt. I am not running xgl or anything fancy at the moment (though I do have beryl installed) What might have happened?

~background~
I recently had some severe instability issues, and the day before I installed a junk-load of programs, so I started uninstalling a bunch of programs, thinking some rogue program was causing the instability. I know I accidentally uninstalled "Ubuntu-desktop" by accident, so I may have uninstalled other necessary programs (I also was missing my hibernate and suspend buttons, but installing ubuntu-desktop brought those back). Eventually I realized the instability was due to a little bit of overclocking I had done a few hours earlier, and that I uninstalled a bunch of programs in vain, but I am still missing my beloved power-off and restart buttons!

thanks for helpl in advance.


~this does not help~
sudo dpkg-reconfigure acpi-support && sudo dpkg-reconfigure acpid
 and again, I am not currently running xgl.

---

### Post by scrooge_74 on 2007-02-09
Check this thread [http://ubuntuforums.org/showthread.php?t=244662](http://ubuntuforums.org/showthread.php?t=244662)

---

### Post by spartan777 on 2007-02-09
thank you, I don't know why I didn't find this thread before. Mackinax had the answer:

One possibility -

Menu: System > Administration > Login Window

In the "Local" tab of "Login Window Preferences", make sure that "Menu Bar: Show Actions menu" is checked.

---

### Post by Sunflower1970 on 2007-02-12
spartan777, I'm glad I found your post. My Restart/Shutdown buttons had disappeared on me yesterday afternoon...One of the things I did was go into my login window preferences to change my login screen (while doing other configuring as well). I must have  clicked to uncheck that box and never noticed.  :oops:

I'm just glad to have my buttons back now :)

---

### Post by spartan777 on 2007-02-13
yeah, I think either xgl, or beryl, or the Nvidia drivers must change this erroneously. I can't imagine why, it seems such a simple thing to fix.

---

### Post by sdil on 2007-02-13
you can click Ctrl+Alt+Backsapce

---

### Post by scrooge_74 on 2007-02-13
> **sdil said:**
> you can click Ctrl+Alt+Backsapce

Why do you want to just kill the Xserver instead of figuring out what is wrong?

---

### Post by likeatim on 2007-02-14
> **scrooge_74 said:**
> Why do you want to just kill the Xserver instead of figuring out what is wrong?
especially since it only kills the **session** (you end up at the login screen again) but doesn't reboot or shutdown

---

