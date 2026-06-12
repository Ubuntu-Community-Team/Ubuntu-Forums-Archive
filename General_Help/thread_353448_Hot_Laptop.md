---
title: "Hot Laptop"
date: 2007-02-04
forum: General Help
---

### Post by hareti on 2007-02-04
Hello,

Why does my laptop run hotter in Linux than it does in Windows? It is an Acer Aspire 1710. When it first starts up the fans run full speed but as soon as the kernel loads they drop down to just on. They stay this way until I do ANYTHING. If I open a terminal, view a picture, - anything that loads the cpu at all, the fan speeds start ramping up. Even if I just leave the laptop on but not doing anything it runs hotter to the touch than it does in windows.

Is there any way I can adjust the cpu frequency or something to make it run cooler?

Thanks

---

### Post by raja on 2007-02-04
As you may know, Ubunut has only frequency scaling. However, if you want to control your cpu frequency manually or determine the 'governor' to be used, you can follow this [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/).  I have this working and it provides a lot of flexibility !

---

### Post by hareti on 2007-02-04
Thanks raja,

I'll take a look...

---

### Post by hareti on 2007-02-04
After reading the frequency scaling article. It says to check /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies. My system doesn't have this directory, it only goes as far as /sys/devices/system/cpu/cpu0/ so I guess I don't have this feature.

There must be some sort of control though - when it runs on batterys it is much cooler and a bit slower. Is there any other way the kernel can control the power used by the CPU?

 - Also, windows alters the speed depending on whether it is running on batteries or mains, and the temp changes accordingly.

---

