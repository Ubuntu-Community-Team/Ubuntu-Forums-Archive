---
title: "it started with the purple screen"
date: 2013-01-02
forum: General Help
---

### Post by nordenj on 2013-01-02
Been working on this for awhile now.  Using a Toshiba Satellite laptop with an AMD graphics card.  I did a dual install of ubuntu 12.10 along side windows 7.  The live CD worked fine with no trouble.  When I installed I would get a purple screen during boot and the computer would hang there.  If I rebooted into Windows, then rebooted into Ubuntu it would work fine.  

Then I downloaded an upgrade, and I could not get past the purple screen no matter what.  So I did a bunch of web surfing to try to find the problem.  This is what fixed the purple screen boot problem:

sudo apt-get update
sudo apt-get upgrade   
sudo apt-get install fglrx    
sudo aticonfig --initial
sudo reboot

However, now that it boots fine, I have no Launcher on the side or system bar on the top.  I have tried the following things and nothing has worked.   First I tried to restart Unity, that did nothing.

Then I tried this:

mv ~/.compiz-1 ~/.compiz-1.BACKUP
mv ~/.config/compiz-1 ~/.config/compiz-1.BACKUP

Again nothing.  So then I tried this:

dpkg -1 | grep unity
sudo apt-get update
sudo apt-get install unity
sudo apt-get update
sudo apt-get install ubuntu desktop
sudo service lightdm restart

That did not fix it, so I tried this:

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install fglrx legacy

its says legacy not found.  Any Ideas?

---

### Post by wojox on 2013-01-02
> **nordenj said:**
> 
sudo apt-get install fglrx legacy

its says legacy not found.  Any Ideas?

Should be this here (you left out the hyphen.)
```
 sudo apt-get install fglrx-legacy
```

---

### Post by imachavel on 2013-01-02
perhaps you need to download it:

sudo apt-get install fglrx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fglrx-legacy

I don't have it either. I'm assuming that with your purple screen issue with the graphics card that Ubuntu seems to have been missing a proper driver for that gfx card. I think the main issue is that once you find a driver, or a 3rd party driver, or a restricted driver, that Ubuntu will use, there's no guarantee you'll get maximum performance or maximum res out of that gfx card. Windows makes drivers that utilise the directx11 api library, I should say when that graphics is manufactured, it's manufactured expecting the driver to run on windows. Ubuntu uses opengl which isn't THAT old, but many graphics card manufacturers don't expect a driver to be compiled for a high end graphics card for opengl, so finding updates and driver support and sometimes codecs can be a pain in the ***.

Windows 8 recently updated their library to include support for OpenGl the way windows xp did, and also directx. It's just kind of stupid. Directx was made as an audio/video library to support mainly c#. The source code isn't given away, and in reality it wouldn't work with Ubuntu anyways. It'd be easier to re write a frame work based on the frame work of direct x that supported audio/video but mainly opengl is not the issue. The issue is just that hardware manufacturers rarely give LOTS of support to Linux and often times the Linux team itself has to write the drivers for a new graphics card so a fresh Ubuntu install with a brand new GFX card seems unlikely and limited to having support.

Is the graphics chip on the laptop board part of the HD 7900 series graphics line? That's pretty high end

---

### Post by nordenj on 2013-01-02
Thanks Wojox, the dash fixed it.  Now everything boots up correctly and the launcher and system bar are there.

Imachavel, the graphics card is an AMD ATI Wrestler Radeon HD 6310.  I don't really know what that means, but that is what I get when I type 

lspci | grep VGA

Everything seems to work now, except I have a block on the bottom of the screen that says AMD Unsupported Hardware.  I guess I can live with it, but it would be nice if I could get rid of it.  Any thoughts?  And thanks for the help.

---

