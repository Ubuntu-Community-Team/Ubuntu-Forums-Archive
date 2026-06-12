---
title: "Lubuntu hangs on shutdown and reboot"
date: 2018-01-30
forum: General Help
---

### Post by bobnutfield on 2018-01-30
Hello Everyone,

This is an irritating problem because I can usually fix stuff like this with little problem.  It is usually related to the grub file I believe.

I have an old laptop that I had been running Ubuntu on for at least 10 years, upgrade after upgrade all the way to 16.04.  It had finally gotten so slow and had so little space on the / folder that I couldn't do anything.  It was time to make a change.  With the age of the laptop and specs (AMD64 with 2 GB memory), I backed everything up and decided to install Lubuntu.  Everything with the install went great and this old girl had some life again.  But, on the first reboot, the system hung at the first dot on the splash screen and the hard drive LED went silent.  I had no choice but the do a power button shutdown, which I know is bad.  My search for an answer led to a fix that was simply adding:

reboot=pci 

after the "quiet splash" line.  It had no affect, nor has anything else I have read.  Even shutdown -h now  from the terminal will hang.

Anyone got any ideas what I can try?  

Many thanks for any replies.

Bob

---

### Post by #&amp;thj^% on 2018-01-30
Have you used "**acpi=force**" instead of "**reboot=pci **"
Just remember to tell grub of the change with:
```
sudo update-grub
```

---

### Post by bobnutfield on 2018-01-30
Thank you for your reply.  I'll try that now and report back.

Many thanks,

Bob

---

### Post by bobnutfield on 2018-01-30
Hello

That doesn't work, either.  Same result.  I have found a number of posts on different forums regarding this same issue with Lubuntu on various brands of laptops.  This one is a Toshiba, but I have seen it with Acer, Lenovo and others as well.  I suppose it could be a bug in Lubuntu.  With all the issues I started having with Ubuntu, I never had this one.  

Many thanks for trying to help

Bob

---

### Post by #&amp;thj^% on 2018-01-30
We got us a stubborn one then have we?
See if this helps:
```
 sudo swapoff -a && systemctl poweroff
```
as a workaround for now.
Also  instructions described in the "Debugging boot/shutdown problems" section of /usr/share/doc/systemd/README.Debian.gz to check if there are any hanging jobs at shutdown.
You will need to start the debug shell prior to each shutdown or reboot by entering: systemctl start debug-shell Capturing a screen photo of journalctl -b in the rescue shell ctl+alt+F9 might be enlightening. Also the output of systemctl list-jobs and systemctl --failed Besides a screen shot you can dump the output of these commands and appended each into the same "filename.text" on / root by adding >>filename.text at the end of the commands e.g. journalctl -b >>filename.text journalctl -xe >>filename.text systemctl list-jobs >>filename.text systemctl --failed >>filename.text lsblk >>filename.text All of these will be in the same file appended together for you to analyze upon your next boot and if you do file a bug report it can be helpful to attach the file into your bug report.

---

### Post by bobnutfield on 2018-01-30
Thanks, you are very kind to help.  Unfortunately, that didn't work either, same result.  This is a fresh install, so before I damage my old laptop  by doing continuous power button shutdowns, I'm giving up on Lubuntu.  There are other lightweight distros out there that I will try.  I am considering giving Ubuntu Mate a shot, or possibly Bodhi, which I believe is also an Ubuntu derivative. 

Thanks you again for your kind efforts.

Bob

---

### Post by bobnutfield on 2018-01-31
Ok, I just installed Mint to try it and experienced the exact same issue.  I was previously using Ubuntu 32bit and never experienced this. I am convinced that it is an issue with the 64bit version on my laptop.  I am going to try the 32bit version this time to test it .  Anyone have any thoughts why this would occur only on the 64bit systems?

Bob

---

### Post by jaysprout on 2018-07-12
I recently converted to Lubuntu and experience the same thing. Previously, I was running the 64bit version of Ubuntu so I don't think that's it. My laptop is a 10+ years old Dell Vostro 1000. Other than this, I haven't experienced any problems.

---

### Post by julian4 on 2018-09-03
This may be a kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1594023](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1594023)

I have the same issue with an old Dell Vostro 1000 running Lubuntu 18.04, Kingston SSD, Linux kernel 4.15.

---

