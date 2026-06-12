---
title: "MESA Update rollback"
date: 2014-11-16
forum: General Help
---

### Post by rpcaldeira2 on 2014-11-16
Hello, I have a Clevo W230SS and i'm using Xubuntu 14.04 and friday i've made the following update:

```
Start-Date: 2014-11-14  18:21:36
Commandline: apt-get upgrade
Upgrade: libgl1-mesa-dev:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libsystemd-login0:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libegl1-mesa:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), systemd-services:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), adobe-flashplugin:amd64 (11.2.202.411-0trusty1, 11.2.202.418-0trusty1), libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libegl1-mesa-dev:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), gnome-calculator:amd64 (3.10.2-0ubuntu1.2, 3.10.3-0ubuntu0.1.1), libsystemd-daemon0:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libgudev-1.0-0:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libpam-systemd:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libglapi-mesa:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libglapi-mesa:i386 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), udev:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libgles2-mesa:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libudev1:amd64 (204-5ubuntu20.7, 204-5ubuntu20.8), libudev1:i386 (204-5ubuntu20.7, 204-5ubuntu20.8), libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libxatracker2:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libgbm1:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), adobe-flash-properties-gtk:amd64 (11.2.202.411-0trusty1, 11.2.202.418-0trusty1), mesa-common-dev:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2), libgles2-mesa-dev:amd64 (10.1.3-0ubuntu0.1, 10.1.3-0ubuntu0.2)
End-Date: 2014-11-14  18:22:14
```

Now, my keyboard language is back to en_us, i don't have wifi or trackpad. Can you help me?

Thanks guys

---

### Post by grahammechanical on 2014-11-16
Are you using the open source video driver or a proprietary video driver? Mesa is part of the open source video driver that is installed by default and the code is still there even when we activate a proprietary video driver. So, mesa will be updated even if we are not using the open source video driver.

Is the update to mesa the problem. There was other stuff updated relating to systemD, Adobe-flashplugin and gnome-calculator. I am just making the point that it may not be Mesa causing this problem.

If you are using the open source video driver, then try activating a proprietary video driver. If that does not solve the problem then you will know that it is not mesa.

Are you saying that you cannot add another keyboard layout? Have you tried to activate WiFi?

Regards.

---

### Post by rpcaldeira2 on 2014-11-16
Thanks for your quick answer[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323").

I do not have any proprietary drivers installed.
Regarding the keyboard layout, i haven't tried to add any other.
But regarding to wifi, the network manager ceased to recognize my wireless adapter...

Thanks again

---

### Post by rpcaldeira2 on 2014-11-16
UPDATE: SOLVED!!!!!!

From grub go to the recovery mode, enter dpkg and reinstall the packages and it worked

Thanks guys :)

---

