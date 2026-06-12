---
title: "How to Fix  Screen Resolution in Ubuntu 13.04. Workaround."
date: 2013-05-16
forum: General Help
---

### Post by hvralpha on 2013-05-16
If your screen resolution is not correct after installation try the following.

First run xrandr in terminal and see what you have.

It will show the screen resolutions your video card is capable of and which outputs are on.
In my case I have Intel Ivy Bridge Graphics and I had both VGA1 and HDMI2 active both at 1024 x 768 resolution. 

My Graphics card is capable of 1920 x 1080  x 60 hz graphics which it shows after running XrandR. 

In the System Settings it shows I have 2 monitors which is both wrong.  These files are all created during installation when Ubuntu takes the best guess of what your configuration is. This is mostly wrong.

I also tried ARandR which I downloaded on the store and running it shows the same as XrandR, but   you can also change screen resolutions through this utility. It is a pain because you have to do it every time you start up.

I also tried putting a ,xprofile file in my home directory but that did not work either.

I just want output on my HDMI2 output and at 1920x 1080 x 60 hz resolution.

Open File /home/username/.local/monitors.xml in Gedit. ( Sudo Gedit and open the file)
You will see the wrong monitor configurations there. 

Now fix them with the following: 

I first remove all the lines under VGA1 and just left the </output> line to show I did not want it activated. This switched the VGA1 output off.

I then replaced the 1024 with 1920 and the 768 with 1080  in the HDMI2 section and saved the file.

I rebooted and viola!, I had the correct resolution.

Hope it works for you as none of the regular things short of doing a complex xorg.conf file worked for me.

---

