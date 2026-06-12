---
title: "Screen freezes right after login"
date: 2007-08-04
forum: General Help
---

### Post by SomethingHere on 2007-08-04
Ubuntu installs fine after the Wubi installation, but after I type in my user name and password, it will play sound file and then a corrupted logo(?) screen pops up and that is as far as it gets.  I can still move the mouse, but can't do anything else.  It requires a hard boot and it just does the same thing every time.

Any suggestions?

Edit:  The logo screen doesn't display correctly.


[IMG]http://farm2.static.flickr.com/1009/1008344930_b8257f73cb.jpg[/IMG]

---

### Post by w4ett on 2007-08-05
It looks like you are using an incorrect video card driver, or your xorg.conf  is  not configured correctly.  At login, try entering into safe graphics mode, and see is you can log in that way.

---

### Post by tuxcantfly on 2007-08-05
When you get there, press Ctrl-Alt-F2, and login from there. Then, install the proper video card drivers. If you're using an nvidia card, enter this:

> sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

and reboot, and it should work better. If using an ATI card, see here [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by SomethingHere on 2007-08-05
> **tuxcantfly said:**
> When you get there, press Ctrl-Alt-F2, and login from there. Then, install the proper video card drivers. If you're using an nvidia card, enter this:

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

and reboot, and it should work better. 

Thanks, that took care of the problem.  I am using a Nvidia 7800GT.

---

