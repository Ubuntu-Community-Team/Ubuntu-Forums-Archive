---
title: "Multiple Switch User/Lock results in Black Screen."
date: 2015-11-22
forum: General Help
---

### Post by 77_GCSX on 2015-11-22
First the usually: System = Ubuntu 14.04 LTS. Kernel 3.13.0-61 Generic Intel Core i7 CPU.

We have 6 users on our system. After switching/locking accounts multiple time we'll get a black screen with a black X for a mouse. The only way to resolve this is to do a CTRL-ALT-F4 and login on and do a sudo reboot.

Anyone else have anything like this?

If anyone needs more info just ask.

Thanks, Paul

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

Could you detail me that graphics card do you have?

---

### Post by 77_GCSX on 2015-12-07
GeForce GT 610/PCIe/SSE2 using the NVIDIA binary driver - version 331.113 from nvidia-331 updates (proprietary)

I know it's outdated but it's been serving me just fine for the past year or so with no issues.

Thanks.

---

### Post by Ricardo_Velasco on 2015-12-07
Greeting:

Investigate a little more about the issue and have your card seems outdated as you said and here I say the steps to install the new drivers
> sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get install nvidia-340 nvidia-settings

That is a source :

Try this option first .



Another source indicates that Nvidia added his own PPA to update the proprietary drivers from Nvidia.

IF you want this PPA also pointing it :


> sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update

If after this actulizacion the same problem remains I indicated the following instructions :


Switch to console (Ctrl-Alt-F1) and stop lightdm: sudo service lightdm stop

Disable gpu-manager by commenting out everything in /etc/init/gpu-manager.conf ([B]If someone could clarify this part I would appreciate)

[/B]Switch to nvidia mode by doing to sudo prime-select nvidia

The plain, unformatted where the next step is on this page :

[http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/](http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/)

After:

> sudo chattr +i /etc/X11/xorg.conf                      
     
 

and:

> sudo lightdm start

                     
The site was originally located where the solution is:

[http://vxlabs.com/2015/02/05/solving...-screen-issue/]("http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/")


Thank you

---

