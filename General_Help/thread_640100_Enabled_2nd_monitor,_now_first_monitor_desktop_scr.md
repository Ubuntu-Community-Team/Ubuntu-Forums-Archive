---
title: "Enabled 2nd monitor, now first monitor desktop scrolls to the left, right up and down"
date: 2007-12-13
forum: General Help
---

### Post by tmcarson1 on 2007-12-13
I have installed a second monitor, and that one is working fine, but now my default monitor I have been using all this time is a little strange.

The ubuntu desktop doesn't fit on screen anymore, I have to move my mouse to the edges of the screen and it will scroll across the desktop, instead of the entire desktop fitting on the screen, any thoughts?

I have changed to a higher resolution and it is still doing it.

Thanks for any advice.

---

### Post by Tenken on 2007-12-13
What video card are you running?

---

### Post by tmcarson1 on 2007-12-13
I am using a Geforce 4ti (nvidia) with restricted driver installed.

1 monitor is on VGA plug, the other is on s-video plug.

s-video works fine, the vga one is the scrolling one.

---

### Post by Tenken on 2007-12-13
I had a similar problem, try running

```
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
sudo nvidia-settings
```

Then go to X Server Display Configuration, configure it to use two seperate X files, save and restart X.

Log back in and run the the nvidia-settings command again and this time configure it to use TwinView. Saving the config file and restarting X one more time should eliminate the scrolling.

---

### Post by chamira on 2008-01-03
Hello & apologies in advance as this is my first post and I'm brand spanking new to Ubuntu/Linux.

I have installed Ubuntu 7.10 & have two Hyundai 19" wide-screen monitors connected to a GeForce 6 series PCI-E graphics card - one on a VGA and the other on a DVI output.

I have also managed to install the NVIDIA restricted driver and have also followed Tenken's  instructions for TwinView but still get that scrolling problem. 

The resolution looks fine at 1440 x 900 @ 75Hz, I could manage to live with the scrolling if it wasn't for the fact my Wacom graphics tablet (an old Graphire 4, I have problems with the Bamboo, but that's another post!) loses its orientation and goes beserk from time to time, I suspect it's related. I really need the tablet assistance as I have RSI & cannot use a mouse for too long.

---

