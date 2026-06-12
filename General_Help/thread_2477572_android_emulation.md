---
title: "android emulation"
date: 2022-07-29
forum: General Help
---

### Post by mattdawolf on 2022-07-29
What would be the best tool(s) to use to emulate an android while having the ability to copy/paste between host and guest, as well as integrating a usb controller? 

I have limited success with VirtualBox. The inability to install guest additions kills most convenient things, like bidirectional copy/paste.

---

### Post by grahammechanical on 2022-07-30
Do you want to run Android applications on Ubuntu? I have installed Anbox.

[https://docs.anbox.io/userguide/install.html](https://docs.anbox.io/userguide/install.html)

Read the instructions carefully. I have never tried to copy/paste with the special Android app that I have installed or with the Android apps and utilities that come with the Anbox.

To install Android apps in Anbox we install the Android Debug Bridge (sdb) which is included in the Android SDK  platform tools which in turn is part of Android SDK manager. Then we can use a command such as

```
sdb install path/to/my-app.apk
```

Regards

---

### Post by miguel001 on 2022-08-02
No matter what you will want a board with virtualization for acceleration and have it enabled in the BIOS. Without that, there is no best way. Instead it would all be slow and annoying.

After that then you want something that can use that. There's various things including Android Studio which is what I use. Its quite fast with AMD svm enabled. Has a lot of options for testing at least. I don't know how well it will suit your desire there as that's not my desire of use.

---

### Post by arraybolt3 on 2022-08-07
If you're on Ubuntu 22.04 (which uses Wayland by default at least in many/most instances), look into Waydroid. It supposedly is significantly better than Anbox. [https://waydro.id/](https://waydro.id/) If you're not using Wayland, you may be able to use Weston to run it anyway.

---

