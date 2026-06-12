---
title: "Sharing the Home directory between Ubuntu and Xubuntu"
date: 2008-05-15
forum: General Help
---

### Post by SFinn on 2008-05-15
Hi,

I installed Ubuntu 7.10 a little while ago, making a separate partition for the Home directory. Now I want to install Xubuntu as well (I'm hoping it will run a little faster). Is there a way to share the Ubuntu Home directory with the Xubuntu Home directory, so I can easily access files from both OS's?

Thanks

---

### Post by adult swim on 2008-05-15
you wont need another ubuntu installation to use xubuntu, it uses the same ubuntu installation.  to get it, from a terminal run ```
sudo apt-get install xubuntu-desktop
```  restart and whenever you get to the login screen click options and then select session and choose xfce.  then you will load xubuntu.

---

### Post by EXCiD3 on 2008-05-15
Xubuntu is a separate version of Ubuntu that replaces Gnome with XFCE. You can install any desktop manager you like, including KDE and openbox among MANY others, onto any installation of (X/K)Ubuntu. Just install which ones you would like to try and select it in Session as mentioned. You can always remove the ones you dont want through your package manager if you decide you found one that best fits you.

---

### Post by SFinn on 2008-05-15
Oh, that's good to know - I had no idea about that before. Would it still take fewer system resources, installing it through apt-get?

---

### Post by EXCiD3 on 2008-05-15
apt-get is just one way you can install XFCE, you can also use a package manager (synaptic for example) to install. Only after you select XFCE as your session will it start using less resources. You will be using Gnome (Ubuntu) by default which uses more resources. You can select XFCE as your default session and you will automatically use it when you login. Anytime you are using XFCE instead of Gnome it will be using less resources. XFCE is just another option to use instead of Gnome, or KDE, etc which are all different window managers (what you see when you login). Hope this helps clarify a little.

---

### Post by bodhi.zazen on 2008-05-15
> **SFinn said:**
> Oh, that's good to know - I had no idea about that before. Would it still take fewer system resources, installing it through apt-get?

No, if you install xubuntu it is much much lighter then installing xubuntu-desktop.

If your /home is already on a separate partition you can easily share it. Install xubuntu and mount the home partition at /home without formatting it.

If not, move it first.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Better leave home alone and share a /data partition

ln -s /mnt/data /home/<your user>/data

---

### Post by piousp on 2008-05-15
if you decide to just install xubuntu-desktop, use aptitude, instead of apt-get. It will make your life easier.

---

### Post by SFinn on 2008-05-16
> **bodhi.zazen said:**
> No, if you install xubuntu it is much much lighter then installing xubuntu-desktop.

If your /home is already on a separate partition you can easily share it. Install xubuntu and mount the home partition at /home without formatting it.

I reckon I'll install Xubuntu then - my computer is a little old.

I've already got a separate partition for /home. For mounting the /home partition, should I do that during installation, or after that?

---

### Post by EXCiD3 on 2008-05-16
You can mount it during installation, just choose manual paritioning and have it mount to /home then.

---

### Post by Archmage on 2008-05-16
> **SFinn said:**
> For mounting the /home partition, should I do that during installation, or after that?


Yes, you should use the manual partition option, not choose your old /-directoy, but choose a new one from your free hard-drive-space, choose the mount-point / and format this one and than choose your home-partition, NOT format this one and mount it as /home.

I would suggest that you back-up your data first.

---

