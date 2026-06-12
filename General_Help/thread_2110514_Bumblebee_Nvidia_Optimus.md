---
title: "Bumblebee Nvidia Optimus"
date: 2013-01-30
forum: General Help
---

### Post by Italianec on 2013-01-30
Hello! 

My notebook is Asus K73S with Ubuntu 12.10 3.7.0.7-generic 64 Bit.

Using GeForce GT540M.

I am experiencing huge problems while trying to install my Video drivers.

I tried every solution on Google, but nothing seems to work.

Currently i just tried this solution with no luck:


sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install bumblebee bumblebee-nvidia bbswitch-dkms
sudo reboot

After reboot i type in console: optirun glxspheres

and followed error occurred:
[Error]Cannot access secondary GPU - error: Could not load GPU driver
[Error]Aborting because fallback start is disabled.

Any idea how to fix the problem and finally get my Nvidia card to work?

Help is greatly appreciated!

I am sorry for my English, it is not my native language.

---

### Post by dino99 on 2013-01-30
i've no clue, but its maybe a glxspheres issue

what is the graphic driver activated ? (look at System Settings Video)

note:
its better to use the latest kernel & video driver & mesa

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by grahammechanical on 2013-01-30
I may be wrong but after we run this command

```
sudo apt-get update
```

we usually run this command for the update to the sources list to take effect

```
sudo apt-get upgrade
```

When you ran

> sudo apt-get install linux-headers-generic

and 

> sudo apt-get install bumblebee bumblebee-nvidia bbswitch-dkms

did the the terminal give you any errors?

What does the Additional Drivers tab in Software Sources say about the video driver that is activated or in use?

Regards.

---

### Post by Italianec on 2013-01-30
> **dino99 said:**
> i've no clue, but its maybe a glxspheres issue

what is the graphic driver activated ? (look at System Settings Video)

note:
its better to use the latest kernel & video driver & mesa

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


Recently the driver stroke is labeled as 

Driver: Unknown.

Experience: Standard


Should i just now wipe everything related to Nvidia drivers and Bumblebee and just do a clean re-install.

Dear Dino could you please explain how to install latest Kernel & Video & Audio & Mesa drivers?

---

### Post by omeomi on 2013-01-30
> **Italianec said:**
> Should i just now wipe everything related to Nvidia drivers and Bumblebee and just do a clean re-install.

Yes, you should do this. If you had any other nvidia drivers present this can create a conflict.

I have Bumblebee up and running for quite some time now and it works smooth but you have to start with a clean install without any other drivers present.

You don't need to install kernel versions or mesa drivers. The installation commands you used are correct.

---

