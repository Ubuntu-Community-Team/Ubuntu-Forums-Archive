---
title: "Can't switch from Nouveau to proprietary NVIDIA driver"
date: 2014-09-13
forum: General Help
---

### Post by emakarov on 2014-09-13
Hello,

I have an old Dell laptop with the GeForce 8400M GS graphics card. After I installed Ubuntu 14.04, I discovered that the default Nouveau driver has problems with resume after suspend. Therefore, I used System Setings > Software and Updates > Additional drivers to switch to the proprietary NVIDIA driver version 331.38, which worked mostly fine; in particular, suspend worked. The other day I switched to Nouveau and back to NVIDIA to test some things. But even though the Additional drivers dialog says that I am using NVIDIA driver 331.38, the machine behaves like it is using the Nouveau driver: the NVIDIA logo does not flash during boot, and it does not wake up from suspend.

Could you tell how I can find for sure which driver I am using? Also, how can I switch to the proprietary driver?

If anyone can help with the suspend issue of the Nouveau driver, that would also be great because I am mostly happy with this driver otherwise. The problem is that though the screen comes on after resume, it freezes up and does not show any change: for example, it does not show the Wi-Fi indicator animation during the connection. Eventually the only thing I can do is to power-cycle the laptop.

Please tell me if you need more information and the commands I can use to get it.

---

### Post by deadflowr on 2014-09-13
```
sudo lshw -C display
```
will show you which driver is currently in use.
It'll say configuration: driver=Something
toward the bottom of the output.

---

### Post by emakarov on 2014-09-13
Thanks. "sudo lshw -C display" says "driver=nouveau". Any idea why switching to proprietary drivers in the Additional drivers dialog has no effect?

---

### Post by deadflowr on 2014-09-13
Do you have nvidia-xserver-settings?
It's an application in the menu.
Doing a quick search for nvidia should bring it up.
You can open it up, then go X display configurations and in the bottom right corner it should say save X configuration or something like that.This will generate an xorg.conf file.
When you reboot I think you should be using the nvidia driver.
Unless something else is wrong...

---

### Post by emakarov on 2014-09-13
I think the program is called nvidia-settings, but it shows as "NVIDIA X Server Settings" in the dash. When I ran it, it had only two options on the left, and "X Server Display Configuration" was not one of them. I don't quite remember those option, but one of them did have a Save button, so I used it. After that, the /etc/X11/xorg.conf file indeed appeared. I also did a complete removal of nvidia-331 package in Synaptic and then switched to NVIDIA 331.38 in Additional drivers again. One of these actions had an effect, and now lshw shows "driver=nvidia". Also, nvidia-settings shows more options on the left, including the "X Server Display Configuration".

I am just afraid to switch to nouveau again... The thing is that NVIDIA gives me a single resolution option, but nouveau gives me three, and one of them coincides with the resolution of the projector I am using, so this makes it possible to mirror displays. I hoped that I could use NVIDIA most of the time because it makes suspend work, but switch to nouveau to use the projector. If only the nouveau driver allowed suspend, that would be perfect. Do you know where I could ask for help with this issue or file a bug?

Thanks for your help.

---

### Post by pissedoffdude on 2014-09-13
That's a dilly of a pickle.  You should probably ask if there's a way to achieve this functionality with the binary nvidia drivers on their forums: [https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/)

Alternatively, feel free file a bug report on your suspend issue with the nouveau drivers (it's at the bottom left): [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

