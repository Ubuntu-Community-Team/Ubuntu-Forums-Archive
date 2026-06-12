---
title: "Black screen, can't do anything"
date: 2008-04-07
forum: General Help
---

### Post by fallenmink on 2008-04-07
First off I am a total noob at Linux so please go into detail if at all possible.

I've been having quite a few problems with my laptop running Ubuntu(significantly less then Vista though may I add), specifically one about it not recognizing my graphics card, I used a tutorial on-line to try and get the card working completely and when I rebooted my computer I get my BIOS then the grub launcher then nothing, 

And now I know it isn't just taking a long time to boot(I let it sit for over an hour just to make sure for myself) so please any help would be amazing, and please let me know if more information is needed.

---

### Post by warp99 on 2008-04-07
What tutorial did you use? Maybe we have to undo some damage.

---

### Post by fallenmink on 2008-04-07
> **warp99 said:**
> What tutorial did you use? Maybe we have to undo some damage.

It was just a generic support site, unfortunately on this computer I don't have it in my browsing history but it was something along the lines of this: [http://www.linuxforums.org/forum/ubuntu-help/110698-ati-video-card-install-guide.html](http://www.linuxforums.org/forum/ubuntu-help/110698-ati-video-card-install-guide.html)
except I believe one of the steps was to delete something(unsure of what it is, sorry) and then to restart to continue, which is where I am now

---

### Post by warp99 on 2008-04-07
Did you install the drivers from ATI, i.e. method 2? What model of ATI video card do you have? Also can you boot into recovery mode, that is when Grub is loading press escape, and choose the second line marked 'recovery mode'? And finally what is the resolution you want you screen to be, ie 800x600, 1024x768, 1280x1100.

---

### Post by fallenmink on 2008-04-07
> **warp99 said:**
> Did you install the drivers from ATI, i.e. method 2? What model of ATI video card do you have? Also can you boot into recovery mode, that is when Grub is loading press escape, and choose the second line marked 'recovery mode'? And finally what is the resolution you want you screen to be, ie 800x600, 1024x768, 1280x1100.

Im on a Radeon X1200, Yes I can boot into recovery mode, no I did not install the drivers because I can't go any further, and my resolution I'm not sure exactly but I think it's 1024x768

---

### Post by Nameless_one on 2008-04-07
You should run this on the recovery console:
```
sudo dpkg-reconfigure xserver-xorg
```

When asked for the driver, choose vesa. If I hacve understood it correctly, it is the simplest driver available, with the less features, and will work for all cards. Then, reboot and the GUI will probably work. Then, try to install the fglrx driver from the repositories. 
If you have to install the restricted driver from ATI, use this guide, it's almost official:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

The one you linked at was very old.

---

### Post by fallenmink on 2008-04-07
Woohoo, thank you so so much it works now, you guys are great :D

---

### Post by warp99 on 2008-04-07
> **fallenmink said:**
> Im on a Radeon X1200, Yes I can boot into recovery mode, no I did not install the drivers because I can't go any further, and my resolution I'm not sure exactly but I think it's 1024x768

Boot into recovery mode first, make sure you have an internet connection, then enter the following:

```
apt-get install --reinstall xorg-driver-fglrx linux-restricted-modules-generic
```

once that is finished run the following:

```
dpkg-reconfigure xserver-xorg
```

Now when you reset you xorg.conf display choose the driver 'fglrx' and when you get to the monitor portion choose the resolution 1024x768 as the highest resolution you want. That means remove all of the resolutions **ABOVE** 1024x768.

Then enter the following:

```
nano /etc/usplash.conf
```

if nano is not installed then enter:

```
apt-get install nano
```

change the resolution to match yours so it looks like this:

```
# Usplash configuration file
xres=1024
yres=768

``` 

Save the file, crtl-o, then exit, crtl-x, and enter the following:

```
dpkg-reconfigure usplash
```

This will generate a new initrd.img file with the correct settings for your boot splash. When everything is complete just enter 'reboot' and you should be ready to go.

---

