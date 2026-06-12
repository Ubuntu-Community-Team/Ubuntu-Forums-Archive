---
title: "How to remove and install the supported ATI driver?"
date: 2013-03-14
forum: General Help
---

### Post by c2tarun on 2013-03-14
Hi friends,

I followed [this]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513") thread to install ATI driver on Ubuntu 12.04.2
In the process there were three debs created which I installed using "dpkg --install *.deb"
Those three debs are:
```
fglrx_9.002-0ubuntu1_amd64.deb  fglrx-amdcccle_9.002-0ubuntu1_amd64.deb  fglrx-dev_9.002-0ubuntu1_amd64.deb
```

Now sometimes my laptop get heated up by simple use of only one browser with 5-6 tabs and system goes extremely slow. I know there may be other reasons for system heating, but I wan't to give this a try. I wan't to remove the driver I installed and then install the one from "Addition Drivers".

Can anyone please tell me how to do it?

---

### Post by Mark Phelps on 2013-03-15
> **c2tarun said:**
> Can anyone please tell me how to do it?

Your own signature has the information you need!  CLick on your first link and in there, are instructions for how to remove the fglrx drivers.

---

### Post by c2tarun on 2013-03-15
> **Mark Phelps said:**
> Your own signature has the information you need!  CLick on your first link and in there, are instructions for how to remove the fglrx drivers.
Well yeah :) but that is for removing fglrx driver right? I downloaded driver from ATI site and then installed. 

Also I have two basic questions:
1. What is difference between fglrx-driver and the one we install via jockey (Additional drivers) and the one we download from the site and install it manually?
2. Which among all three is best?

---

### Post by Mark Phelps on 2013-03-15
> **c2tarun said:**
> Well yeah :) but that is for removing fglrx driver right? I downloaded driver from ATI site and then installed. 
Right ... but your question was how to remove the driver:

> I wan't to remove the driver I installed ...


As to your other questions ...

> Also I have two basic questions:
1. What is difference between fglrx-driver and the one we install via jockey (Additional drivers) and the one we download from the site and install it manually?
2. Which among all three is best?
The one you install in Additional Drivers is automatically updated when you do an Ubuntu update that affects the kernel.

If you install any other way (.deb or source download), you will run into problems when you do such an update and have to (1) remove the old drivers, and (2) install the new drivers.

The drivers from AMD are always the most current, in some cases because they post Beta versions.

As to Best -- that depends on how current you want to be and how much work you want to do when the kernel versions change.

---

### Post by c2tarun on 2013-03-16
My laptop gets heated up too much on playing HD video in vlc or if I use my firefox or chrome in full screen mode for long time. Could this be a graphics driver issue?

---

### Post by Mark Phelps on 2013-03-16
> **c2tarun said:**
> My laptop gets heated up too much on playing HD video in vlc or if I use my firefox or chrome in full screen mode for long time. Could this be a graphics driver issue?

Most likely -- not.  The recent Linux kernels don't manage processor idle states well, and unlike the Windows kernels, don't throttle your processor down when you're not placing heavy demands on it.  That means it runs hotter than in Windows.

You can install Jupiter to see if that does anything:

[http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

---

