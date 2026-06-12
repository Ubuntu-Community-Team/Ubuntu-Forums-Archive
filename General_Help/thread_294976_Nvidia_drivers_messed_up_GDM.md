---
title: "Nvidia drivers messed up GDM"
date: 2006-11-07
forum: General Help
---

### Post by Chrono86 on 2006-11-07
Hey guys
Just installed Ubuntu 6.10 on my AMD64 2800+ with a GF6600gt PCIeX. (but not using the 64bit version o/s). Anyways I follwed this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

to install the drivers and now when I boot up the pc gdm says it cannot start because it can't find any device instances, or something like that. What happened and how can I fix it?
Thanks
Adam

---

### Post by PriceChild on 2006-11-07
"or something like that".

Could you provide the exact error please?

---

### Post by Chrono86 on 2006-11-07
Here's the error output when X fails to start

> NVIDIA: No matching device section for instance (BusID PCI:5:0:0) found

No devices detected

Fatal server error:
no screens found

---

### Post by OffHand on 2006-11-07
Try to logout and press ctr+alt+F1 (or F2). Login and run:
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions.

---

### Post by Chrono86 on 2006-11-07
Ok I went through the configuration.

Now whenever I run 'startx' or boot up ubuntu it gives me an error message stating whatever color depth I had selected (whether it be 24 or 16...why would I choose any lower?) isn't supported by the driver...what's up?

Thanks

---

### Post by OffHand on 2006-11-07
What's the output of```
cat /proc/driver/nvidia/version
```

---

### Post by Chrono86 on 2006-11-07
I get a no such file or directory error.

It seems there is no 'nvidia' folder inside /proc/driver

---

### Post by OffHand on 2006-11-07
> **Chrono86 said:**
> I get a no such file or directory error.

It seems there is no 'nvidia' folder inside /proc/driver

Looks like you need to install the drivers properly.

---

### Post by Chrono86 on 2006-11-07
Not to sound rude, but I followed the directions exactly as stated on the Ubuntu guide...I am no beginer to computers or even Linux.

So how would I about installing the drivers from the prompt?

---

### Post by OffHand on 2006-11-07
> **Chrono86 said:**
> Not to sound rude, but I followed the directions exactly as stated on the Ubuntu guide...I am no beginer to computers or even Linux.

So how would I about installing the drivers from the prompt?

I'm just saying the drivers are not installed properly. Not blaming you for it  ;)
You could try the new released drivers by Nvidia or try reconfigure X one more time. The newest driver can be found here:
[http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html)
What's the output of:```
glxinfo
```

---

### Post by lazyart on 2006-11-07
Perhaps reconfigure X again but choose the nv (or worse case, vesa) driver.  That should get you to the GUI and you can use synaptic to hunt down the nvidia driver.

You can run the CLI version with sudo synaptic but it's a bit clunky.

---

### Post by Chrono86 on 2006-11-07
I realized I had been choosing VESA every time...trying NV resulted in an error...but choosing NVIDIA worked! Does this mean the drivers are now working? How would I test it?

---

### Post by OffHand on 2006-11-07
> **Chrono86 said:**
> I realized I had been choosing VESA every time...trying NV resulted in an error...but choosing NVIDIA worked! Does this mean the drivers are now working? How would I test it?

```
glxinfo
```

---

### Post by Chrono86 on 2006-11-07
Alright here's a weird issue. glxinfo does indeed show me the drivers are installed, but when I go to change the desktop resolution I only get 3 choices: 640x480, 800x600, and 1024x768...last time I used Ubuntu and installed nvidia drivers I had a lot more options than that...what happened?

---

### Post by digby on 2006-11-07
You have to add the lines for your resolution to your /etc/X11/xorg.conf file.  Mine was also messed up when I initially installed.

I believe that the dpkg-reconfigure xserver-xorg routine that you've been doing should have that option, otherwise, post your xorg.conf, and we'll see what we can do.

---

