---
title: "No Login Screen On Ubuntu"
date: 2007-12-08
forum: General Help
---

### Post by vampire622003 on 2007-12-08
P4 2.2GHz
1.5 GB RAM
36 GB Partition for Ubuntu
1.7 GB Swap File
ATI Radeon X1300 PCI

I have installed Ubuntu, and it gets past the Boot Up (Loading) Screen, then it goes black.
I can access my console thingy and login (not go to desktop, just my name with a $ sign). That's all I know what to do.
How do I fix it?
I have never used Ubuntu before, so I need help, please. Thanks

I also noticed when I login (using the command console thing), some type of error says something about "bcm43xx_microcode5.fw" not loading or failed. It keeps popping up in the console thing.

---

### Post by vampire622003 on 2007-12-08
bump

---

### Post by vampire622003 on 2007-12-08
All I see in the console thing when I log in is my name with a $ sign, and that erorr keeps coming up, over and over again.

---

### Post by vampire622003 on 2007-12-08
bump

---

### Post by patty mac on 2007-12-08
Ug, you've got a radeon.  Unfortunately, the xorg ati drivers don't work.  You'll either need to install the proprietary drivers, which will be hard for a command line newbie, or switch to VESA, which will be a lot easier - after you get a desktop you can worry about whether or not you want the proprietary drivers.

Anyway, there are two ways to do this - one is to open up /etc/x11/xorg.conf with sudo priviledges and find the "device" section and change it from "ati" to "vesa".  Use:

$sudo nano /etc/x11/xorg.conf

Nano is thankfully self explanatory.  The other, easier one, is to type

$sudo dpkg-reconfigure xserver-xorg

and select VESA when it asks you to pick a driver.  Every other option you'll have is for advanced configuration that no one needs except for advanced troubleshooting.  Just go with the defaults.  You'll drop back into a command line after it's all done.  Type in

$startx

and you'll go to your desktop.  The graphical login will come up when you reboot.  If this doesn't work, or if you want to install the proprietary one later with the command line to show off, do these next steps.  First,

$nano /etc/apt/sources.list

There will be a lot of items here.  If you delete the pound signs in front of the URLs you'll make those URLs availabe for your system.  It's the APT way of including the URLs of the proprietary stuff while making it unavailable by default.

$sudo apt-get update 
$sudo apt-get install linux-restricted-modules-generic
$sudo apt-get update 
$sudo apt-get install xorg-driver-fglrx
$sudo apt-get install fglrx-control
$sudo depmod -a

The resources at my disposal say the normal way of doing it, running aticonfig --initial, won't work.  So we get to do it the way we did it in number one, running:

$dpkg-reconfigure xserver-xorg

This time, it will matter what screen resolution you pick.  If you're not sure what your card can handle, pick them all and X will sort out which is correct.  The driver you're looking for is fglrx.  After that, type:

$startx

and you should be good.

---

### Post by schauerlich on 2007-12-08
Please be more patient. Bumping your thread every few minutes will not help it get answered quicker.

That being said, once you're logged in to the terminal, try running

```
sudo /etc/init.d/gdm stop
```

To stop GDM (the login screen) from starting up. Then, run

```
startx
```

To go into the GUI.

---

### Post by derby007 on 2007-12-08
Eh 'vampire' did this solution work for u? I had the same problem with my X1300 Pro, I changed my xorg.conf to the VESA driver & this gets u into Ubuntu graphically. Once up and running I enabled the proprietry driver in the "menu". This installs the 'fglrx' package, u can then get compiz up-and-running, (although u might also need xserver-xgl) !

---

### Post by vampire622003 on 2007-12-08
I am about to try it.

---

### Post by vampire622003 on 2007-12-08
I tried doing it, and after it was done, and I typed in startx, I get three errors. One says it can't read the VESA bios (V_BIOS), another one says it has found 0 screens, and requesting insuffiecient memory window, I'll have to look.


And after I reconfigure,and i reboot these lines come up that say "Loading Boot Scripts" and stuff and they blink about four times then stop blinking.

---

### Post by vampire622003 on 2007-12-08
I went to that source.list thing, and there was nothing in there.

---

### Post by vampire622003 on 2007-12-08
when i try to stop it with the gdm stop command it says command not found

---

