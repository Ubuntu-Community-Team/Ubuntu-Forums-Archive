---
title: "[SOLVED] NVIDIA Beta 173.08 Drivers Broke System"
date: 2008-05-02
forum: General Help
---

### Post by noerrorsfound on 2008-05-02
In an attempt to fix an America's Army problem, I followed the advice of another user and installed NVIDIA Beta Drivers 173.08. However, now whenever I boot, GDM ends up saying "Ubuntu is in low-graphics mode" and when I try to configure it, the test for both the proprietary nvidia and open source nv fails. If I just click OK, I can login and I'm currently using Ubuntu to post. I've tried re-enabling and disabling the stable NVIDIA drivers through "Hardware Drivers" but right now it says they're enabled (checkmark) and "In Use." :mad:

---

### Post by bodhi.zazen on 2008-05-02
he he he ... I guess that is why the call 'em Beta.

First , remove the Beta driver and re-install the old driver (you did not say if you used the Nvidia or nv driver).

Second, you might watn to check the Nvidia site to see if anyone has posted the problem or a solution.

---

### Post by noerrorsfound on 2008-05-02
I wouldn't have bothered installing them if I didn't want to see if it would fix a bug preventing me from playing AA decently (my input gets lagged on repeated mouse clicks which means shooting is futile).

I don't know how to remove the beta since there's no uninstaller, but I did try re-installing the default through Ubuntu before I posted, and now I get the previously mentioned "In use" with a checkmark.

"NVIDIA Beta 173.08" was mentioned twice. As far as I know, the open source drivers can't do 3D acceleration, so playing AA wouldn't be possible with them.

I don't see anything on their forum, sadly.

---

### Post by noerrorsfound on 2008-05-07
Alright, I reinstalled Ubuntu, and then reinstalled the drivers and encountered the same problem. Here's how to reproduce it:
[LIST=1]
[*]Stop GDM.
[*]Install beta drivers.
[*]Start GDM
[*]Drivers work! The startup NVIDIA screen even says "beta drivers" so I know they're not the old ones.
[*]Restart computer.
[*]If you can get GDM to boot (my startup seemed to halt at "Running local boot scripts" so I had to start GDM myself), select the proprietary video card driver software (nvidia) and click Test. It says: (Title) **Configuration test failed** (Message) **Please verify the selected devices and configuration**. The same message appears even if I select the open source "nv" drivers. However, clicking OK will let you use Ubuntu, just not with NVIDIA's drivers.
[/LIST]
This doesn't seem to be a problem with the drivers. It seems to be a problem with Ubuntu or Xserver.

---

### Post by ghost_ryder35 on 2008-05-07
what version of ubuntu are you using?  if your using hardy the drivers probally dont work correctly because hardy has the latest kernel and latest xserver.  having the driver fail is good feedback for the devlopers of your driver.  let them know

---

### Post by sdennie on 2008-05-07
Did you remove the nvidia-glx-new package before installing the beta driver?  Try:

```

sudo apt-get remove nvidia-glx-new
sudo sh NVIDIA-whatever_version.sh

```

Now, on reboot, the Ubuntu nvidia driver won't clobber the beta driver you installed.

---

### Post by noerrorsfound on 2008-05-08
Tried that, and I don't seem to even have it:
> Package nvidia-glx-new is not installed, so not removed
I did disable Ubuntu's NVIDIA driver through "Hardware Drivers" first by unchecking the box.

---

### Post by PmDematagoda on 2008-05-08
Try doing this:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
    DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reconfigure the X-Server to use the Nvidia driver and boot the PC and see if the X-Server now works.

---

### Post by noerrorsfound on 2008-05-08
That works. Thanks. Do you know how to solve my other problem of [mouse input delay](http://ubuntuforums.org/showthread.php?t=777926) that only affects America's Army?

---

