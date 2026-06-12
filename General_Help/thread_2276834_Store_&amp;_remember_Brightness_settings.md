---
title: "Store &amp; remember Brightness settings"
date: 2015-05-05
forum: General Help
---

### Post by Mel_Blakey on 2015-05-05
Believe me, I have searched this issue many times over the last month. But, I can not get Ubuntu to save the brightness settings. Volume & other settings don't reset themselves, so why does the brightness keep reverting to maximum?
It seems to take advantage of any opportunity. It wouldn't be so bad if I just had to set it when I 1st boot up. But having to reset it everytime the machine wakes up is getting a bit tedious.

Ubuntu 14.04 64bit
HP Compaq Presario CQ57
Graphics: Intel® Sandybridge Mobile

I tried this [http://www.maketecheasier.com/configure-screen-brightness-in-ubuntu/](http://www.maketecheasier.com/configure-screen-brightness-in-ubuntu/) no luck!

Any help? Thanks....

---

### Post by dino99 on 2015-05-05
maybe you need to add that grub parameter:  acpi_osi=Linux  
[http://ubuntuforums.org/showthread.php?t=1802755&page=3](http://ubuntuforums.org/showthread.php?t=1802755&page=3)

---

### Post by coffeecat on 2015-05-05
First thing. The author of that link is generalising from the particular when he says:

> If you have noticed, no matter which level you have adjusted the screen brightness to, on the next reboot, the brightness level will go back up to 100%. This is probably a bug that Canonical has not get around to solve.

That is true only for some hardware. I'm lucky in that my Toshiba Qosmio desktop and Acer Aspire laptop both remember my brightness setting between boots. They both have Intel graphics, and I notice you do too, so that is unlucky for you.

Did you try xbacklight as recommended in your link?

Alternatively, I found this:

[http://askubuntu.com/questions/327040/how-to-permanently-set-screen-brightness-level-in-ubuntu-12-04-on-dell-vostro-24](http://askubuntu.com/questions/327040/how-to-permanently-set-screen-brightness-level-in-ubuntu-12-04-on-dell-vostro-24)

However, the relevant path to my brightness file is /sys/class/backlight/intel_backlight/brightness, not /sys/class/backlight/acpi_video0/brightness. Check what the path to brightness is in your system and that might be worth a try. Except, don't use "sudo gedit /etc/rc.local" to edit rc.local - that's bad practice. Use "sudo -H gedit /etc/rc.local" or install the package gksu and run "gksu gedit /etc/rc.local" instead.

---

### Post by Mel_Blakey on 2015-05-05
Thank You** dino99 **&** coffecat**

I found the fix mentioned on my search but couldn't find the file '/etc/rc.local' on my system.

I didn't know that I had to use 'sudo -H gedit' (*I am new to this*!) and now that I have it seems to have made a difference.

Thanks!

---

### Post by coffeecat on 2015-05-05
I'm not clear. Did the askubuntu link help? Did it fix your issue? It would be useful to know for other HP Compaq Presario CQ57 users.

/etc/rc.local would be on your system however you invoke gedit. The use of sudo alone with graphical applications is not recommended and I was simply picking up on an error in an otherwise well-documented solution.

---

### Post by Mel_Blakey on 2015-05-10
> **coffeecat said:**
> I'm not clear. Did the askubuntu link help? Did it fix your issue? It would be useful to know for other HP Compaq Presario CQ57 users

[COLOR=#000080]**YES! It has fixed the issue.** The settings are saved both on reboot and when the lappy resumes from standby/sleep.[/COLOR]

Sorry for the delay, but I wanted to give it a few days before I marked it solved.

Also, thanks for your explanation. It is *really* helpful to people on a learning curve, like me!

---

### Post by pmi2 on 2015-05-10
@coffeecat:  I was able to find a workaround for my laptop brightness thanks to the link you posted also.  

It is a new/(used) HP Elitebook 8560p.  No Intel Graphics, I have the AMD Radeon HD 6470M which was standard for this older laptop (just posting this to note that in general, this works for other than Intel graphics, and other laptops).

The name of the directory where the brightness settings file is located is different for me (but still under /sys/class/backlight...).  I also have the added complication of an ALS (ambient light sensor).  

ALS does not seem to work the same in Ubuntu and in Windows, so the only solution I have found so far is to just disable it.  Aside from the ALS, the brightness adjustment via the function keys, or through System Settings work correctly from a default Ubuntu 14.04 install.

---

