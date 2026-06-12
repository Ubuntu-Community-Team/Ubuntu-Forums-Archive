---
title: "Fresh Install of Ubuntu Hangs on Startup"
date: 2018-06-11
forum: General Help
---

### Post by ssm1985 on 2018-06-11
Hello All,

I'm a relative newby to Ubuntu and I hope someone can help. I've been dealing with this situation for the last three days and I'm almost ready to seek psychological help as well... anyways here's the deal:

I bought this laptop a month ago and installed Ubuntu 18.04 alongside Windows 10 on a dual boot. It was working great. I think I had to do something with the video card drivers to get the second monitor working but things were running smooth and great. I absolutely loved it. Then I pulled a dumb newby move and accidentally changed the permissions on most of my Ubuntu installation and I couldn't open Atom, wifi disappeared, couldn't move files, etc. I made it useless. Long story short after spending hours and hours trying to figure out how to undo that, I just decided to do a fresh install of Ubuntu.

Since I've reinstalled Ubuntu 18.04, I can only boot it up via "recovery mode". If I do a normal boot it hangs on the Ubuntu loading screen. The dots stop moving and it just freezes. I originally felt this might have something to do with my graphics card driver because if my memory serves me correct, it seemed to work fine after I got my external monitor working before when I set it up the first time outlined above. Admittedly I cannot recall this for sure however.

I have an NVIDIA GeForce GTX 1050 Ti Mobile and I am running the nvidia-driver-390. I have spent the last three days searching forums, blogs, youtube, etc... and I'm stuck. I've run into numerous other problems along the way while trying the methods I stumble across and occasionally it seemed to make things worse and screw things up more so... I would do another install of Ubuntu.

So I have now reinstalled Ubuntu several times at this point, my second monitor isn't even recognized to be attached, and I can't run Ubuntu unless I boot it from recovery mode. The second monitor thing seemed to be a popular issue but nothing has worked yet.

On another interesting note, upon completing the installation of Ubuntu and being prompted to restart, that also froze. Had to do a hard shutdown.

I would appreciate any help possible. I don't want to check myself into a loony bin. 

Thanks!

Oh and if it helps, here are my PC specs:
[LIST]
[*]Asus Republic of Gamers PC 
[*]Intel® Core&#8482; i7-7700HQ CPU @ 2.80GHz × 8 
[*]16GB RAM 
[*]128 GB SSD (Windows is installed here) 
[*]1 TB HDD (Partitioned 500GB for Ubuntu) 
[*]NVIDIA GeForce GTX 1050 Ti Mobile graphics card 
[/LIST]

---

### Post by ssm1985 on 2018-06-11
I'll also try to post things I've done as I continue to do them... I  just tried uncommenting WaylandEnable=false in /etc/gdm3/custom.conf

Outlined here: [https://linuxconfig.org/how-to-disable-wayland-and-enable-xorg-display-server-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-wayland-and-enable-xorg-display-server-on-ubuntu-18-04-bionic-beaver-linux)

No dice....

Previously before I could confirm I had the right driver installed I was dealing with issues similar to this:
[https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/](https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/)

Since I'm still not sure if this has to do with my graphics card driver and I'm researching that, here's the output of xrandr:

xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00*

---

### Post by ssm1985 on 2018-06-12
It looks like my problem is solved. I'm not sure whether it was because of a few things combined or one thing specifically... but here's what I did:

- Switching from gdm3 to lightdm got me to the login screen - but would freeze after entering my password (see [post #8 on this thread]("https://ubuntuforums.org/showthread.php?t=2390509"))
- If I disabled the login requirement on startup then Ubuntu would load, however it would now freeze on shutdown
- Disabling secure boot seemed to make everything come together and function how it should (see [first answer on this thread]("https://askubuntu.com/questions/1029068/ubuntu-18-04-stuck-at-shutdown"))
- I then switched back to gdm3

I'm not sure if keeping secure boot disabled is something to worry about or not. Will have to research that more. However it does seem that the issue was to do with my graphics card/driver. 

Anyways, Ubuntu starts up and shuts down normally, and I have my second monitor functioning as it should. This is a huge weight off my chest and I might have celebrated it a little too much last night because I'm slightly hungover now...

---

