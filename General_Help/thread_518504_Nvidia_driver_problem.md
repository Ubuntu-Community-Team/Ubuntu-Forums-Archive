---
title: "Nvidia driver problem"
date: 2007-08-05
forum: General Help
---

### Post by smmalis on 2007-08-05
I can't seem to install the nvidia drivers correctly.  I used Synaptic to get nvidia-glx.  Ran sudo nvidia-xconfig.  Rebooted.  Now I can't get any graphics, it boots into command prompt.  Any ideas?

---

### Post by maduranga on 2007-08-06
it is because something wrong with xserver.. "sudo dpkg-reconfigure xserver-xorg" and then reconfigure it. then try with envy

---

### Post by smmalis on 2007-08-06
I tried that and it said: unknown command dkg-reconfigure.

---

### Post by pxwpxw on 2007-08-06
sudo dpkg-reconfigure

---

### Post by smmalis on 2007-08-06
I did that, went through the whole config, and I still get errors when trying to startx.

---

### Post by simlu on 2007-08-06
> **smmalis said:**
> I did that, went through the whole config, and I still get errors when trying to startx.

What nvidia card exactly do you have? Try that:
```
 sudo scanpci | grep nVidia 
```

You may need to install "nvidia-glx-new" instead of the usual "nvidia-glx" package.

---

### Post by smmalis on 2007-08-06
I have a GeForce 8800 GTS, and x still wouldn't start.  I just reinstalled Ubuntu from my live CD, but I would like to be able to have the latest drivers.  Any ideas on how to do it so that it works?

---

### Post by simlu on 2007-08-06
> **smmalis said:**
> I have a GeForce 8800 GTS, and x still wouldn't start.  I just reinstalled Ubuntu from my live CD, but I would like to be able to have the latest drivers.  Any ideas on how to do it so that it works?

I checked for you and all you need to do is to install nvidia-glx-new package and your card should work fine. 

```
sudo apt-get install nvidia-glx-new
```

This will install the 9755 driver which supports your video card (nVidia 8800 GTS - [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html"))

---

