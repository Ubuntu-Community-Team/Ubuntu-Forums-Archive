---
title: "Nvidia drivers + 1680 x 1050 display problem"
date: 2008-06-24
forum: General Help
---

### Post by prickly on 2008-06-24
My Ubuntu (Hardy) desktop suffers from one main annoying problem, which is that after almost every update I have to uninstall the Nvidia drivers, reboot, and then enable the Nvidia drivers and reboot again to get back to a 1680 x 1050 display, otherwise I am stuck at 640 x 480.

My desktop is connected to an IOGear swictchbox which is in turn connected to my monitor. 

After uninstalling the Nvidia drivers and rebooting sometimes the system will start at 1680 x 1050 and if it does it flickers horribly and is not usable, otherwise the system starts at 640 x 480 and I have to go through the whole uninstall / reinstall Nvidia drivers thing again. 

In fact I had to install Ubuntu on a standard monitor 1024 x 768 just to install the OS as I could not do a graphical display installation whilst connected to my widescreen monitor.

So are there driver issues for widescreen monitors in general or is this related to the fact that I am connected through a switchbox?

This is my motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157108](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157108)

My GPU is the NVidia 6100.

This is my monitor: [http://www.newegg.com/Product/Product.aspx?Item=N82E16824001096](http://www.newegg.com/Product/Product.aspx?Item=N82E16824001096)

This is my switchbox: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817107419](http://www.newegg.com/Product/Product.aspx?Item=N82E16817107419)

I can post further information if it will help once I get home. 

Many thanks.

---

### Post by jimv on 2008-06-24
Kinda odd...it's like the updates aren't installing the new Nvidia modules or something.  I'm running a 6100 on this laptop and I ahven't had that problem, but I also used EnvyNG to install the drivers.

---

### Post by central419 on 2008-06-24
I think it does have to do with the switchbox.
I'm running dual monitors, and 1 is happy to stay in the right resolution, but the other which is connected thrue a KVM also has problems staying at the resolution I told to be at.

My solution is to run "sudo nvidia-xconfig" once, and restart X (ctrl+alt+backspace).
I login again, and the resolution is correct. Usually. Sometimes it takes a couple attempts to persuade it to do it right.

---

### Post by prickly on 2008-06-25
Thanks Central, I will give that a go next time it happens.

---

### Post by prickly on 2008-06-27
Actually, now that I am making sure that I boot up with the switchbox on the machine that I am booting all of the time I have not had any issues :)

---

