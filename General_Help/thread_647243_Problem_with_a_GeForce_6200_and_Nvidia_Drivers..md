---
title: "Problem with a GeForce 6200 and Nvidia Drivers."
date: 2007-12-22
forum: General Help
---

### Post by hyrule_man on 2007-12-22
Ok.. I have a 6200 LE-A and Ubuntu 7.10. (But the same issues occur in Feisty.)

Ok.. Now, when I install my Nvidia drivers from the restricted drivers manager, and reboot, I cannot set any resolution besides 800x600. So.. yeah. Thats my problem. Ideas? Please? :confused:

---

### Post by jken146 on 2007-12-22
I have a 6200 and it does work fine.  I can't remember if it worked straight away though,

You probably just need to add the higher resolutions to your xorg.conf file.  You could edit the file manually (back it up first!) or do the following:

Hit Ctrl+Alt+F1

Log in

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
The first command stops your X server and the last one starts it again.

---

### Post by hyrule_man on 2007-12-22
Ok, either when I git Ctrl+Alt+F1, or do that first command, it takes me to a plain black screen.. Can't type, cant Ctrl+Alt+Backspace.. Nothing. Other ideas?:(

---

### Post by hyrule_man on 2007-12-24
Bump.

---

### Post by logos34 on 2007-12-24
gksudo nvidia-settings

>x server display config

---

### Post by hyrule_man on 2007-12-24
And do.. What?

---

### Post by hyrule_man on 2007-12-24
My resolution settings there are Auto, and Off. and I cannot select Off.

---

### Post by hyrule_man on 2007-12-24
Bump...

---

### Post by marshall.robert on 2007-12-28
im having exactly the same problem after i upgraded my card, i configure x (dpkg-reconfigure), it found everything, including my monitor and its resolutions which has never happened before, and restart x, nothing.
i try nvidia settings, and all i have is a few tick boxes (unlike my laptop which has a fully array of features and settings (8600gt)).
i have even gone into xorg.conf and commented out all but 1280*1024, it still persists to have a resolution of 800*600.
desktop effects also wont initialize.
both the nv and vesa drivers give me the same, before upgrading it would work under them...

any idea, help or anything will be greatly appreciated, im out of ideas.


edit: i hit ctrl+alt+f1to get to a termial screen, logged in as root, stopped gdm (/etc/init.d/gdm stop), reconfigured x using the vesa driver, started x (startx) and it gave me root logged in to an x session, with a resolution of 1280*1024 24bit colour depth, and an 86hz refresh rate. i then logged out the root x session which took me back to the console screen with root still logged in, i then typed the command 'shutdown now' which initiated the shutdown procedure, but then went and loaded eveything up (like a mini internal reboot), including my default user and an x session at my desired resolution.

edit 2: i used the add/remove software to get rid of the currently installed nvidia driver(nvidia-glx), then just to make sure nothing would intefere i rebooted, then i used the restricted drivers manager to install the relevant drivers for the video card (nvidia-glx-new), now the nvidia-settings looks good, with everything there. full control over both heads, and their resolutions. i then opened a terminal and run the command sudo dpkg-reconfigure xserver-xorg, selected the nvidia driver, then restarted x with ctrl+alt+backspace. which has brought me on to the next problem, it wont log in under the current configuration....

edit 3: a reboot seemed to do the job....

if you have a problem understanding what ive written then please say, i will check back.

-rob

---

### Post by jovial_cynic on 2007-12-28
hyrule_man -

If you're stuck in 800x600 when you get into X, your system might be using the xorg.conf.failsafe file instead of your xorg.conf file.  It's a failsafe version of xorg.conf that will most likely run on any system, and it gets created and ran when the settings in xorg.conf are causing a problem.

Check /etc/X11 to see if xorg.conf.failsafe exists.  

If so, uninstall your nvidia driver and try installing again.

---

### Post by randavance on 2007-12-28
I have a similar problem that I run into with my NVIDIA card. This is how I solve it.

I hit ctl+alt+f1, this is bringing up a command line, it's seperate from the stuff running on your graphical desktop (which you can get back to with ctrl+alt+f7) so you'll need to log in again.

from there I run 

```
sudo dpkg-reconfigure xserver-xorg
```

put in your password

this should bring up one of those blue and white text installation programs.

run through, have it try and find your card, that probably wont work.

When it asks you to choose the type of card scroll down the list and click the one that says "NV".

Put the name of your card into the text field that comes up after.

and from there just breeze through, most of it is just clicking OK, but read it all.

When you get to the part with the resolutions, scroll down the list and click the space bar to check off the resolutions your monitor can handle (I just do 1440x900 because that's my screens resolution).

Choose medium difficulty when it asks about the monitor and pick the option correct for you.

And then when your done reboot your system

```
sudo reboot
```

Oh, and you might also want to try, on your desktop menu going to "system > administration > restricted drivers manager", putting in your password, and activating the NVIDIA driver.

Hopefully that will have worked.

---

### Post by marshall.robert on 2007-12-28
i would recommend that when you have everything working, with the proper (new) nvidia driver installed, then i would run 'sudo nvidia-settings' to setup your resolution, refresh rate, and colour depth etc...

---

