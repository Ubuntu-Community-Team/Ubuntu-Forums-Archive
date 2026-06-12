---
title: "Nvidia driver do not work as intended"
date: 2019-07-14
forum: General Help
---

### Post by plionel on 2019-07-14
I have seen many posts but since I have passed to Ubuntu 18.10 and then 19.04 but I do not succeed to use my second monitor.
I can use the main one if I use the driver Nouveau that does not handle my second monitor.
 If I use the nvidia driver 430 (I did not see it before my "purge" commands today, before the driver 418 was recommended) then I can log in but I have a black screen and a mouse and that's it.
Here is the last attempt that I do to try to fix it :
```

apt install xserver-xorg-video-nouveau
service lightdm stop
apt purge nvidia-compute-utils-418
apt purge nvidia-dkms-418
apt purge nvidia-kernel-common-418
apt purge nvidia-kernel-source-418
apt purge nvidia-prime
apt purge nvidia-settings
apt purge nvidia-utils-418
apt auto-remove
dpkg --get-selections | grep nvidia
add-apt-repository ppa:graphics:drivers/ppa
apt update
ubuntu-drivers devices
ubuntu-drivers autoinstall
apt install nvidia-prime nvidia-settings
apt install nvidia-cuda-toolkit
apt install nvidia-modprobe

```

So now, i have the 430 and not 418 but it still not have resolved my case.

With a xfce session, it works ...in all the cases so why not with the classic Ubuntu session ?

I have a GeForce GTX 1080 on an Acer Predator GX 792.

What can I do ?

---

### Post by rbmorse on 2019-07-14
I just cleared up the same issue on 18.04 by:

```
sudo apt purge nvidia-*
```

Reboot, that should get you up on nouveau.  

Installing the 430 drivers with 

```
sudo apt install nvidia-drivers-430
```

---

### Post by plionel on 2019-07-15
What is the difference with my list of commands that I put ? I purged nvidia and install new 430 drivers after that ... :-k

---

### Post by plionel on 2019-07-15
I just done your exact commands just to be sure though (there is no 's' to 'drivers' by the way) and I have also the black screen.

---

### Post by CatKiller on 2019-07-15
> **plionel said:**
> 
With a xfce session, it works ...in all the cases so why not with the classic Ubuntu session ?

Gnome had an issue where it would default to a (broken on Nvidia) Wayland session if it detected hardware acceleration. I don't know if that's still the case: I don't use Gnome.

---

### Post by plionel on 2019-07-16
I just can't go to log in screen with Wayland so i deactivated it since a long time. With Wayland, I have the famous bug "Started BPFilter" that hangs.

---

