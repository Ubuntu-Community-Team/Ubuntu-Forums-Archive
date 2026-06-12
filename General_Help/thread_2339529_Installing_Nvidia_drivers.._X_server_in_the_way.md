---
title: "Installing Nvidia drivers.. X server in the way"
date: 2016-10-09
forum: General Help
---

### Post by GuppiePilot on 2016-10-09
New Lenovo laptop, dedicated graphics with an NVidia chip.  I'm doing a dual-boot until I can verify that I can handle all my video editing needs with Ubuntu alone, but...  I can't get the NVidia drivers to work, so the system is using the onboard Intel 520 chip.  Nouveau drivers are in use, and no matter which rabbit hole I go down with installing Nvidia drivers, there are no options in the "Additional Drivers" tab besides the onboard graphics.  The dedicated graphics was the whole reason behind this laptop purchase.

SO:  While installing from Nvidia's home page, I get an error message about the X server running.  Following the guidance, I log out, try Control-Alt-F1.. Nada.  Is there a new way with Xenial to get at this?

Thanks for your help!

---

### Post by Geoffrey_Arndt on 2016-10-10
OK, please verify your hardware - "New Lenovo Laptop" just doesn't cut it.   If the system has dual video chipsets, there is a way to handle that different from the normal "additional drivers" method in Settings.    The Intel 520 chip will provide pretty decent hardware performance for all but higher end gaming and some CAD/Engineering software.    But to activate the Nvidia, other methods are involved.

If you have this type of dual-graphics system . . . check out this link:  [http://askubuntu.com/questions/610418/ubuntu-14-04-dual-graphics-nvidia-doesnt-work](http://askubuntu.com/questions/610418/ubuntu-14-04-dual-graphics-nvidia-doesnt-work)

---

### Post by GuppiePilot on 2016-10-10
The computer is a Lenovo P40, the discrete graphics card is NVIDIA Quadro M500M with 2GB memory.  My system recognizes the 16Gb RAM installed, but not the Nvidia's 2Gb.

Thanks for the link, but I don't have Bumblebee, and I do have Nvidia's Xserver settings app --  there's just nothing there.

So I'd like to try to get around the X server issue.  As I mentioned above, I log out, hit control - Alt - F1, and nothing happens.  I can't find alternate routes.  Your help is appreciated, thanks!

---

