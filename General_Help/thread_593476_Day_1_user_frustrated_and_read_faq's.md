---
title: "Day 1 user frustrated and read faq's"
date: 2007-10-27
forum: General Help
---

### Post by petalumaslim on 2007-10-27
heya,

I'm interested in using Ubuntu for a BOINC. "New to Ubuntu" sounds a like a great topic but provides absolutely no information as to how to navigate a new os. the help section is completely useless for day one users!!!!  After 20 minutes i stumbled across the wifi section and was able to get online. Subsequent to that i downloaded Boinc and an Nvidia driver. both are on my desktop waiting to be installed. when i click on them i get a message saying could not open file. needless to say i have found ubuntu a less than satisfying experience and would appreciate some help.

thanks,
ken

p.s. 
can you update you're new to ubuntu help topic to provide new user's with a step by step tutorial ?
thank you

---

### Post by SPr on 2007-10-27
Click System>Administration>Synaptic Package Manager. Enter your password. Search for BOINC and nVidia. Select what you need and click "Apply". Synaptic will download and install them automatically.

Have you made a backup of your Ubuntu partition yet? When I first began using Ubuntu I had to re-installed it a few times because I kept breaking things. Having a backup of a fresh install would be much quicker.

---

### Post by Sunforge on 2007-10-27
If you're running Gutsy or Feisty you will find that there is a "restricted drivers" section which will list which restricted drivers you can enable for your computer.

In either version go to
system - administration - restricted devices manager
input your password
check the box to enable the driver
apply changes

This should download the nvidia driver from the repositories and you should be good to go.

If you want to enable the latest Nvidia driver you could try the ENVY script, which I haven't tried but has had a good response from the forums:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I'd recommend trying the restricted drivers available in Ubuntu unless you've had no luck with them.

If you want a general Ubuntu specific how to guide you can try this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04)
This applies to Feisty and Gutsy (with a few exceptions)

The third and least favoured option, if you're new to Linux and Ubuntu is downloading the latest driver from NVIDIA which is a shell script, from here:

ttp://www.nvidia.com/object/linux_display_ia32_100.14.19.html

Move it to your home folder and then fire up ye olde commande prompte (tm) and type: "sh NVIDIA-Linux-x86-100.14.19-pkg1.run" to get the thing installed.

If you've downloaded a .EXE file it's a Windows only binary and won't work under Linux.

---

