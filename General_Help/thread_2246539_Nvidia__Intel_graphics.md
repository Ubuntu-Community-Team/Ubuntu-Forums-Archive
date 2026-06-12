---
title: "Nvidia / Intel graphics"
date: 2014-10-01
forum: General Help
---

### Post by Ilgazman on 2014-10-01
Hi there, 

I've installed Ubuntu 14.4 today and I got some problems with it but I solved and almost finish to using it as a Developer. But I have really important problem about my graphic card. I think this is related with my last OS setup. I changed the bios setting to Integrated for installing, but now I changed it to switchable. But something goes wrong. I can't solve it. Is there any solution for finding my Graphic Card's driver and updates? My graphic card is **nVidia GeForce 610M** **1GB**. So, what should I do? 


Regards,
Abdullah

---

### Post by Mark Phelps on 2014-10-01
Sounds like you may have "integrated graphics" -- which is a really hard problem to address in Linux, as the drivers for this are generally not available.

To see what you have, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  Post that line information back here.

Also, you should tell us the make and model PC you're using.

---

### Post by Ilgazman on 2014-10-01
> **Mark Phelps said:**
> Sounds like you may have "integrated graphics" -- which is a really hard problem to address in Linux, as the drivers for this are generally not available.

To see what you have, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  Post that line information back here.

Also, you should tell us the make and model PC you're using.


I think this is my **nVidia Card**:

01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce 610M] (rev a1)

And this is Integrated one: 
(Intel HD Family 3000 Series)

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by grahammechanical on 2014-10-01
The best I can offer is these links. The first link is now outdated as 14.04 was released at the end of April and you should already have the the latest Nvidia driver if you ticked the box "Install third party software" during the installation process. If you did not do that the, go to System Settings>Software and Updates>Additional Drivers tab and use that to install an Nvidia driver.

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Keep in mind that Nvidia Optimus technology was available in machines on the market for many months before Nvidia even started work on a Linux driver.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

This is the best that open source developers can offer

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Regards.

---

### Post by Ilgazman on 2014-10-02
> **grahammechanical said:**
> The best I can offer is these links. The first link is now outdated as 14.04 was released at the end of April and you should already have the the latest Nvidia driver if you ticked the box "Install third party software" during the installation process. If you did not do that the, go to System Settings>Software and Updates>Additional Drivers tab and use that to install an Nvidia driver.

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Keep in mind that Nvidia Optimus technology was available in machines on the market for many months before Nvidia even started work on a Linux driver.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

This is the best that open source developers can offer

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Regards.

I did what you suggested. There is no problem anymore, especially my cursor problem that sometimes cursor was disapearred. Thank you so much!

Regards,
Abdullah

---

