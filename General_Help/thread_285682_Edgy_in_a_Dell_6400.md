---
title: "Edgy in a Dell 6400?"
date: 2006-10-27
forum: General Help
---

### Post by zapcome on 2006-10-27
I've been an Ubuntu user for a while (I started using Hoary) and a few days ago I bought a laptop. I want to install Edgy on my laptop but after reading some threads in this forums I found out that Dapper had some problems with the fan controls, and that was causing overheating problems for some users. 

Of course, there was solution for that (just installing the i8k fan controls) and I wanna know if Edgy has support for the fan controls out of the box.

My laptop is a DELL Inspiron 6400, with a dual core 2 processor, 2 GB of RAM, Ati radeon X1400, an intel wireless network card, 120GB SATA Hard Drive, 15.4" UltraSharp Wide Screen SXGA+ TFT Display with Truelife and a Dell Wireless 355 Bluetooth Module 

My questions are :

- Does Edgy has support out of the box for the Fan controls of the Dell inspiron 6400?
- Which version of ubuntu has the best support for the Inspiron 6400 hardware?... Dapper or Edgy?

Thanks for your help!

---

### Post by coolyama on 2006-10-30
I have the same configuration as yours, last night I have installed  Edgy. I am having problems with the Intel Wifi drivers at the moment. I think my fans are not kicking in properly. I would advice you not to install it until you find proper steps to do it. At the moment, I am searching for some info on how to get the wifi working and also figure out a way to install the ATI drivers.

---

### Post by Cable on 2006-10-30
Would [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") help in installing your ATI drivers?

---

### Post by MeanGuy on 2006-11-07
Cable, that was exactly what i was looking for .. just did the steps. 
added 

Section "Extensions"
        Option      "Composite" "0"
EndSection

then restarted my machine, and it was detected just fine.
thanx.

---

