---
title: "[SOLVED] apt-get problem"
date: 2008-03-28
forum: General Help
---

### Post by DeVonne on 2008-03-28
Hello, I just started using ubuntu today

I was following a guide on internet connection sharing, and it told me to use apt-get
but apt-get cant find the package

I also tried following another guide to install other things via apt-get
and the packages was not found

I tried it on a lot of things but it wont find any packages not even vlc

Help!

Thanks!

---

### Post by Waappu on 2008-03-28
Hi

If you type in terminal```
sudo apt-get update
```what is output?

---

### Post by smoker on 2008-03-28
it will depend if these packages are in the repositories or not, try opening the 'synaptic package manager' from the admin menu, and using the search function for whatever you are looking for,

best of luck

---

### Post by DeVonne on 2008-03-28
> **Waappu said:**
> Hi

If you type in terminal```
sudo apt-get update
```what is output?


visionary@visionary-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
visionary@visionary-desktop:~$ 


> **smoker said:**
> it will depend if these packages are in the repositories or not, try opening the 'synaptic package manager' from the admin menu, and using the search function for whatever you are looking for,

best of luck

Yes I looked in this for some packages, it did not have them :mad:

---

### Post by Bubba64 on 2008-03-28
It looks like you need to open more repositories go to system administration source resources and if you want click on the repositories not enabled most people suggest,  not source, but the rest are good. This will reload more options of programs . Then run update manager which is in same drop down as source resources to get the downloads provided in the opened repositories.

---

### Post by DeVonne on 2008-03-28
Oh and hopefully this is useful


visionary@visionary-desktop:~$ sudo -i
root@visionary-desktop:~# apt-get install dnsmasq ipmasq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dnsmasq
root@visionary-desktop:~# 


I need that to work because of this guide here
[http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370")

---

### Post by DeVonne on 2008-03-28
> **Bubba64 said:**
> It looks like you need to open more repositories go to system administration source resources and if you want click on the repositories not enabled most people suggest,  not source, but the rest are good. This will reload more options of programs .

What do you mean exactly?
I looked in System -> Administration
But did not see what you mean

---

### Post by Waappu on 2008-03-28
> **DeVonne said:**
> visionary@visionary-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
visionary@visionary-desktop:~$

Hi

Seems you don't have any repository enabled in sources.list.

Go System->Admistration and open Synaptic package manager

Then in Synaptic
Settings->Repositories

Check all exept source codes

---

### Post by Bubba64 on 2008-03-28
look again when you click on system and move the cursor to administrative a list of programs should drop down look for software resources and click on it. I might have given the wrong name exactly the first time sorry. the post above me is correct it will take you to the same place. If you do this via synaptic you will get instructions to hit reload in synaptic if you do per my instructions it will ask if you want to reload,

---

### Post by DeVonne on 2008-03-28
> **Waappu said:**
> Hi

Seems you don't have any repository enabled in sources.list.

Go System->Admistration and open Synaptic package manager

Then in Synaptic
Settings->Repositories

Check all exept source codes

Thank you! I think this fixed most of my problems like the ubuntu restricted extras
I did get an error with the
apt-get install dnsmasq ipmasq

root@visionary-desktop:~# apt-get install dnsmasq ipmasq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Bubba64 on 2008-03-28
You need to use sudo to have root control run the command with
 sudo apt-get install dnsmasq ipmasq

---

### Post by Waappu on 2008-03-28
> **DeVonne said:**
> Thank you! I think this fixed most of my problems like the ubuntu restricted extras
I did get an error with the
apt-get install dnsmasq ipmasq

root@visionary-desktop:~# apt-get install dnsmasq ipmasq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Hi

Close Synaptic and then ```
sudo apt-get install dnsmasq ipmasq
``` You need be root or use sudo to install things

---

### Post by Bubba64 on 2008-03-28
Looks like you have things handled here waappu i defer to the larger bean count.

---

### Post by Waappu on 2008-03-28
> **Bubba64 said:**
> Looks like you have things handled here waappu i defer to the larger bean count.

Well don't know about that =) ...

I noticed we both miss that > 
root@visionary-desktop: from DeVonnes post. He was running apt-get as root

---

### Post by Bubba64 on 2008-03-28
> **Waappu said:**
> Well don't know about that =) ...

I noticed we both miss that  from DeVonnes post. He was running apt-get as root

Good Point I never use the root terminal so I wasn't looking for it.

---

### Post by DeVonne on 2008-03-29
Thank you Waappu and Bubba

I seemed to have gotten it to work yesterday when I did a reboot

And yes I was running as root as I am one to do when something does not work ;)

---

### Post by Bubba64 on 2008-03-29
Glad to see everything is working, and you probably have figured out that if you run the regular terminal with sudo that gives you root permission to do what you want done. Ubuntu wiki is a great help besides the forums just use the search bar for help.
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by DeVonne on 2008-03-29
Yes I have, Thank you for the help, VERY appreciated,

Thank you for the link I shall bookmark it :)

---

