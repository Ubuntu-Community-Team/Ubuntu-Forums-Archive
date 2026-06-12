---
title: "howto change video driver while booting"
date: 2021-11-06
forum: General Help
---

### Post by jgw on 2021-11-06
I am posting this because it might be of interest if somebody has a problem with an nvidia driver.

I just reinstalled Ubuntu 20.04.3   My display is an nvidia card.  My display was going bonkers.  When I installed I was gifted with two drivers.  nvidia 340 and xorg.   It came up using the xorg driver so, in my infinite wisdom, I decided to switch to the nvidia driver.  I did that and applied it and re-booted.  I was then gifted with a blank black screen.  

I then searched to internet with a solution and found:
sudo  systemctl  stop  lightdm.service
sudo  apt  purge  '^nvidia-*'
sudo  apt  install  xserver-xorg-video-nouveau
sudo  reboot  now

this allowed me to purge the nvidia driver and install the xorg driver and it saved the day.  

As far as I can tell you can delete and also go out and import another driver if you know what you want.  I knew what I had on the system so I didn't really have to do that.

To get to this the trick is to start pressing the esc key when booting.  This will take you to the option to choose advanced settings and other stuff.  Select the advanced settings and then turn on the network and then choose to do stuff (forget the wording but its obvious).  then do the above commands and you will be on the other driver which should work.  

The interesting thing is that when I think I went back to the initial driver that had the problems I am not sure that I didn't load an entirely different driver as what I have now no longer has problems but I don't care as its working.

I am going to mark this as solved going in.  I have been fighting this stuff for over a week now and am done and up and running.  Most of my problems were caused by my messing around.  Oh, there are a LOT of replies when you google "ubuntu booting into recovery/grub menu".  I have read a bunch of them and they are not simple.  The trick is getting into the first recovery/grub menu and you can move on from there easily without all the other stuff.  

Hope this might help somebody and save them a bit of time.

---

