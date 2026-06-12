---
title: "Need help running two file types Desperately need help!"
date: 2007-04-08
forum: General Help
---

### Post by The Pillows on 2007-04-08
I don't know what I'm doing wrong but I can't run these file types, .rpm and .run . I can extract some stuff from .rpm but have no idea what to do with it and I can get them to run in the terminal just I have no idea at all what to type and/or do. I really need someone to help me out here and I desperately need to find out how to run these two file types correctly so I can install my video card and get rid of this 1 frame per second crap because everything is on vesa. Help please.

---

### Post by tom56 on 2007-04-08
If you are trying to install the nvidia drivers then there is an easier way to do it:
```
sudo aptitude install nvidia-glx
```

Then change the driver bit of your /etc/X11/xorg.conf to "nvidia" (probably is currently "nv" or "vesa").

---

### Post by The Pillows on 2007-04-08
> **tom56 said:**
> If you are trying to install the nvidia drivers then there is an easier way to do it:
```
sudo aptitude install nvidia-glx
```

Then change the driver bit of your /etc/X11/xorg.conf to "nvidia" (probably is currently "nv" or "vesa").Actually I'm trying to do ATI and since I don't even have the drivers installed..Anyways could you maybe tell me how to run .run and .rpm correctly? ^_^

---

### Post by tom56 on 2007-04-08
```
sudo aptitude install rpm
```
RPM is a package manager, just like apt is. To install an rpm file:
```
sudo rpm -i package.rpm
```

But I think there may be an easier way of installing ATI drivers. Try doing a search of the forums and wiki.

---

### Post by justin whitaker on 2007-04-08
> **The Pillows said:**
> I don't know what I'm doing wrong but I can't run these file types, .rpm and .run . I can extract some stuff from .rpm but have no idea what to do with it and I can get them to run in the terminal just I have no idea at all what to type and/or do. I really need someone to help me out here and I desperately need to find out how to run these two file types correctly so I can install my video card and get rid of this 1 frame per second crap because everything is on vesa. Help please.

Here is a link to using .rpm files in Ubuntu:

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

Both alien and rpm are in the Ubuntu repositories. You can do apt-get install alien, or apt-get install rpm. 

For installing a .run file, it's pretty straight forward:

[http://ubuntuforums.org/showthread.php?p=2403867](http://ubuntuforums.org/showthread.php?p=2403867)

Good luck!

---

### Post by The Pillows on 2007-04-08
Thanks a million you two! ^____^

---

### Post by Maestro23 on 2007-04-08
Some more links for you:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

