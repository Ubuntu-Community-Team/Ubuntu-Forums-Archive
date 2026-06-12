---
title: "Unable to recognize the graphic card"
date: 2012-12-18
forum: General Help
---

### Post by marcoZazza on 2012-12-18
Hello Everyone,

I'm having this issue with my graphic card and I'm sure there is a way to fix it.

I installed ubuntu on my laptop that has a Nvidia GeForce 8600M GT turbocache graphic card and it seems like it's not recognizing it.
If I open AllSettings/Details it say that the graphic card is Unknown.

I went already to the Nvidia website and downloaded this drivers at this [LINK]("http://www.geforce.com/drivers/results/52241").
Even after installing this driver is still not recognizing it.

Is there something I can do ?

Also the computer is responding really slow, everytime you click something (even to open the System Settings ) it takes something like 8 to 10 second before the actual opening of the folder/file/software, is this issue connected to the graphic card or is something else?

thanks a lot for the help

Marco

---

### Post by bogan on 2012-12-18
Hi!, **marcoZassa**, You Posted:> If I open AllSettings/Details it say that the graphic card is Unknown.There is a known bug in System Settings that does this, and often says a Desktop is a Laptop.

We need more info about what faults appear with the graphics, apart from the slowness.

Have you run nvidia-settings? or 'NVIDIA X Server Settings'? if so is the Graphics and its driver recognised there??

If you are running 12.10, did you install the 'linux-headers-generic', and remove any previous driver, before installing the nvidia.com Download?

What is the output from:```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan.**

---

### Post by ibjsb4 on 2012-12-18
I do not run one of these 8600's but found a several hits here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Nvidia+GeForce+8600M+GT&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Nvidia+GeForce+8600M+GT&as_qdr=all&sa=Google+Search&lang=en)

And stopped looking when I found this.

[http://ubuntuforums.org/showthread.php?t=1974689](http://ubuntuforums.org/showthread.php?t=1974689)

Good luck

---

