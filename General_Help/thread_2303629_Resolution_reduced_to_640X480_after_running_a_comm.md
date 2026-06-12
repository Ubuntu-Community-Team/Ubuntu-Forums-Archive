---
title: "Resolution reduced to 640X480 after running a command! Help!"
date: 2015-11-20
forum: General Help
---

### Post by kuverit on 2015-11-20
Hi, I was experiencing video tearing issues. Was trying to fix it. This is what I was having a look at: [https://wiki.archlinux.org/index.php/NVIDIA](https://wiki.archlinux.org/index.php/NVIDIA)

> Tearing can be avoided by forcing a full composition pipeline, regardless of the compositor you are using. To test whether this option will work, type

```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"
```

It has been reported to reduce the performance of some OpenGL applications, though.

**In order to make the change permanent**, you need to add the following line...

So, I thought running this command would make a temporary change. So, I ran it. Now, my display is screwed. The change isn't temporary, its permanent.

Please tell me how to get it back to original condition.

I'm using kubuntu 15.10. Nvidia 820M.

---

### Post by kuverit on 2015-11-20
Bump

Somebody help please!

---

### Post by grahammechanical on 2015-11-20
In Ubuntu there is a utility called Additional Drivers. It lets us set which video driver to use. It may be called the same in Kubuntu. Have you tried using Additional Drivers to change to the open source driver, then restart, then select the appropriate Nvidia driver again?

---

### Post by blm-ubunet on 2015-11-20
```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = Off }"
```
Might be a good start..
Else could try editing/deleting the nvidia-settings config file "~/.nvidia-settings-rc" then logout-login.

or try reconfigure the existing installed driver.

---

### Post by kuverit on 2015-11-20
> **grahammechanical said:**
> In Ubuntu there is a utility called Additional Drivers. It lets us set which video driver to use. It may be called the same in Kubuntu. Have you tried using Additional Drivers to change to the open source driver, then restart, then select the appropriate Nvidia driver again?
I had Nvidia drivers installed through additional drivers.

---

### Post by kuverit on 2015-11-20
> **blm-ubunet said:**
> ```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = Off }"
```
Might be a good start..
Else could try deleting the nvidia-settings config file "~/.nvidia-rc" or similar then logout-login.

or try reconfigure the existing installed driver.

Will try it tomorrow and see what happens. Thanks.

---

### Post by buzzingrobot on 2015-11-20
Graham is suggesting using Additional Drivers to wipe out this errant Nvidia install, install the open source driver, boot to that and do a fresh Nvidia install via Additional Drivers.

Also, I think the Nvidia Settings GUI lets you save its current state as a file and then load it at startup.  Would be useful to save a known working config before experimenting.

---

### Post by blm-ubunet on 2015-11-20
I wouldn't use a sledgehammer to crack an egg.
NVidia's documentation is second to none..
```

cat ~/.nvidia-settings-rc
nvidia-settings --help
```
The command line options are as vast as VLC or ffmpeg but possibly less confusing but very well documented.

---

### Post by kuverit on 2015-11-21
The problem is solved. Thanks everyone for your support, especially grahammechanical and buzzingrobot. 


This solved it:
> Graham is suggesting using Additional Drivers to wipe out this errant Nvidia install, install the open source driver, boot to that and do a fresh Nvidia install via Additional Drivers.

By solved, I mean, I'm no more reduced to 640X480 resolution. I just disabled the Nvidia driver and enabled the Nouveau driver. I haven't tried installing Nvidia back.

I was wondering what is the advantage of using Nvidia drivers over the Nouveau drivers?

---

