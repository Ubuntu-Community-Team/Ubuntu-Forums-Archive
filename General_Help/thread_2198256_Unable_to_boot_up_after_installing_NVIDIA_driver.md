---
title: "Unable to boot up after installing NVIDIA driver"
date: 2014-01-07
forum: General Help
---

### Post by rmcellig on 2014-01-07
I just installed Xubuntu 13.10 on my laptop. I should have left well enough alone. When I went to settings/Additional Drivers, my video driver was set to Nouveau. I went and changed it to NVIDIA 173. After a restart of my machine, all I get is a full screen NVIDIA logo and then a black screen. How do I make things right again?

Do I have to restart in Recovery mode and do something in the terminal or is there another way of getting my desktop back.

---

### Post by QIII on 2014-01-08
Hello!

What is the model of the GPU?  Does the machine have Intel/NVIDIA hybrid graphics?

---

### Post by jeanjd63 on 2014-01-08
Hello, 
You can first suppress the nvidia drivers :
When you got the black screen, you do CTRL+ALT+F1 and then you connect with yours users password and you do :
**sudo  apt-get  purge  "nvidia *"**
then
[B]sudo  reboot 
[/B]

---

### Post by rmcellig on 2014-01-08
I have a HP DV 2000 laptop.  The base model uses the integrated Intel Graphics Media Accelerator (GMA) 950 graphics renderer to drive the display.


jeanjd63

    Re: Unable to boot up after installing NVIDIA driver
    Hello,
    You can first suppress the nvidia drivers :
    When you got the black screen, you do CTRL+ALT+F1 and then you connect with yours users password and you do :
    sudo apt-get purge "nvidia *"
    then
    sudo reboot 

I am unable to go to a virtual desktop using ctrl-alt-f1. All I see is a small non flashing white line in the upper left hand corner of the screen.

---

### Post by rmcellig on 2014-01-08
I followed the purge instructions and now everything works fine. I had to start up with a previous kernel for this to work. Thanks for the help!!

---

