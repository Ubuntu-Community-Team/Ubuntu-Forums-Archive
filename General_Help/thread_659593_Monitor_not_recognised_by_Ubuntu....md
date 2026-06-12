---
title: "Monitor not recognised by Ubuntu..."
date: 2008-01-05
forum: General Help
---

### Post by smartboyathome on 2008-01-05
I have an emachine d5239, and when I try to boot up to the Ubuntu 7.10 AMD64 DVD, the screen turns off just as the xserver turns on and when I move the mouse, it turns back on, but it is at the wrong resolution, and has all wrong resolutions available. On windows, I can get up to 1680x1050, but on the DVD I can only get 1280x1024, 1024x768, 800x600, and 640x480. Needless to say, the pixels are distorted on these resolutions, making Ubuntu look bad. Is there a way around this problem?

---

### Post by taurus on 2008-01-05
I take it you have not installed Ubuntu on your machine then.  What graphic card do you have?  Maybe you can reconfigure your X again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, you can restart X again with <Ctrl><Alt>Backspace.

---

### Post by dcstar on 2008-01-06
> **smartboyathome said:**
> I have an emachine d5239, and when I try to boot up to the Ubuntu 7.10 AMD64 DVD, the screen turns off just as the xserver turns on and when I move the mouse, it turns back on, but it is at the wrong resolution, and has all wrong resolutions available. On windows, I can get up to 1680x1050, but on the DVD I can only get 1280x1024, 1024x768, 800x600, and 640x480. Needless to say, the pixels are distorted on these resolutions, making Ubuntu look bad. Is there a way around this problem?

Try booting up using the "Safe Mode" (second menu option).

When you do a proper install then you can use drivers that may no be available on the live CD, so the video should work better.

Do you know what video chipset your machine has?

---

### Post by smartboyathome on 2008-01-06
I don't know the exact model, but I do know it is an NVidia card. Also, I will try installing from safe mode when I get a chance.

---

### Post by smartboyathome on 2008-01-12
Ok, I got time to try again (and found out it has an NVidia 6100 graphics card), and not even dpkg-reconfigure could get it to work. It couldn't detect the graphics card driver nor the monitor resolution, and when I set it to the nvidia driver (installed it using Restricted Driver Manager), and set the resolutions to 1680x1050, 1440x900, and 1280x800, and it still didn't work. Please help, I don't know if I will be able to stand using Vista much longer for Enemy Territory... :(

---

### Post by smartboyathome on 2008-01-13
*bump* Someone please help.

---

### Post by smartboyathome on 2008-01-16
Bump again. Seriously, this problem with the CD is starting to get on my nerves (along with Vista).

---

### Post by fedex1993 on 2008-01-16
install machine video card drivers thats what happened with my 22 inch monitor ubuntu didnt reconize it
and then i installed my nvidia drivers and now its more clear than i ever seen

---

### Post by smartboyathome on 2008-01-16
Like I said, I tried installing nvidia from the restricted driver manager and it didn't work. Maybe I should install it and try?

---

### Post by ubuntu-freak on 2008-01-16
Try here
 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
 
Give my multimedia how-to a go too
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

