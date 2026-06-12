---
title: "Just Installed Kubuntu, All Went Well Until Graphics Card"
date: 2008-02-03
forum: General Help
---

### Post by Linuxuser463443 on 2008-02-03
Hey

I've just installed Kubuntu for the first time, I followed some guides  to get my speedtouch 330 working properly and everything was fine, I was able to get on the net & download opera. I noticed that graphics performance was terrible so I followed a guide in order to install my graphics card as I was recommended this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) 

I used method two as I figured that the most up to date driver would be the best one to use. Unfortunately when I rebooted I was presented with a black screen, before the log in prompt, however the monitor was on and the menu showed that it was at the correct resolution, just no image on the screen.

So I reinstalled and then had a look around google and found something called Envy which I installed and it installed the ATI Graphics card drivers for me, this also gave the same result on bootup, active screen but no image.

Finally I used the restricted manager to download the free ATI Radeon driver, this also gave the same as the other two methods. 

The Graphics card is as follows:

ATI (Sapphire) Radeon x1550
512MB Edition
AGP Edition

Is there anything I can do about this, once this works there will be no reason for me to use Windows unless there's a game I want to play.

---

### Post by Linuxuser463443 on 2008-02-03
Update, I've reinstalled again, I downloaded the driver from ATI's Website and followed their instructions. There is definately some improvement and I can tell that the card is now being recognised properly as Catalyst Control centre is giving the right info. Also no more blank screen on boot.

However there's another problem, 2D performance is still slow and 3D Is just as bad, also fglrxinfo brings this up:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [pcie] Failed to gather memory of size 262144Kb for PCIe. Error (-1007)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(EE) AIGLX: Screen 0 is not DRI capable

```

Update 2:

I've read other threads which suggested putting fglrx in the /etc/modules, I did and no difference was made.

---

