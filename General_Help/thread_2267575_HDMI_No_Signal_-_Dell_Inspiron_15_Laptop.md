---
title: "HDMI No Signal - Dell Inspiron 15 Laptop"
date: 2015-03-02
forum: General Help
---

### Post by Pvt.Julian on 2015-03-02
Hi Guys

I have Dell Inspiron 15 Laptop with standard Intel Graphics and currently running Ubuntu 14.04 LTS 64bit  ,I am trying to connect it to my SONY TV via HDMI but when I Plug it in ,TV keeps saying No Signal and the laptop doesn't seem to even pick up that there is something plugged in at all ...? I have tried to search the issue but havnt been able to find anything that I have even tried something called " disper " with no luck and Xrandr ...I am not very clued up on Linux if anyone could help I would really appreciate it . This is xrandr info that comes up on my machine if that helps....

" pvtjulian@pvtjulian-Inspiron-3521:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   39.9  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
pvtjulian@pvtjulian-Inspiron-3521:~$ "

---

### Post by gifford on 2015-03-02
Try plugging it in to the TV before starting Ubuntu.

---

### Post by efflandt on 2015-03-03
Or log out of X and then log back in. X looks for video when it is started, not if hot plugged after it is running. Otherwise from System Settings > Displays, you could try the "Detect Displays" button.

---

### Post by Pvt.Julian on 2015-03-04
I have tried that ,plugging in the cable before booting up then for some reason machine gets to a certain point and stays there till you unplug the cable ....

---

### Post by Pvt.Julian on 2015-03-04
I have tried the Detect screen button but nothing happens when i press it ,it does not detect anything ....Its almost as if the computer is not picking up that there is anything plugged in...When i plug the HDMI cable literally nothing happens No message , No flicker , No error message ..nothing just does not respond ...The HDMI definitely works and the laptop is only a few months old infact I have used it on the same TV running the Mint Distro. But on Ubuntu just wont seem to work ...I have installed all the updates available and everything so that is not the issue ...

---

### Post by Pvt.Julian on 2015-03-05
Hi Guys I have managed to get the machine to read that there is something plugged in (Don't ask me how coz I have no idea but we making progress : )  ..) ...when i go in the display options now it reads there is a Sony TV on the other end however now when i try to switch over to that display or duplicate the screens , the TV stays black and comes up with a message " Signal not recognised please check connection " or something of that sort ....Does that mean that it cant work with that particular TV set or is it something to do with OS .??

---

