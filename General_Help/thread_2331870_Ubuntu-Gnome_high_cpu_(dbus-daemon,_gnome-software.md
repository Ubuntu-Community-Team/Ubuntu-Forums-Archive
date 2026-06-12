---
title: "Ubuntu-Gnome high cpu (dbus-daemon, gnome-software, gnome-shell, gnome-setting)"
date: 2016-07-26
forum: General Help
---

### Post by BeNi.G on 2016-07-26
Hi, 

I'm using ubuntu gnome 16.04 and getting those processes to be very high CPU (around 80% on all cores)
(dbus-daemon, gnome-software, gnome-shell, gnome-setting)

my hardware is Lenovo 500 laptop with cpu i7, ram 8GB 

Hope you could help me
Thanks

---

### Post by GU4$+7rxH#@ on 2016-07-26
Hello

I have a possible solution. But this problem have many possibilities errors.

This problem may be because you dont install drivers video card.

Or you should flash your BIOS.

I´m sending possible solutions related with your problem. These solutions is ubicated in some forums.

[https://bbs.archlinux.org/viewtopic.php?id=149601](https://bbs.archlinux.org/viewtopic.php?id=149601)

[http://askubuntu.com/questions/369517/gnome-shell-with-very-high-cpu-usage](http://askubuntu.com/questions/369517/gnome-shell-with-very-high-cpu-usage)

[https://ask.fedoraproject.org/en/question/62522/gnome-shell-very-high-cpu-usage-on-a-clean-install-f21/](https://ask.fedoraproject.org/en/question/62522/gnome-shell-very-high-cpu-usage-on-a-clean-install-f21/)

You should take precaution for flash your BIOS. Because this flash may damage your PC¡¡

Thanks

---

### Post by xeddog on 2016-07-26
This sounds very much like my experience with 16.04 after upgrading from 15.10.  My system:

Intel I-7 3.5GHz dual threads
16GB Ram
1 TB esata disk for /
1 TB esata disk for /home
nVidia GT 730 graphics.

One major difference for me is that memory usage is very low, and CPUs are not taxed at all.  Even with all of my usual apps running memory usage is below 15%, Swap flat-lined at zero, and cpu utilization generally below 20%with occasional higher numbers for two or three processors.  

Sometimes when just switching tabs in FireFox, it takes long enough that the FF window darkens for several seconds before switching.  A simple screen refresh may take 10-15 seconds the first time if it completes at all, but if I do it again immediately it is almost instant.  If the screen refresh does not complete, I have to stop it (click on the "x") and do it again which will complete almost immediately.  Sometimes the Unity launcher takes several seconds to unhide (I have auto-hide on), and after opening it might take quite a while to actually launch an application.  Pressing alt-tab to switch between applications might take a few seconds to get started, but once I'm actually able to switch, it then works fine.  In short, sometimes it seems like something somewhere goes to sleep and takes a while to wake up.After it does wake, it seems ok.

It didn't do this when running 15.10.  I'm just sayin'.

Wayne

---

### Post by BeNi.G on 2016-07-27
> **rickyvelasc said:**
> Hello

I have a possible solution. But this problem have many possibilities errors.

This problem may be because you dont install drivers video card.

Or you should flash your BIOS.

I´m sending possible solutions related with your problem. These solutions is ubicated in some forums.

[https://bbs.archlinux.org/viewtopic.php?id=149601](https://bbs.archlinux.org/viewtopic.php?id=149601)

[http://askubuntu.com/questions/369517/gnome-shell-with-very-high-cpu-usage](http://askubuntu.com/questions/369517/gnome-shell-with-very-high-cpu-usage)

[https://ask.fedoraproject.org/en/question/62522/gnome-shell-very-high-cpu-usage-on-a-clean-install-f21/](https://ask.fedoraproject.org/en/question/62522/gnome-shell-very-high-cpu-usage-on-a-clean-install-f21/)

You should take precaution for flash your BIOS. Because this flash may damage your PC¡¡

Thanks

Hi, I've flashed the bios, but problem don't solve

---

### Post by GU4$+7rxH#@ on 2016-07-27
Hello.

In Spanish forums , I found a solution that seems to be effective


The problem : It's for Fedora 18

I also sent you but I think you can install the package 'yum'


> sudo yum update
su -c 'yum localinstall --nogpgcheck [http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm) [http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)'
sudo yum -y install mesa-dri-drivers mesa-libGLU
yum install libtxc_dxtn --enablerepo=rpmfusion-free-updates-testing
sudo yum install libtxc_dxtn --enablerepo=rpmfusion-free-updates-testing
sudo yum -y install mesa-dri-drivers.i686 mesa-libGLU.i686 
sudo yum install libtxc_dxtn.i686 --enablerepo=rpmfusion-free-updates-testing
sudo yum -y update
reboot
sudo yum install mesa-li*
xdg-user-dirs-update
tracker-control -rs
sudo yum update
/usr/libexec/plymouth/plymouth-update-initrd
sudo /usr/libexec/plymouth/plymouth-update-initrd
sudo yum install nouveau
sudo yum install nouveau*
su
startx
init 3
sudo init 3
sudo yum remove *nvidia*
sudo rm /etc/X11/xorg.conf
sudo yum install mesa*
reboot



How to install Yum??.. [https://rahulmehta1.wordpress.com/2011/08/31/to-install-yum-on-ubuntu/](https://rahulmehta1.wordpress.com/2011/08/31/to-install-yum-on-ubuntu/)

---

### Post by CantankRus on 2016-07-27
> **rickyvelasc said:**
> Hello.

In Spanish forums , I found a solution that seems to be effective


The problem : It's for Fedora 18

I also sent you but I think you can install the package 'yum'






How to install Yum??.. [https://rahulmehta1.wordpress.com/2011/08/31/to-install-yum-on-ubuntu/](https://rahulmehta1.wordpress.com/2011/08/31/to-install-yum-on-ubuntu/)
Really... your posting links on how to install yum so commands can be run from some random search you found.

---

