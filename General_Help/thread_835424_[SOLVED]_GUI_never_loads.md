---
title: "[SOLVED] GUI never loads"
date: 2008-06-20
forum: General Help
---

### Post by rugbylg6 on 2008-06-20
I have a dual boot with kubuntu Gutsy and XP, I haven't had a serious problem since I installed it. Now the loading bar comes up nicely then a blank screen comes up and the log in screen never loads. I went into recovery mode and the terminal loaded up perfectly but I can't get the GUI to work. I havn't installed anything important recently, and haven't even updated in about 3 weeks. 
Thanks

---

### Post by VMC on 2008-06-20
> **rugbylg6 said:**
> I have a dual boot with kubuntu Gutsy and XP, I haven't had a serious problem since I installed it. Now the loading bar comes up nicely then a blank screen comes up and the log in screen never loads. I went into recovery mode and the terminal loaded up perfectly but I can't get the GUI to work. I havn't installed anything important recently, and haven't even updated in about 3 weeks. 
Thanks

When you say GUI, do you mean the desktop? You also said that the recovery mode boots perfectly. I'll guess and say recovery-mode boots to a Terminal and your Generic boots to just a black screen?

Boot back up with recovery-mode and dump contents of this:

sudo fdisk -l

Also from Terminal, if you type 'startx' what happens?

---

### Post by Zorael on 2008-06-20
Also of interest would be the contents of your /var/log/Xorg.0.log file, if you could somehow attach that here.

---

### Post by rugbylg6 on 2008-06-20
startx told me it "failed to initilize Nvidia kernal module" then a fatal server error.
fdisk -l just came up with my partitions, everything looked ok there

/var/log/xorg.0.log did not exist

---

### Post by Zorael on 2008-06-20
Xorg.0.log with a capital X, but that Nvidia error message was what I was looking for. Try installing the driver via envyNG or from the nvidia-glx-new package.
```
$ sudo aptitude install envyng-core
$ sudo envyng -t
```
Alternatively:
```
$ sudo aptitude install nvidia-glx-new
```


Regardless of which you choose, do this afterwards:
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

---

### Post by rugbylg6 on 2008-06-20
perfect, thanks a ton. Now what exactly happened?

---

### Post by Zorael on 2008-06-20
So it worked? Cheers.

Well, you said you haven't updated in about three weeks, but this behavior is common upon changing kernels; the module that the Nvidia driver installs is kernel-specific and needs to be reinstalled when you upgrade to a new one. the nvidia-glx-new (and perhaps the envyNG) package(s) should automatically update themselves when you get a new kernel, so hopefully you shouldn't run into this problem again, as long as you stick to their drivers. I can't promise that this is the case with envyNG, but it certainly is with nvidia-glx-new. You know the drill now anyway; recovery mode, 'sudo envy -t', pick install, le done.

The last command just makes sure that the driver is enabled in your xorg.conf file, and adds some common tweaks to get Compiz working. Might as well add those when we're running the command anyway, don't you agree?

---

