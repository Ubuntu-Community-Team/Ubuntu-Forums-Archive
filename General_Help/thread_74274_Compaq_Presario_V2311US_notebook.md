---
title: "Compaq Presario V2311US notebook"
date: 2005-10-11
forum: General Help
---

### Post by desidaerius on 2005-10-11
I have attempted to run the 5.04 Live-CD on my V2311 notebook. It runs an AMD Turion 64-bit CPU at 1.6 Ghz, has a 60 GB hard drive, CD-RW/DVD drive and 512 MB of RAM. Each time I try to run the Live CD, whether it is the 64- or 32- bit version, my computer freezes right as the Gnome desktop is getting ready to load. :confused: 

Up to this point, the Live CD initializes without any apparent problems. All hardware is detected- sound, display and mouse are all fuctional. (You can hear the Ubuntu start-up sound and the mouse pointer moves fine. Then the desktop freezes.)

I have tried loading the CD with noapic and nolapic selected. Unfortunately this does not seem to help the problem. :( 

Has anyone else encountered this same issue with the Live CD? I don't know if the install CD will create the same issue or not, I'm reluctant to try to install to the hard drive until I find out for sure if Ubuntu will run on my V2311US. Can anyone tell me what the problem in this case may be and suggest any remedies? 

Any help you could provide would be much appreciated!

---

### Post by mlomker on 2005-10-11
> Can anyone tell me what the problem in this case may be and suggest any remedies?

I'd speculate that it is an issue with the video driver that is being detected and could be worked around if you installed by selecting a different driver.  I moved this thread to the liveCD forum to see if someone has specific advice for you.

---

### Post by desidaerius on 2005-10-11
Thanks for the suggestion. How can I change the driver? Is it available under boot options?

---

### Post by mlomker on 2005-10-11
On an installed version you'd Ctrl-Alt-F2 to another prompt and login:

```

sudo killall gdm
sudo dpkg-reconfigure xserver-xorg
startx

```

I'm not sure what the differences are with a liveCD.

---

