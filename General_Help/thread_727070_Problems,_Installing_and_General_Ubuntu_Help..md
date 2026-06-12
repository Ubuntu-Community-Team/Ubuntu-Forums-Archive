---
title: "Problems, Installing and General Ubuntu Help."
date: 2008-03-17
forum: General Help
---

### Post by SimonJLee on 2008-03-17
Since I'm a new Ubuntu user, I am having problems trying to configure my resolution and installing certain programs. I know that Ubuntu uses the synaptic package manager , but I am  NOT connected to the internet on my other PC. Also in the screen graphics tab, I cannot find the model for my monitor (CTX, PV520), so when I boot up my PC, the monitor would usually glare at me saying 'Unsupported Mode', With various text, I honestly, don't understand.

How do I run .exe files.
How do I change the resolution for my monitor.

I've known about the WINE package, but I cannot find the package through synaptic or knowing how to install it. Could anyone be kinda to help this newbie of Ubuntu.

:confused:

Thanks in advance

---

### Post by danwood76 on 2008-03-17
You may not find your exact monitor in that list your best bet is to choose plug and play.
When it starts up ubuntu loads a splash screen, this is often incorrectly configured in gutsy, the way to fix it is to open up the terminal and type:
```

sudo gedit /etc/usplash.conf

```
and modify the screen resolutions to match your screens resolution and save (normally setting it to 1024 x 768 works best):
```

# Usplash configuration file
xres=1024
yres=768

```
Then you need to update the boot loader like so:
```

sudo update-initramfs -u

```

For wine you need to add the wine repos, best thing to do is go to the [wine]("http://www.winehq.org/") site and follow the instructions from there.

In linux there are no *.exe files, but you can use wine to run a lot of windows executables.

You need the internet to install most of the pacvkages in the repos, it is possible to download all the packages onto several CDs so you dont need the net, but you obviously need the net to do the initial getting of the packages.

hope this clears some things up for you,
Danny

---

### Post by SimonJLee on 2008-03-17
But, since my wireless adapter uses an .exe , how else would I be able to connect to the internet?
if I DON'T have the driver CD for that application :(.

Wine launches .exe's but is there any other method to speed up mounting the .exe's?

Thanks for the monitor help Danny.

---

### Post by DoctorMO on 2008-03-17
If your wifi requires drivers that aren't provided then you should first check the Restricted Drivers Manager in "System > Administration > Restricted Driver Managers" and see if your wifi card apears in the list, you can then try and check the box to enable it and supply the required driver files.

It's important that you get the right driver files in zip format instead of exe, wine will not help you with driver installers.

---

### Post by danwood76 on 2008-03-18
Quite a lot of wifi cards have linux drivers but some dont.
If there isnt linux drivers available there is a program called ndiswrapper that will allow you to load windows drivers in linux.

What wireless card do you have?
I will talk you through the install of the drivers.

---

### Post by SimonJLee on 2008-03-18
I currently use WG111, NETGEAR wireless adapter, and the main router as DG834, but the other computer is using the Windows OS.

[http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG111.aspx](http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG111.aspx)
[http://www.netgear.com/Products/RoutersandGateways/WiredRouters/DG834.aspx](http://www.netgear.com/Products/RoutersandGateways/WiredRouters/DG834.aspx)

How would I be able to configure the network to connect to the router, since the passcode is using a WEP Key?

---

### Post by danwood76 on 2008-03-18
Its very simple once you get the wireless working.
Im just gonna have a quick search on your card, though I think you will have to use ndiswrapper to install the windows drivers.

---

### Post by SimonJLee on 2008-03-18
So does that mean WINE would not be as useful, but only installing applications from a CD, not from a CD Driver.

---

### Post by danwood76 on 2008-03-18
WINE can be used to run applications only.

Device drivers need to be compiled for linux as they are like building blocks for the operating system to be able to communicate with your hardware.

Fortunatly the Ndiswrapper project created a wrapper for windows drivers that can be used to load the windows drivers in linux with great results.

There is a GUI for ndiswrapper and details of how to install it and load the drivers are available in the community docs:
[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

You will need to obtain the windows drivers in zip format format to be able to use them with ndiswrapper. (the exe doesnt have the drivers easily extractable)

-- edit --

It depends which version of the W111 you have but I have found drivers for version 2 and 3
[V2]("ftp://downloads.netgear.com/files/wg111v2_3_4_0.zip")
[V3]("ftp://downloads.netgear.com/files/wg111v3_1_1_0_setup.zip")

---

### Post by SimonJLee on 2008-03-18
Right, would Xubuntu include all of these packages , since now i'm thinking of chainging to xubuntu for a faster environment, Is Xubuntu the same as Ubuntu but instead of using Xfce then GNOME. Since ill be soon be using my OS for gaming then working anyway. ^^

---

### Post by danwood76 on 2008-03-18
Yes Xubuntu will include all the same packages.
I would only switch to Xfce if your GNOME environment is laggy.
You can install Xubuntu by doing:
```

sudo apt-get install xubuntu-desktop

```

in your current install, you will then need to log out and change the session to the Xfce one and log back in.

---

