---
title: "ATI x1400 Driver And Desktop Effects"
date: 2008-06-27
forum: General Help
---

### Post by JoshMartin7 on 2008-06-27
Hello, I'm pretty new to Linux and I'm not 100% on all the Linux lingo. I had Hardy Heron previously but I took it off and then decided to put it back on. I had enabled my ATI x1400 driver on my Inspiron 6400 Dell laptop before I had got rid of Ubuntu before and I can't figure out how to do it again. I went to the desktop effects and stuff and the box is checked for enabling the driver but it says it's not in use. I'm pretty sure before I had just typed something in the terminal and it worked but not sure.
If anyone could help that'd be awesome!
Thanks a million,
-Josh

---

### Post by BenAshton24 on 2008-06-27
Try running the following command in terminal

sudo apt-get install xorg-driver-fglrx

hope this helps :D

---

### Post by Forlong on 2008-06-28
Run this and post the output here for additional info: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

And please try to be a little more specifc.
> I went to the desktop effects and stuff and the box is checked for enabling the driver but it says it's not in use
Is not very helpful... you mean, you went to *System &#8594; Administration &#8594; Hardware Drivers*, right?
And it says the driver is installed but not in use?
Did you try to install it manually (or via Envy)?

---

### Post by mbarvian on 2008-06-28
try this:

   1. Download and Install ATI Catalyst Control Center: This one is pretty easy. To do this, just go to Applications > Add/Remove Programs > make sure All Available Programs are listed > check (or tick) the box next to ATI Catalyst Control Center. Then click "Apply Changes" down near the bottom.
   
   2. Download and Install the Necessary Packages: Please note: you must have a working Internet connection for this section to work, so why not use your new Wireless connection:)? Also, you must have the extra and the extra repositories enabled in System > Administration > Software Sources for this section to work. If you are connected to the Internet in some way, go to Application > Accessories > Terminal and type in: 

```
sudo apt-get update
```

This will update your software. After that is done (it might prompt you for your password, if so, just type it in), type in:

```
sudo apt-get install linux-restricted-modules-generic
```

Once you are done with that, type in:

```
sudo apt-get install xorg-driver-fglrx
```

This will install the actual driver for the card. Once that's finished, type in:

```
sudo depmod -a
```

Once all of that is finished, you are going to want to edit the xorg.conf file, so please type in:

```
sudo gedit /etc/X11/xorg.conf
```

Once gedit opens up with xorg.conf, look for a section that looks like this:

```
Section "Device"
 blahblahblah
EndSection
```

Once you find it, add the following line right before where it says "Endsection":

```
        Driver      "fglrx"
```

Then click Save at the top of the program, and it will close.

Now, type this in terminal:

```
sudo aticonfig --initial -f
```

Now, restart your computer. Once it reboots, click Applications > Other > ATI Catalyst Control Center. If you get a window with options, and other things, you have successfully installed your graphics card! Now you can look into some of those neat desktop effects. However, if, when you try and open ATI Catalyst Control Center you get a screen that says that the drivers are not installed, it was unsuccessful and you need to review all of the steps and try again.

---

### Post by rubin85 on 2008-06-29
I have ATI Radeon Mobility X1400, and I'm not sure if its the same driver as the plain ATI x1400 but I followed these steps and it helped my system quite a lot. However, when trying to open the ATI Catalyst Control Center, it says the drivers are not installed. It is much faster and smoother now, whereas before it was much glichier. I wrote another thread about my problem, and if anyone has other suggestions for me I will try it out, otherwise I think my problem is fixed.

---

### Post by mbarvian on 2008-06-29
If the Catalyst Control Center doesn't recognize the drivers, you can go to System > Administration > Hardware Drivers and see if the drivers are in use or not.

---

### Post by aoceano on 2008-06-30
Hi,
Im kind new to Ubuntu, i know the basics only.
I got the Catalyt control center and installed the driver. 
But in the Catalyst control center says that my video card is 128 mb memory only, when it should be 256 mb dedicade.

I have a toshiba laptop with the ATI Mobility Radeon x1400.
If anyone could help me.
Thank you.

---

