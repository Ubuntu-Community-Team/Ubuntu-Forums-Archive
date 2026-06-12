---
title: "NVidia Driver Problem."
date: 2007-12-03
forum: General Help
---

### Post by lukyjay on 2007-12-03
Hi,

It seems that i have updated my nvidia drivers with the ones from nvidia.com, now every time i select the nv driver, and hit okay, it just goes back to that vesa generic driver, and my monitor is stuck at 800x600.

When i change back to the nvidia drivers, i can get 1440x900 but i cannot get Compiz or the special desktop effects.

Is there a way i can get back to my 1440x900 with good performance on my 8600GT under Gutsy Ubuntu?

Thanks, Jay

---

### Post by -grubby on 2007-12-03
well I'm guessing the drivers for your NVIDIA card are still kind of immature. maybe you could try NVIDIA-GLX-NEW, but I'm thinking this is only for slightly (or not-so-slightly) old NVIDIA cards,not yours (I have an NVIDIA Geforce 6200 and have the aforementioned driver

---

### Post by lukyjay on 2007-12-04
> **nathangrubb said:**
> well I'm guessing the drivers for your NVIDIA card are still kind of immature. maybe you could try NVIDIA-GLX-NEW, but I'm thinking this is only for slightly (or not-so-slightly) old NVIDIA cards,not yours (I have an NVIDIA Geforce 6200 and have the aforementioned driver
And how would i try the GLX-NEW ?

---

### Post by lukyjay on 2007-12-04
In package manager its already installed.

---

### Post by -grubby on 2007-12-04
while than I suppose you would use it by:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```   and select driver "nvidia". After that's done the changes willl take effect if you ctrl-alt-backspace

---

### Post by basicbill on 2007-12-04
Hi,
Not sure if this will help....but I found an article on theinquirer dot net that reports on an application called 'Envy'.
Apparently it's supposed to installed NVidia drivers automatically and do other wonderous things.

Perhaps it will help.

Regards,
bb

---

### Post by tupesadilla on 2007-12-04
the envy script will DEFINITLY help.. i had super problems installing nvidia drivers.. used envy... installed everything i needed and everything worked flawlessly... try it..

sudo apt-get install envy
or via synaptic

---

### Post by pedro_orange on 2007-12-04
I concur...Envy is the nuts. Really did the job for me.

I also recommend reading your VDU manual and double checking what resolutions it likes to be at. I spent an entire evening trying to figure out why whenever I booted up after enabling my nvidia driver I would get the black screen of death. 
The answer? Wrong resolution. 

sudo dpkg-reconfigure -phigh xserver-xorg

^ That command should sort you out. Makes life really simple.

---

### Post by FuturePilot on 2007-12-04
> **nathangrubb said:**
> well I'm guessing the drivers for your NVIDIA card are still kind of immature. maybe you could try NVIDIA-GLX-NEW, but I'm thinking this is only for slightly (or not-so-slightly) old NVIDIA cards,not yours (I have an NVIDIA Geforce 6200 and have the aforementioned driver

Only the nvidia-glx-new (100.11.19) will support the 8600. The nvidia-glx (9639) will not work for this card. It is for the older cards. And the nvidia-glx-legacy (71xx) is for the even older cards.

---

### Post by maxwellcom on 2007-12-08
I have a PNY GeForce 8600 GT, and the nvidia-glx-new driver does not work.  At reboot my system hangs with a blank screen and I am unable to do anything.  I have tried envy as well, with the same result.

Has anyone experienced a similar issue?

---

### Post by Horatio on 2007-12-08
There is much to like about Ubuntu. Although it is disappointing that a meta package does not exit to install Nvidia's drivers so glx is used. The envy script does a good job of fixing the problem. I'd like the install of the Nvidia drivers to be as easy as it is in Gentoo. In Gentoo just execute the command 'emerge nvidia-drivers' and then execute Nvidia's xorg.conf configuration script. I still take a look at the configuration file to see what was done. So, Linux can be transparent and easy. Again, most the my experience with Ubuntu has been good, but this has been a headache. 

Adding to the headache the wiki documentation lead me to believe if I install the nvidia-glx-leygacy  package I would have nvidia drive installed. True, it was installed, and I could see Nvidia's logo after adding to xorg.conf's module section glx and its driver section nvidia. Albeit, the command glxinfo showed glx was not being used. Thankfully I found envy.

Why is envy not a perfect solution. Because, it was a pain to install. The execution of 'sudo dpkg -i ( the envy script current .deb ) ' only starts the process. Okay, I missed the switch to install the dependencies too. I found that executing 'sudo apt-get -f install' finished the job. I'm only left wondering if there was an easier method. I'm using the command line because it's faster than using the graphical interface and kApt is generally useless. In addition, envy is not supported by Catatonical or the Ubuntu community.

---

