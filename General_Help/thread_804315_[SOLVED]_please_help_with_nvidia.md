---
title: "[SOLVED] please help with nvidia"
date: 2008-05-23
forum: General Help
---

### Post by AndreiMe on 2008-05-23
i have a nvidia geforce fx 5500 and i'm trying to install the drivers for it. while in 7.10 this was a somewhat easy thing to do, i can't seem to get it right in ubuntu. downloading the driver and installing it from the console from the nvidia site didn't work. trying to use envy didn't work. actually envy doesn't work. and then there are all the methods from websites that just didn't do the trick.
is there a complete manual or something like that for ubuntu 8.04. any help would be greatly appreciated.

---

### Post by Nepherte on 2008-05-23
Could you tell us an overview of the methods you used and what specific errors you got?

The most generic way to install the video drivers is to download them from the nvidia site. The version you'll want is 169.12

Switch to another console: Ctrl + Alt + F1 and login

I'm not sure if you'll need it, but it won't harm. Let's install build-essential:
```
sudo apt-get install build-essential
```

Stop GDM:
```
sudo /etc/init.d/gdm stop
```

Navigate to the directory where you downloaded the driver with the cd command
```
cd <directory>
```

Make the file executable: 
```
chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```

Run the installer:
```
sudo sh NVIDIA-Linux-x86-169.12.pkg1.run
```

Restart gdm:
```
sudo /etc/init.d/gdm start
```

---

### Post by atomkarinca on 2008-05-23
I have the same video card and installing it via Hardware Drivers works perfectly for me.

---

### Post by AndreiMe on 2008-05-24
i followed the steps and the second time they worked just fine.  thanks

---

