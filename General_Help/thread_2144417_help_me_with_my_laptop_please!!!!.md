---
title: "help me with my laptop please!!!!"
date: 2013-05-12
forum: General Help
---

### Post by yaqoobs on 2013-05-12
first of all, hello to the world of ubuntu.

i have a lenovo thinkpad T420, and it uses an Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller  NVIDIA Corporation GF119M [Quadro NVS 4200M] graphic card (got the driver info from i-nex), i went to software and updates and clicked on the additional drivers, it was blank.

how can i install the latest and most stable NVIDIA drive for my laptop.

note: i am using ubuntu 13.04

thanks in advance for everyone who is willing to help, and if you need any other information about any topic, i'll be willing to help

---

### Post by dino99 on 2013-05-12
here is an old post about that model: [http://pauldreik.blogspot.fr/2011/11/ubuntu-1110-on-thinkpad-t420.html](http://pauldreik.blogspot.fr/2011/11/ubuntu-1110-on-thinkpad-t420.html)

but you might also read these ones after googling around "ubuntu t420"

---

### Post by grahammechanical on 2013-05-12
The link provided by dino99 says this

> [FONT=Georgia]The computer has a core i5 processor, a 1600x900 screen with a nvidia graphics card and an integrated gpu on the processor.[/FONT]

Does your machine have both the Nvidia graphics card and an intergrated gpu? If so then you have Nvidia Optimus technology and the most likely reason that there is not an option to install a proprietary video driver in Additional Drivers is because a proprietary driver does not exist. Nvidia only started developing a driver for optimus technology a few weeks ago. For months open source developers have been working on a driver for Nvidia Optimus technology. The project is called Bumblebee.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

This may be what you need.

Regards.

---

