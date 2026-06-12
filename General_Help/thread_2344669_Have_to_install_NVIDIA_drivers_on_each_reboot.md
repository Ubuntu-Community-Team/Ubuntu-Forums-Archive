---
title: "Have to install NVIDIA drivers on each reboot?"
date: 2016-11-27
forum: General Help
---

### Post by Joseph_Watts on 2016-11-27
Each time I reboot I have to go through and reinstall the NVIDIA drivers for my monitor settings to be recognized. I'll compile a quick list of the steps involved.

One time download from NVIDIA website for NVIDIA_x86_64-375.20.run
You can't actually run this while lightdm is running. This means going to the login screen, hitting Ctrl+Alt+F1 and signing in.
From there I do```
 sudo service lightdm stop.
```
 I then run the installer```
. sudo ./~\Downloads\NVIDIA_x86_64-375.20.run
```
once that is finished run this. ```
sudo service lightdm start
```

If I don't jump through these poorly crafted hoops I end up with a desktop resolution that is something along the lines of like 600x400 (I don't remember the exact value, probably doesn't matter anyway.)
Anyway, once I start lightdm I'm placed back at the login screen at my proper resolution. Assuming I didn't go through the aforementioned steps I'm left with little to no resolution/monitor settings in arandr.

I'm kind of a newbie in Linux so any help would be appreciated. Thanks!

BTW: I'm running i3 window manager in-case that makes any difference.

---

### Post by howefield on 2016-11-27
Any reason for not using the drivers from the official repository, might be easier and less chance of something like the above happening ?

Are you using Ubuntu ?

---

### Post by Joseph_Watts on 2016-11-27
Are you referring to this? [code]sudo apt-get install nvidia-current[\code]

---

### Post by howefield on 2016-11-27
Well, I'd usually use the additional drivers application to see what packages were available, alternatively if you really need a newer driver like the 375.20 version that you downloaded from the vendors website there is also the graphics-drivers PPA : [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Easier to manage and stay up to date this way.

PS. If you install any of these drivers, you'll need to uninstall whatever you have manually installed.

---

