---
title: "Login loop after Nvidia driver install"
date: 2016-05-16
forum: General Help
---

### Post by vijaiharihar on 2016-05-16
I am using Ubuntu 14.04 on my Asus r510JX laptop with the following specifications:
Processor: intel i7-4720 HQ with integrated graphics
Graphics Card: Nvidia GTX 950M
I tried installing the Nvidia drivers by downloading from Nvidia website and manually installing but this led to a login loop.
Consequently, I uninstalled this driver by running ./NVIDIA* --uninstall. Still the login loop problem persisted.
Next I tried the following:
sudo apt-get purge nvidia*
and then tried installing nvidia-358 and nvidia-362 packages using apt-get.
However after trying both these drivers, still I have the same login loop problem.
I have already reviewed many similar posts and answers such as:
[http://askubuntu.com/questions/721633/nvidia-graphics-card-driver-installed-led-to-login-loop](http://askubuntu.com/questions/721633/nvidia-graphics-card-driver-installed-led-to-login-loop)
and
[http://askubuntu.com/questions/716942/login-loop-on-ubuntu-15-10](http://askubuntu.com/questions/716942/login-loop-on-ubuntu-15-10)
but to no avail.
Note: by using lspci I can see that the system is currently using the integrated graphics and somewhere I heard that it might be necessary to enable graphics card in BIOS. However in the UEFI firmware that I am using I see no option to enable graphics card.
Can someone please suggest a solution?

---

### Post by blaze24-matrix on 2016-05-16
Try to use an external monitor (VGA). See what's happening. Could be the screen resolution?

---

### Post by mcduck on 2016-05-16
You could try booting to UEFI menu and switching secure boot off. At least for me that fixed the nVidia driver (on Asus G51JM laptop with 960M GPU). I suspect there's some issue with the driver signing or something related. (Then again I didn't have this issue on 14.04 or any other previous Ubuntu version, it only appeared on 16.04, so your problem might be something different).

Also make sure you have nvidia-prime installed (and I recommend installing the prime-applet as well to make it easier to switch between Intel and nVidia GPUs)

---

### Post by mc4man on 2016-05-16
You likely should have never tried to use the Nvidia site drivers with an optimus machine. If you can't boot up to the intel iGPU then I'd start over. In that case probably better to  use either 14.04.1 iso or 16.04 iso. 

The best you may see by default  on 14.04.4 with repo or ppa nvidia drivers,  (nvidia-prime),  is a boot to a black screen. If you wish to use 14.04.4 & can get to that black screen then that can be worked around & also vsync can be enabled if desired. Note that a black screen is not the same as a login loop..

(- some hardware will also have issue on 16.04 with nvidia drivers. Here a skylake (i7-6500u/940m) can only use the 358 drivers, earlier & later all have the loop. The 358 work but only if the greeter screen is allowed to crash before any input, it then returns & all is well. In your case this isn't the issue.

---

### Post by Linuxisfast on 2016-05-16
If you need latest greatest use tried and tested graphics driver ppa and never the nvidia driver.

---

### Post by vijaiharihar on 2016-05-16
@mc4man, Thanks for the information. I haven't been able to get to the black screen that you mentioned. What I would like to know is: even after I get rid of all ppa nvidia drivers by executing "sudo apt-get purge nvidia*", the login loop persists. Why is that? I expected the nouveau driver to be used but it isn't being used. I was using the nouveau driver previously without any problems (except that I could not get any control over the brightness of the screen, which is why I decided to switch to Nvidia drivers in the first place). Can you suggest a way to get Ubuntu to use nouveau again and also to resolve the brightness issue?

---

### Post by vijaiharihar on 2016-05-16
@Linuxisfast, please note that I have already tried the ppa drivers and the problem persists.

---

### Post by Linuxisfast on 2016-05-16
> **vijaiharihar said:**
> @Linuxisfast, please note that I have already tried the ppa drivers and the problem persists.


Please try the ppa after fresh install and also you won't need Bumblebee, just use nvidia-prime

---

