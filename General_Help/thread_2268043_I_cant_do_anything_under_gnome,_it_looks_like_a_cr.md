---
title: "I cant do anything under gnome, it looks like a crop."
date: 2015-03-05
forum: General Help
---

### Post by loopingz on 2015-03-05
I had ubuntu amd64 14.04.1 installed as dual boot, not used everyday, was working ok. I had a amd graphic card (6950). I switched for a nvidia 970. I am unsure if it is the root cause or not because I did not check at first.
But then I cant use correctly ubuntu. Login is going perfectly fine and then I land on something that looks like a central crop of the desktop. I have the mouse, nothing to left or right click, nothing to do, no bars, nothing. CTRL ALT T shows nothing. CTRL ALT F can give me a command line prompt where I can login.
I just did a live sdcard with 14.10 and then updated. It went mostly fine, I just had one error that some software couldnot be retrieved. Anyway It booted straight to linux (which was not the previous behavior), and it worked. The resolution I did not how to check for sure but maybe it was not 1080p looked lower, maybe 720p I am not sure. My firefox was still working good with my previous session and everything. I installed a grub graphical manager tool, put windows first (sorry guys). Then I looked at closed source drivers and there was nothing available. So I started step 1 and 2 of [http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/)
Reboot and back at the same issue :(
Anybody understand?
I did ctrl alt f1 to do step 3 and 4 of [http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/)
Then I have seen the easy way (fun).
I made some progress.
Now I boot directly to a terminal...
If I type startx it starts and resolution looks much better.
I am able to configurate my panels (two plugged one used) to their native resolution.
I dont see the left menu, so I would like to fix the following:
Add the left menu back!
Directly boot to startx
Add the top bar menu

Any help is welcome.

Thanks.

---

### Post by Portaro on 2015-03-05
I dont have gnome I use lxde.

But I think the command is gnome-panel to start your general panel and I think that the left panel is a dock you need to see how is the command to start.

To save this starts at session by deafult simple create a .desktop in - 
copy to $HOME/.config/autostart/gnome-panel.desktop ....

---

### Post by grahammechanical on 2015-03-05
Did you do a fresh install of Ubuntu 14.04.1 over Ubuntu 14.04?

When we install Ubuntu and we tick the box labelled "Install third party software" we get a proprietary video driver installed. In your case it would have been for the AMD graphic adapter. Then you changed to the Nvidia and were runing on the wrong video driver. so, Ubuntu loaded using a fall back open source video driver called llvmpipe. This is my guess and could be that you  getting the wrong screen resolution.

If you installed 14.10 over 14.04.1 then you should have a Nvidia driver for that card. But if you upgraded from 14.04.1 to 14.10 then it is most likely that you still have the AMD driver hanging around. When changing video adapters it is advisable to revert to using the default open source video driver to make the change over and then install the relevant proprietary video driver.

My advice would be to go to System Settings>Software and Updates>Additonal Drivers tab and install the open source video driver. Then restart and see what the screem resolution is like. You might want to shutdown and restart more than once to establish a clean loading profile. Then go to Additonal Drivers again and install the proprietary video driver or leave things as they are if the open source video driver (Nouveau for Nvidia) is working fine.

Regards.

---

### Post by loopingz on 2015-03-06
I reached 14.04.1 through normal update and then passed to 14.10 through live cd update. With my current progress I would say that the nvidia proprietary working is up and working at the native resolution of my screen.
My first issue to solve is to get the launcher back. I will check tonight the autostart stuff.

Thanks

---

### Post by loopingz on 2015-03-07
I got it work. I checked a lot of places but this one was very useful: [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
There was at least some issues with Nvidia drivers and xorg.conf
And by the way
sudo lightdm start
is much recommended than startx...

I am bit worried about those nvidia drivers issue, it was working easier on amd!

---

