---
title: "Asus UX31e randomly crashes when power is lower than 50%"
date: 2015-08-07
forum: General Help
---

### Post by julius-a on 2015-08-07
Hi all!
I'm new to the ubuntu forums, so I hope this is the right place to post this.
I own an Asus UX31e Ultrabook (Intel® Core™ i5 2557M Processor) and used ubuntu 14.04 as my primary (and only) operating system on this machine (since half a year I switched to elementary OS freya, but it is based on ubuntu 14.04).
I really love to work with this ultrabook, but there is one very annoying bug that affects my system when the power gets below 50%: it sometimes randomly powers off. This happens as abruptly as a poweroff caused by a power cut. However it does not happen when the AC connector is plugged in. 

I've tried it to fix it since I observed the issue the first time - I started with adjusting the boot parameters, because I read that some people solved the issue by adding the line "i915.semaphores=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, but in my case it didn't change anything. I also tried another fix, for which I unplugged the battery connector for about 10 minutes and then plugged it back in - but this also didn't affect the system's stability. The last thing I did was recompiling the kernel with a fixed DSDT (which I extracted and recompiled after fixing errors), unfortunately this had no effect as well. Checking /var/log/syslog also gives no useful information, because the system powers off too fast for the syslog to realize (no recurring logs at the time of the poweroff).

Even though I couldn't fix the issue, I made some observations which let me believe that it is a software related problem. When the power is below 50% and I stay at the login screen without logging in, no sudden shutdown happens. I can also stay in tty screen without any problems (until the computer shuts down normally because of low battery). But in the moment I log in at the greeter and the normal UI session starts my system gets unstable and the issue occurs again. I also do not have any problems when the system is booted into the graphical session after resuming the boot from recovery mode (in this mode the graphics modules are not fully loaded, so the resolution is low). I don't have enough knowledge about the login process, but I guess the problem has to do with some specific part of a graphics module which gets loaded when I log in. The problem is not related to high cpu temperature, because it also happens when the Ultrabook is cold (just booted up after hours of not using it).

So I wanted to ask if someone knows what could be the cause of this strange phenomenon. I know that I didn't provide a lot of information, but maybe someone already had a similar issue on a different machine and remembers how to fix it, or knows which software component could cause such a behavior. Thanks in advance!

---

### Post by QDR06VV9 on 2015-08-07
I had a friend that i installed 14.04 on his Asus UX31e but with the i7 Cpu.
He also complained of sudden shut-downs, albeit he was not as informative about his description of his problems.
But after many hours trying one thing after another, Due to the touch-pad they elected to  to install(Mediocre at best not trying to sound cheeky here)
What worked was I had installed another non-stock kernel I believe it was a 3.19 version from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.8-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.8-vivid/)
Normally it not well advised to offer such advise but reading your post I feel you are capable of handing that.
I am currently running  4.1.3-040103-lowlatency on Trusty(14.04.03) and Loving it.
If not post back and I can guide through it.
Or maybe someone else will have a better solution.
Kind Regards

---

### Post by julius-a on 2015-08-11
Thank you for your fast response! Great to hear, that there are solutions for this problem out there. I would really appreciate it if you could guide me through the installation steps (if they are not just installing the 64-bit linux-image* and linux-header* files).
Regards

---

### Post by QDR06VV9 on 2015-08-11
Well yes it is that easy, just install the debs!
Just not enough time in the day to Hand Compile anymore.LOL
Just in case I will show you how i do it.
1.Make a file in your Home Directory and name it kernels.
2.Go to this site [http://kernel.ubuntu.com/~kernel-ppa/mainline/n](http://kernel.ubuntu.com/~kernel-ppa/mainline/n) and choose the kernel that you want to install(Click on it)
3.Now make sure you pick linux-headers && linux-headers all &&
linux-image, 

[IMG]http://i.imgur.com/7xNNZ2r.png[/IMG]
Download them to your new folder "kernels"
4.Optional: but probably the wiser thing thing to do Is Un install any Non Free Drivers like Nvidia, and AMD or ATI.
Side Note I have not had any Problems with keeping the Drivers stated in the above installed unless It was in the early stages of Development of the kernels IE RC1 77 RC2 etc etc.
Once you are ready to install the new kernel, Fire your terminal up and type in
```
cd kernels
```
 ##This will take you to new kernels Folder in your home directory.
 Great now enter in terminal
```
 sudo dpkg -i *.deb
```
Then just to be safe
```
sudo update-grub
```
 Let it work it's magic and Reboot to your new kernel.
 After logging in you then can install all your drivers again.
If you have Issues with the new kernel you can always Select the last know working kernel from grub.
To Un-Install the kernel just use synaptic to un-install all 3 Debs
 Best of luck Hope you are as lucky as my Crony.
 Regards

---

### Post by julius-a on 2015-08-11
Thank you for these detailed instructions. I followed the steps, and uname -r shows me the expected kernel version: 3.19.8-031908-generic . Unfortunately this didn't fix the issue- a short time after I left my laptop unplugged to see how stable the system runs it powered off again without any warning :(

---

### Post by julius-a on 2015-09-15
Dear runrickus,
I recently upgraded my system to Ubuntu 15.04 (no Elementary OS, just a clean new install) which runs on the kernel 3.19.0-28-generic you recommended. I just wanted to report that my laptop didn't show a sudden shutdown since more than a week, so I'm really optimistic that this finally solved the problem. Thank you once again for your help!

---

### Post by QDR06VV9 on 2015-09-15
> **julius-a said:**
> Dear runrickus,
I recently upgraded my system to Ubuntu 15.04 (no Elementary OS, just a clean new install) which runs on the kernel 3.19.0-28-generic you recommended. I just wanted to report that my laptop didn't show a sudden shutdown since more than a week, so I'm really optimistic that this finally solved the problem. Thank you once again for your help!
That is great! Could not figure out why it did not work for 14.04 until I just noticed this "Elementary OS"
But I am happy that got sorted out for you, Thanks for replying back with the good news.
Kind Regards:D

---

