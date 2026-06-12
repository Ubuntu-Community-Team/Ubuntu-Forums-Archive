---
title: "Woeful battery life"
date: 2012-12-11
forum: General Help
---

### Post by debodas on 2012-12-11
Running Ubuntu 12.10 64bit on a laptop. Currently using MATE desktop. Battery life has been woeful no matter which desktop environment I have used. So,so much worse than windows.

Also, I am experiencing a few internal errors, which state there is a gpu error. I'm wondering if this could be a reason for the awful battery life?

Anyway, any ideas would be very much appreciated. If anyone is wondering, I have a Nvidia 610m graphics card.

---

### Post by krustenBrot on 2012-12-11
First of all: which Laptop?
What about CPU scaling? Are you using something like *cpufreq-indicator*?
Is your graphics card a standalone card or can you use optimus?

---

### Post by debodas on 2012-12-11
> **krustenBrot said:**
> First of all: which Laptop?
What about CPU scaling? Are you using something like *cpufreq-indicator*?
Is your graphics card a standalone card or can you use optimus?

[http://pricespy.co.nz/product.php?p=1192138](http://pricespy.co.nz/product.php?p=1192138) This laptop
No, I am not using any cpu scaling.
I am fairly certain it is optimus, not 100% certain though.

---

### Post by krustenBrot on 2012-12-12
Okay there a re two options you should consider:
1. CPU-Scaling: Why should your CPU waste power if you aren't running tasks that need that power?
There are several tools for this e.g. [jupiter]("https://launchpad.net/~webupd8team/+archive/jupiter") but I am going to show you how to install cpufreq-indicator its small and it gets the job done. 
Open a terminal ( *press the Windows key and type *'terminal' *into the dash *) now type:```
 sudo apt-get install cpufreq-indicator
``` ...into it and press enter - it will now look up the package and if it finds it you'll have to confirm that you want to install it. Now reboot or re-login and you should see a small indicator in the top panel. Click it for options.

Secondly, Nvidia Optimus, please check if your notebook is Optimus enabled. E.g. do you have the option on windows to run Applications with different gaphic processors? (*right click - run with graphic processor... ) *or check the driver or read the packaging information (are there two graphic cards mentioned?)Somehow you'll want to confirm that it is Optimus enabled before taking the next steps.

---

### Post by mastablasta on 2012-12-12
if oyu have optimus you will need to install bumblebee

---

### Post by debodas on 2012-12-13
Got this.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cpufreq-indicator
```

---

### Post by krustenBrot on 2012-12-13
My bad...
It is:[B] sudo apt-get install indicator-cpufreq

[/B]You can always search for packages using **apt-cache search** **NAME **e.g. *apt-cache search cpufreq* lists the correct package. :)

---

### Post by debodas on 2012-12-13
Ok, CPUfreq and bumblebee installed :)
Opened up steam for linux beta using optirun, opened fine, about to play a game and see if there is any difference.

---

### Post by Rebelli0us on 2012-12-13
The open source Nvidia driver doesn't throttle the GPU, try installing nvidia-current in Synaptic.

---

### Post by Mopar1973Man on 2012-12-13
I've installed PowerTop to see how much power each process is taking on my laptop. Also got a few tweaks in it to aid in getting the power consumption down. I've got a rather new Toshiba laptop and get 3-4 hours on the battery. Then I use Conky to monitor CPU, battery, etc.

---

### Post by debodas on 2012-12-15
Ok, I'm going to assume its definitely my graphics which are causing the issue. My Ubuntu distro is having more and more sudden hangs, and the graphics card is listed as the cause for them all.
I'll install Nvidia-current and let you know how I get on.

---

### Post by debodas on 2012-12-16
Looks like its working well now, cheers guys.

---

