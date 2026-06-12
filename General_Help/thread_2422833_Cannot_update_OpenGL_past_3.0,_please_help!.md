---
title: "Cannot update OpenGL past 3.0, please help!"
date: 2019-07-13
forum: General Help
---

### Post by dark-wanderer on 2019-07-13
I have just got a new laptop, and it has an nvidia GTX 1060 graphics card in it.
It SHOULD be able to use the same or better than my old 960 card did in my previous laptop.

However, I have the nvidia 418 driver installed, and whenever I check glxinfo, it tells me I'm still using OpenGL 3.0.

What am I doing wrong and how do I fix it?

---

### Post by cruzer001 on 2019-07-13
It is my understanding that OpenGL in part of the driver package and there is no upgrade path other than a driver upgrade.

---

### Post by dark-wanderer on 2019-07-13
I've checked using terminal, and it states that my max should be 4.5, but the version string remains 3.0.
My previous laptop has a version string of 4.6. How do I update the version string so it can show just what my graphics card can do?
I'm trying to play a game, and it keeps returning an error, as it thinks my laptop is only capable of 3.0, where 4.0 is the minimum required.

---

### Post by cruzer001 on 2019-07-13
Just seen this in another thread.  A 430 driver available thru PPA.

[https://ubuntuforums.org/showthread.php?t=2422775&p=13872510#post13872510](https://ubuntuforums.org/showthread.php?t=2422775&p=13872510#post13872510)

---

### Post by TheFu on 2019-07-13
After you do an update/upgrade APT cycle, 

```
sudo ubuntu-drivers autoinstall
```
If you are on an LTS, this is relevant for nvidia drivers: [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)
Yet another reason to run an LTS.

---

### Post by deadflowr on 2019-07-13
Is it seeing the correct driver, or did the driver install get mucked up somehow and it's running llvmpipe instead?
what shows
```
glxinfo | grep OpenGL
```

---

