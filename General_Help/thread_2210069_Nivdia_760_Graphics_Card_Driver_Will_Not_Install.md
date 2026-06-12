---
title: "Nivdia 760 Graphics Card Driver Will Not Install"
date: 2014-03-08
forum: General Help
---

### Post by ryan61 on 2014-03-08
Hello once again Forum! I have a Nivdia 760 graphics card. I run terminal as root and try to install it. I get an error saying that I need to have X Server turned off. I have tried pressing CTRL+ALT+F2 to try it. I get passed the X Server but now i'm missing a file and the installation cannot be complete.
 
Thank You For Your Time!
ryan61:)

---

### Post by dannyboy79 on 2014-03-08
where did you download and store the .run file? i install the .run file from the nvidia website all the time, in fact I just installed 334.21. I have the EVGA GTX 760 SC 2GB edition. What driver are you currently running?

---

### Post by ryan61 on 2014-03-08
I have downloaded it Nivdia. It was saved in downloads. I did cd /home/USER NAME/Downloads then I did sh NVIDIA-Linux-x86_64-334.16.run the error happened after that. Thanks for the help!

---

### Post by sffvba[e0rt on 2014-03-08
*Thread moved to **General Help**.*

Does the drivers in "Additional Drivers" not work for your card? ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia))

---

### Post by ryan61 on 2014-03-08
I do not know if this effects anything though but my graphics card is VESA: GK104 Board - 20040010 it tells me


But for my drivers I have NIVDIA binary Xorg driver, kernel modulr VDPAU libary from nvidia-319-updates and
NIVDIA binary Xorg driver, kernel modulr VDPAU libary from nvidia-331-updates

---

### Post by sffvba[e0rt on 2014-03-08
> **ryan61 said:**
> I do not know if this effects anything though but my graphics card is VESA: GK104 Board - 20040010 it tells me


But for my drivers I have NIVDIA binary Xorg driver, kernel modulr VDPAU libary from nvidia-319-updates and
NIVDIA binary Xorg driver, kernel modulr VDPAU libary from nvidia-331-updates

From additional drivers I typically select the 319 drivers, but the 331 drivers should also work.

---

### Post by ryan61 on 2014-03-08
> **not found said:**
> From additional drivers I typically select the 319 drivers, but the 331 drivers should also work.

From my understanding it will not matter if it does not say NVIDIA GTX 760 as my graphics?

---

### Post by sffvba[e0rt on 2014-03-09
> **ryan61 said:**
> From my understanding it will not matter if it does not say NVIDIA GTX 760 as my graphics?

As soon as you have the proprietary drivers installed you should see the correct name for your card being displayed in the **Details **window.

[IMG]http://www.question-defense.com/wp-content/uploads/2012/06/ubuntu-version-details-window.gif[/IMG]

---

### Post by jacob21 on 2014-03-09
I installed the driver for my GTX 760 by stopping X.

```
sudo service lightdm stop
```

Then CTRL+ALT+F1 and install the .run file.

```
sh NVIDIA-Linux-x86_64-331.49.run
```

---

