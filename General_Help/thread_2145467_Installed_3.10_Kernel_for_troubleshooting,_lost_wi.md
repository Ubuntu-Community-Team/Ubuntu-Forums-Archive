---
title: "Installed 3.10 Kernel for troubleshooting, lost wireless driver. Expected behavior?"
date: 2013-05-15
forum: General Help
---

### Post by Roasted on 2013-05-15
I'm running 13.04 64 bit. In an effort to do some troubleshooting for an unrelated issue (brightness related with function keys) the dev on Launchpad suggested that I install the 3.10 RC1 kernel for Saucy. I did so, and now I lost wireless. I understand that by installing the STA driver, it compiled it into the current kernel that was in use. What's confusing is if I go into software sources > additional drivers, it still says that my Broadcom STA driver is installed and in use, but under Network Manager I have nothing wireless listed. 

Why is it that the driver is not available for the 3.10 kernel, despite saying it's installed and active?

Thanks for any insight!

---

### Post by Nolix on 2013-05-15
I installed 3.9.2 and lost wireless. So I'm guessing it's no different in the mainline.

---

### Post by Roasted on 2013-05-15
Are you running the Broadcom STA driver? Did you regain it on 3.9 at all?

---

### Post by Nolix on 2013-05-15
> **Roasted said:**
> Are you running the Broadcom STA driver? Did you regain it on 3.9 at all?

I am running the Broadcom STA driver, I didn't regain it I downgraded to 3.8 but since Eth0 is working you should try reinstalling the broadcom driver. [URL="http://askubuntu.com/questions/55868/how-to-install-a-broadcom-wireless-driver"]http://askubuntu.com/questions/55868/how-to-install-a-broadcom-wireless-driver


[/URL]

---

### Post by Roasted on 2013-05-15
Thanks. This still doesn't make any sense to me though. It seems as if the version available in the repos is newer than what Broadcom has on their own site in the downloads section. I'm being told that I need to compile the driver against kernel 3.10 so 3.10 can support it. At this point, I'm questioning why I can't activate the wireless card/driver from 3.10 in the same demeanor that I did with 3.8, aka, from the software sources > additional drivers menu. That menu does nothing, even if I remove, reboot, install, reboot, it does nothing, meanwhile it works perfectly in 3.8. On top of that, the version in the repos is newer, and it makes me wonder why I seemingly have to download the older version externally and use that for the newer kernel.

I'm sure I'm misunderstanding something, but as of now that's what I'm gathering. Is there not a more efficient way to add the driver for 3.10 the same way I added it for 3.8?

---

### Post by Nolix on 2013-05-15
[http://ubuntuforums.org/showthread.php?t=2145416](http://ubuntuforums.org/showthread.php?t=2145416)

Just figured you should see that. Apparently this mornings update fixed the driver with his broadcom on 3.9.2

---

