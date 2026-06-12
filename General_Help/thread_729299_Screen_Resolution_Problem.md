---
title: "Screen Resolution Problem"
date: 2008-03-19
forum: General Help
---

### Post by dlovley on 2008-03-19
Hello,

I am a brand new Ubuntu user. I have a triple boot system running xp, vista, and ubuntu. I have an intell quad processor and on board Intell graphics (brand new machine). When I installed Ubuntu the highest option for screen resolution in the list under preferences/screen resolution was 1280 X 800. I need at least 1280 X1024 for this monitor to look right. It's a Viewsonic A91f 19 inch display. Any help would be most appreciated. I have a cd with drivers that came with the computer for everything from the graphics to internet hookup. Can it be applied in linux? If not, what to do?

-D

---

### Post by dlovley on 2008-03-19
Disregard I figured it out. Thanks to anyone who read.

-D

---

### Post by mgmiller on 2008-03-19
You may have more luck posting this request in the hardware and laptops forum.  Unfortunately, I have no experience with intel graphics.  I do know, you will need to find out which graphics chip set you have and which driver you are currently using.  None of the drivers you have on the discs will be of any use.  They are probably windows only.  Any drivers you need should be easily installable through syaptic or apt-get.  

To get the graphics chipset:
```
lspci
```
should give you a list of hardware.  Look for VGA compatible controller.

To see which driver:
```
cat /etc/X11/xorg.conf
```
Then scroll down till you see the section called... Section "Device"

Here is what mine looks like:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```

Your identifier line may say Generic like mine or it may more specifically identify the card.  

Your Driver line will tell you which driver you are using.  In my case it is "nvidia"

That's about what I know.  You will be using a different driver because you have intel graphics.  There may be more than one driver for intel.  You may need to change drivers to get the resolution you want or you may be able to do some of the following things.  Again, I have no experience with intel graphics, so try to get a little more info before trying any of the following.

The following commands and info may or may not work for intel graphics...proceed with caution.

Method #1:
Sometimes running the following command will force a re detect of everything and fix some problems:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After running it, you should log off and hit ctrl alt backspace to restart  the graphical sub system.

Method #2:
Try editing the xorg.conf file to include your needed resolution:
First, back up your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf xorg.backup
```

Next, edit the file:
```
sudo gedit /etc/X11/xorg.conf
```

Then scroll down to the mode line where it shows the resolutions and just add in the one you want on the line for 24 bit color.  Save it and log off and restart x by hitting ctrl alt backspace.
after logging in, see if the choice you want is now listed in the drop down list for screen resolutions.

Good luck.

---

### Post by mgmiller on 2008-03-19
> Disregard I figured it out. Thanks to anyone who read.

Please post your solution so others can see it.  
Also, please mark the thread as solved by clicking on the thread tools on the top of the page.

Glad you figured it out.

Welcome to Ubuntu.

---

