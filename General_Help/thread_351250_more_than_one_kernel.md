---
title: "more than one kernel?"
date: 2007-02-01
forum: General Help
---

### Post by chris103549 on 2007-02-01
Hi.

I have been running dapper for awhile and about 3 weeks ago upgraded to edgy. Everything works great but I get random lockups. The machine will hang for no apparent reason. There are no log messages and only a hard reboot brings me back.

I have an nvidia card so I thought maybe that was the problem. It doesn't seem to matter which driver I use. 

I cannot reproduce the problem and I never know when it's going to happen. I wonder if anyone else is experiencing this?

I had the thought that maybe I should compile a new kernel or something? I'm not sure how to do this and I don't want to overwrite anything. Can I compile a new one and then decide through grub which one to boot up? I'm sure the answer is yes but I'm not sure how to go about it. 

Any help would be appreciated!

---

### Post by pseudonym on 2007-02-01
Have a look in /var/log/syslog for messages produced at the time your system locks up. There may be something there which sheds some light on your problem.

If you want to build your own kernel [this]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile") is the thread you need to read. But you may not need to go this far yet...

---

### Post by chris103549 on 2007-02-02
Thanks for the reply.  Nothing is written to any logs (that I can see). The whole machine just hangs... 

I did notice today that if I pull up a semi-long webpage in firefox and use my scroll button (logitech usb wireless mouse) to scroll the page up and down really fast, I have a good chance of the machine hanging... I tried this a few times and it locked up both times after maybe 5 seconds of fast scrolling. But this could mean nothing since it hangs other times too. :)

Should I try a new kernel?

---

### Post by teaker1s on 2007-02-02
if your processor is single core AMD, you may find k7 kernel is better than 386i:KS

---

### Post by pseudonym on 2007-02-02
Is the nvidia graphics driver properly installed? Check /var/log/Xorg.0.log to verify it's being loaded and used when you start X...

---

### Post by chris103549 on 2007-02-02
Hi!

My cpu is an amd athlon 1.4ghz, so maybe running that k7 kernel would be better?

Also...

From /var/log/Xorg.0.log:

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7184
        Module class: XFree86 Video Driver

---

### Post by pseudonym on 2007-02-02
> **chris103549 said:**
> My cpu is an amd athlon 1.4ghz, so maybe running that k7 kernel would be better?
By all means, install the k7 kernel, but the difference between it and the 386 kernel is not so great that one would cause your system to lock up.

> **chris103549 said:**
> (II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7184
        Module class: XFree86 Video Driver
7184 is the legacy nvidia driver. I assume you have a legacy nvidia card as per [this list]("http://www.nvidia.com/object/1.0-7184_supported_products.html")? If not, then uninstall the legacy driver and install the current version driver.

Failing that I would consider re-installing Xorg, which is not as big a deal as it sounds. First, uninstall the nvidia driver completely, then - ```
Press Ctrl+Alt+F1 to drop to a console
Log in
sudo /etc/init.d/gdm stop
sudo apt-get --reinstall install xserver-xorg xserver-xorg-core xserver-xorg-dev
re-install the nvidia driver by your chosen method
sudo /etc/init.d/gdm start
```
HTH

---

### Post by chris103549 on 2007-02-03
Yes, my video card is on that list.

I think I will try reinstalling xorg, but will that overwrite any of my settings? Just curious.

Thanks alot for your help.

---

