---
title: "buttons not working on HP Presario CQ60 (Ubuntu 12.10)"
date: 2012-12-28
forum: General Help
---

### Post by GabrielMac on 2012-12-28
I cannot seem to get the touchpad to have a right click button. The left button will not act like a left click and instead pastes whatever I have copied recently. It is extremely annoying. I cannot get the right button to right click and it does the same pasting action. The touchpad had similar problems in Microsoft Windows. 

I have been working on this computer for 2 days. first I did a factory recovery from the recovery partition. then that did not work because as soon as I tried to do all the updates the internet explorer update failed and the rest of the updates did not install properly and then nothing worked right anymore and the computer was slow. So, I installed Ubuntu 12.10

Now the buttons seem to be the same button and have strange actions. I think maybe it is a hardware problem?

What should I do? Please help, this is not my computer and I want her to have a nice functioning computer without the need for an external mouse.

Thank you for any information and God Bless,

Gabriel

---

### Post by pqwoerituytrueiwoq on 2012-12-28
if your buttons are doing the wrong thing you can remap them
[https://help.ubuntu.com/community/MouseCustomizations](https://help.ubuntu.com/community/MouseCustomizations)
otherwise look in the mouse settings

---

### Post by GabrielMac on 2012-12-28
Well this is just wonderful! I used the xev command, after installing the software, and tested the mouse. To my vexation I found that the buttons both register as 'button2'!!! 
Now what do I do?

Can anyone help?

---

### Post by pqwoerituytrueiwoq on 2012-12-28
i have a  HP Presario cq60-215dx next to me and it did not have this issue, what is the rest of your model #

---

### Post by GabrielMac on 2012-12-28
it is a CQ60-615DX

---

### Post by pqwoerituytrueiwoq on 2012-12-28
for the mean time you could remap button 2 to button on so you have a left click
maybe you can use tap for left click and the physical button for right click

my asus laptop's touchpad has 1 finger tab for left (button 1); 2 finger tap for right click (button 2); 3 finger tap for middle click (button 3)

---

### Post by GabrielMac on 2012-12-29
That tutorial seems to be for an older version of Ubuntu. Xorg.conf? That is no longer in etc/X11 anymore. 

I do not understand how to make this a permanent thing. I have not been able to use xmodmap right either. I really wish Ubuntu would use graphical programs instead of terminal programs to remap the mouse.

---

### Post by pqwoerituytrueiwoq on 2012-12-30
the file is /etc/X11/xorg.conf this file is generated automatically at boot, but is not stored anywhere on the hdd 
you can generate one with this command
```
sudo Xorg -configure
```

---

### Post by GabrielMac on 2012-12-30
I get an error saying that the x-server is already running. How do I get to a terminal without the xserver running? I tried ctrl-alt>f1 but I don't know how to shut down the xserver.

---

### Post by pqwoerituytrueiwoq on 2012-12-31
```
sudo service lighdm stop
```
```
sudo Xorg -configure
```
```
sudo service lighdm start
```

---

