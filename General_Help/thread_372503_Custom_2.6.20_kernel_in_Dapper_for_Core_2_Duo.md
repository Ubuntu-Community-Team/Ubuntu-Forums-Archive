---
title: "Custom 2.6.20 kernel in Dapper for Core 2 Duo"
date: 2007-02-28
forum: General Help
---

### Post by dannyboy79 on 2007-02-28
Hi there,
I am getting an E4300 and a ASRock 775dual-VSTA motherboard. I am going to be running 1.5gb PC3200 DDR400 ram, a XFX GeForce 6200 128mb agp video card. I am currently running Dapper and want to stick with that due to doing a lot of customization and having all my apps running correctly etc etc. It is my understanding that I can compile a custom kernel to get better performance out of my machine and linux in general according to the thread entitled Master Kernel or something or other. I want to do this. I am wondering however what is the difference between using patches provided by Con Kolivas from here: [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)
or just using the patches provided by kernel.org? Also, if I do this, am I going to want to use the current .config that is found within my /usr/src/ sub-folders? I currently have 2.6.15-28-686 installed. Then if I do this over ssh, I will want to use menuconfig and not xconfig correct? Also, I understand by reading Con's guide here ([http://ck.kolivas.org/faqs/walkthrough.txt](http://ck.kolivas.org/faqs/walkthrough.txt)) that I can run: 

make oldconfig

and this will only prompt you for any new features in the kernel which are usually
easy enough to understand, but generally if you don't know then choosing the
default recommended by the script just by pressing enter will do.


I guess the part that I am unsure on yet, is that the guide at Master Kernel (within this forum) states something about either using menuconfig or xconfig to configure the kernel, do I still need to do this if I use the .config already on my machine? What things are set with this config from Ubuntu that I may be missing or whatnot. Are there any options that I specifically need to look for due to my hardware I have mentioned above? 

Last question: if Dapper still updates kernel versions (not sure if that's the terminology but I know that I have updated from 2.6.15-23 to now 2.6.15-28), which causes me to have to reinstall nvidia and sometimes make sure that grub was updated corectly than why don't they just update to the newest kernel thru synaptic? Also, after I compile and install this new kernel, will I get the updates thru synaptic (example: 2.6.20-xx or whatever) like I did for the 2.6.15 kernel? or will I have to keep compiling new kernels applying the newest patches. If some1 could please answer ALL my questions I would really appreciate it. I can honestly say that out of over 1450 posts that I have made, 95% of them are helping others and I rarely ever ask for help, so please, help me here.

---

### Post by dannyboy79 on 2007-03-06
please some1 help.

---

