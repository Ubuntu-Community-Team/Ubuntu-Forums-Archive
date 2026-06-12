---
title: "New Hardware support: Now problems"
date: 2014-07-16
forum: General Help
---

### Post by Robbyx on 2014-07-16
I was running the upgrade manager in 12.04. I noticed that there was an invitation to install some new hardware support and so I went ahead.

Rebooting is now a problem:

If I reboot using the normal hd sda: method I get an error message that a partition does not exist (it is the system partition). I do not know how to recover it at this stage and I can not proceed other than into busybox.

I tried the repair mode grub option, but could not get to the menu options. The screen hung. 

IF I run the liveCD but use the option to start from the first HD, after some error messages that I ignore I seem to be able to get into my normal 12.04 system. All HD partitions  are present and viewable.


in order to get an up todate image of the drives I tried booting off  clonezilla, it could not see my USB 3 portable HD so I could not clone any drives because only the HD drives were available and 
I will cause trouble if i try to send an image to a drive that is being cloned. 

What should I do next?

Robin

---

### Post by kc1di on 2014-07-16
I think I would run boot repair fist before doing anything else see if it will fix grub for.
pay attention to the webpage it gives you at the end of the run and post it here so we can look at the out put if it does not work. 
you can get boot-repair [here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Robbyx on 2014-07-16
thank you for your response. I have followed the standard advise for boot repair and it has not corrected my problem.
[http://paste.ubuntu.com/7805303](http://paste.ubuntu.com/7805303)

When I go into the live cd and choose the start from first HD, it initially fails and exits me from the start up process. If I then type EXIT it restarts and then boots into ubuntu.

The error message on the boot up process is /init: line 252 wait for root device, not found: gave up waiting.

 I have found that if I go back to the prior linux of  3.8.0-42-generic  the boot process does not fail and I do not need to use the live CD.

---

### Post by kc1di on 2014-07-17
it seem like there may be a kernel module missing of corrupt I have no Idea why, you may want to revert to the old kernel and try reinstalling the newer one.
See if it builds the module correctly this time. 
Good luck ;)

---

### Post by Robbyx on 2014-07-18
Thank you.

---

