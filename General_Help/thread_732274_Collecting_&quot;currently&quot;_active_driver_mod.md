---
title: "Collecting &quot;currently&quot; active driver modules for kernel build configuration?"
date: 2008-03-22
forum: General Help
---

### Post by bobby_d on 2008-03-22
Hi all, 

I am not sure if this is the right forum to ask this in - if so please move.. 

I have started using Ubuntu only recently (8.04) and was forced to try develop my own driver as a kernel module. One of the biggest problems I encountered was that at certain times, I needed to rebuild the kernel, which following the tutorials around here, is not a difficult procedure. However, it takes almost an hour on my machine. 

I have noticed that the sources offer a configuration utility via make menuconfig, which will allow for graphical editing of the configuration file (which I have not used directly yet) - and I have tried it out. But even though one may import the original config file of the default build, I can notice that the bulk of the compile time is spent in compiling /drivers - most of whom I don't need to run my hardware (for instance, ISDN drivers are being built, which I don't use as I have no comparable hardware). 

I tried to use the make menuconfig to deselect some modules and thereby decrease the build time, but a couple of times it turned out I have deselected a module needed for other modules (that I use) to work, and that is a costly mistake, as then I have to rebuild and again wait an hour. 

I was therefore wandering, if there exists a utility, that would scan/read/iterate through all currently active modules (at least driver ones), once one is logged into Gnome, check their dependencies, and then generate a configuration file for the kernel sources build engine, which would contain the minimal needed Ubuntu build + those required by dependencies of the currently active/loaded ones - and nothing else? 

Then I could log in into a plain default stable installation, run the utility and thereby have included say, serial and parallel driver modules (that I use) for compilation - but not ISDN and the like that I don't use... Then I wouldn't have to deselect anything to make the build smaller (so less chance of making errors that will cost hours of rebuild) - only select when I need something in addition. 

If there isn't such I utility, I was just wandering if there exists something in the Linux/Gnome/Ubuntu system, that would make the existence of such a utility near impossible? 

Thanks for any comments...

---

