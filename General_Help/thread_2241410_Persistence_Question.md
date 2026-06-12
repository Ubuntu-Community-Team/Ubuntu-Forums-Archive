---
title: "Persistence Question"
date: 2014-08-26
forum: General Help
---

### Post by Andrew_Gravlin on 2014-08-26
I know there is alot of info for persistence out there but this question I have not seen a answer to. I did not search vastly but did spend around 20m trying to figure this out.

My question is this:

Can one use a LiveCD from a CD with persistence on a USB Stick? I would like to do it this route for the bonus of the 2gb in space on my 4gb USB Disk.

I also want to do this to avoid the following problem:

I also occasionally notice with it all on USB the screen will go black after installing stuff and upon reboot and trying linux from a setup with Universal USB Installer and will go back black after and wont load. dmesg doesnt show any errors and it comes back with display after you hold power while it goes to the shutdown portion but nothing else. Hard to explain but basically boots to a black screen with no cursor or anything.

---

### Post by sudodus on 2014-08-26
Welcome to the Ubuntu Forums :-)

Yes it is possible. Try according to this link

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

But I prefer going via USB only. The best option is to have a fast USB 3 pendrive (improves the speed even if you have only USB 2 ports on the computer). See this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

*Edit*: You can also make a regular installation to a USB pendrive (just like an installation to an internal drive, but to the pendrive).

---

### Post by Andrew_Gravlin on 2014-08-26
Ill try the install to USB directly. That will give the full 4gb right? Reason I need this is because standard HDD failed on me and I was using linux as its the best live environment for this.

I just need to be able to have the following:
PlayOnLinux for Firefox and Latest Flash and Java from windows.
Wine for PlayOnLinux
And finally VLC for DVD Playback.

Simple stuff but somehow I run out of space before they get installed. Also before you ask why I need the above: Some sites wont accept the flash for Linux's Firefox's latest Flash. So I need to use Wine.


Thanks in advance for any and all advice.

---

### Post by sudodus on 2014-08-26
If you install to USB, you need more than 4 GB except for Lubuntu, which can be installed for example via the One Button Installer or OBI-9w. 8 GB is OK, but fast USB 3 pendrives have 16 GB or more. And an installed system needs more space than a live system, because a lot of the live system is stored compressed as 'squashfs'.

So if you cannot get a bigger pendrive, and you have problems to find space enough for your application programs, your original idea is good, to boot from CD and use the whole pendrive for a casper-rw file (or casper-rw partition).

-o-

You can try Chrome (maybe also Chromium Browser), I read that it comes with a new version of flash, which might work better for you. Unfortunately the support of flash for linux is not good (it is proprietary software).

---

### Post by Andrew_Gravlin on 2014-08-27
Ok I did that and set it up right but it only wants to now run in low graphics mode. Is there a way to manually install an Nvidia Graphics driver to the USB Drive copy of the OS so that it loads properly? It loads fine without persistence.

---

### Post by sudodus on 2014-08-27
I use nvidia drivers myself with Ubuntu 12.04.5: nvidia driver version 304.88 with a GeForce GT 430 card. But I have no experience of installing proprietary graphics drivers in a persistent live system.

Maybe you can try the boot option nomodeset.

Try the following in terminal window

```
sudo apt-get install nvidia-
```

and press TAB to the the available alternatives.

Depending on version of Ubuntu you will get
```

sudo apt-get install nvidia-173
sudo apt-get install nvidia-304
sudo apt-get install nvidia-319
...
sudo apt-get install nvidia-current
sudo apt-get install nvidia-experimental-304
...

```

Fill in the whole command and run it (press Enter) and reboot the computer.

---

### Post by Andrew_Gravlin on 2014-08-28
Problem is when I boot it with the usb as the casper-rw filesystem it runs in low graphics mode. I will try the nomodeset option and then install the driver and see what happens.

---

