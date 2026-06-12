---
title: "Ubuntu 16.04 Can't get logged in after daily update"
date: 2016-11-03
forum: General Help
---

### Post by xeddog on 2016-11-03
I have Ubuntu 16.04 installed on a machine that has been running for some time now, and since it is a single user machine, I have used auto-login.  After this mornings updates, which were mostly nvidia related, I can't get logged back in.  I am presented with a login screen, my userid is selected, but when I enter my password it won't properly authenticate.  And yes, I'm certain I am entering it correctly.  I had this  problem some time back, but I don't remember what I did to resolve it.  Something to do with the video drivers as I remember.

Any ideas??


Thanks,

Wayne

---

### Post by #&amp;thj^% on 2016-11-03
I'm not sure how you installed your driver for Nvidia so this may not work for you.
Try this:
```
sudo apt remove nvidia*
##And answer yes##
sudo reboot
```
And now can you log in?
I my self use the repository ppa:graphics-drivers/ppa, and have had no issues with it.
PPA found here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
My card is not a mobile Chip...so might have some relevance if yours is.
```
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450]
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 370.28

```
BTW I found Auto Login a bit buggy on 16.04

---

### Post by xeddog on 2016-11-03
Thanks fallen.  After I submitted my post I did remember some of what I did to recover last time.  I had already done the "apt remove nvidia*" command and rebooted.  That gave me a VGA screen that at least got me logged in.  From there I ran the driver install program to install nvidia-304* My graphics card is an old geforce 6200) which ran ok, but after a reboot I was back to the log in screen that wouldn't let me in.  It has gone downhill from there, so I might have to do a clean install.  I am trying not to do that because my data isn't backed up.  There isn't anything critical, but I would like to try and save it first.  This might be a good time to go get a new disk drive.  This computer is a backup computer to my backup computer and has an old IDE hard drive too.  Notice how often I used the word "old"?

Wayne

---

### Post by scpatl4now on 2016-11-04
I had same problem at login screen ctrl alt F1

at prompt

```
mv .Xauthority .Xauthority
exit
```

Ctrl alt F7
log in

---

### Post by ardvark on 2016-11-04
I too have the same problem. The login screen comes up but there's a 1 inch black frame around the outside (like the screen size has been reduced). After login, screen flashes several times and goes back to a login screen. Sure sounds like a video driver problem. I'd try the fix above, but how do you put in those commands if you're not logged in?

I can get logged in if I use "Gnome Flashback(metacity). Screen is the wrong resolution, can't seem to detect my monitor so I don't have any 1080 resolution.

---

### Post by xeddog on 2016-11-04
```
mv .Xauthority .Xauthority
exit
```

When I tried the move command it just came back ans said the two files "are the same file" and I presume didn't do anything.  Is one of them supposed to be a different name?


Thanks,

Wayne

---

