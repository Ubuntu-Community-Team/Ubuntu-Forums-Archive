---
title: "Is There A Way To Install Gimp 2.10 On Ubuntu 14.04?"
date: 2018-05-09
forum: General Help
---

### Post by braznyc on 2018-05-09
Any help is welcome.

Any PPA that works?

Thanks!

---

### Post by dino99 on 2018-05-09
An active ppa , but not the latest version  [https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp)

---

### Post by deadflowr on 2018-05-09
if you're not afraid of snap packages you can install the snap on 14.04. (currently the snap version is 2.10)
[https://insights.ubuntu.com/2017/03/30/snaps-are-now-available-for-ubuntu-14-04-lts-desktop-and-server]("https://insights.ubuntu.com/2017/03/30/snaps-are-now-available-for-ubuntu-14-04-lts-desktop-and-server")

Note that installing snapd on 14.04 will want install linux-generic-lts-xenial kernel. (The 4.4 kernels)

---

### Post by monkeybrain20122 on 2018-05-09
I compiled from source in 16.04, but you need to set up an environment with own libs since the system ones are too old for gimp 2.10. In 16.04  I have to compile a few of these dependencies (maybe 4 or 5 of them) in gimp's environment. You will need to compile more in 14.04 since more of its libs are too old.

---

### Post by monkeybrain20122 on 2018-05-09
> **deadflowr said:**
> if you're not afraid of snap packages you can install the snap on 14.04. (currently the snap version is 2.10)
[https://insights.ubuntu.com/2017/03/30/snaps-are-now-available-for-ubuntu-14-04-lts-desktop-and-server](https://insights.ubuntu.com/2017/03/30/snaps-are-now-available-for-ubuntu-14-04-lts-desktop-and-server)

Note that installing snapd on 14.04 will want install linux-generic-lts-xenial kernel. (The 4.4 kernels)

According to [this  ]("https://www.omgubuntu.co.uk/2018/05/gimp-2-10-ubuntu-download")from May2 there is a Flatpak, the snap is 'coming'. Not sure whether it has arrived or not.

---

### Post by braznyc on 2018-05-09
The Flatpak is not working on Ubuntu 14.04.

---

### Post by kostkon on 2018-05-09
> **braznyc said:**
> The Flatpak is not working on Ubuntu 14.04.
What about the snap?
```
>>~> snap info gimp
name:      gimp
summary:   GNU Image Manipulation Program
publisher: snapcrafters
contact:   https://github.com/snapcrafters/gimp/issues
license:   GPL-3.0+
description: |
  Whether you are a graphic designer, photographer, illustrator, or scientist, GIMP provides you with
  sophisticated tools to get your job done. You can further enhance your productivity with GIMP thanks
  to many customization options and 3rd party plugins.
snap-id: KDHYbyuzZukmLhiogKiUksByRhXD2gYV
channels:                
  stable:    2.10.0 (38) 217MB -
  candidate: 2.10.0 (38) 217MB -
  beta:      &#8593;                 
  edge:      2.10.0 (38) 217MB -
```

---

### Post by braznyc on 2018-05-09
I installed the Snap package and added manually a command to run it from the KDE launcher. because I couldn't find shortcut for it on the start menu or anywhere else:

snap run gimp


I hope it runs smooth on my computer.



Thank you, guys!

---

