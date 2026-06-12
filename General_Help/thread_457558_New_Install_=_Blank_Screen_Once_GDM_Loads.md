---
title: "New Install = Blank Screen Once GDM Loads"
date: 2007-05-28
forum: General Help
---

### Post by CarlosinFL on 2007-05-28
I have a new PC which I will spec below however I have installed Ubuntu on it several times and using several different disks to make sure the media is not defective. It loads the installer fine with no problem and I am able to walk through a basic Ubuntu 7.04 install with no problems but when it's complete and reboots, I see Grub menu and then I select the kernel I wish to boot into and right when GDM loads or when you see the colorful "Ubunut" logo and bar moving, I get a blank screen.

I then rebooted and booted into fail safe mode and I was able to use everything with no problem.

I really don't understand why I get a blank screen when X Windows or GDM loads. The system is still responsive with num lock and caps lock but I see nothing.

**System Specs:**

Intel Core 2 Duo
ASUS P5N32-E SLI
4GB of G.Skill DDR2 RAM
eVGA nVidia 8800GTS PCI-E Video Card

Please help...

---

### Post by Fungyo on 2007-05-28
if you get a blank screen but the system is still responsive, you could try hitting ctrl+alt+F1, then configuring your xserver by typing 
```
sudo dpkg-reconfigure xserver-xorg
``` 
and answering the questions.

One thing i would do first though is boot into safe mode so you can search for the horizontal sync and vertical refresh rate of your monitor.
After getting those values: here are mine for an example.
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
and then performing the above command, you will be asked to set up your monitor. you will be presented with 3 options; simple, medium & advanced, choose advanced then enter the values you found for your monitor.
also you will want to install nvidia drivers after completing the configuration of your xserver.

This may prove usefull to you: [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty")

---

