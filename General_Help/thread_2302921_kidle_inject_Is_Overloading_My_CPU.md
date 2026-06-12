---
title: "kidle_inject Is Overloading My CPU"
date: 2015-11-14
forum: General Help
---

### Post by jooge on 2015-11-14
Hi folks,

For the last 5 days or so I have been having some major issues with my CPU as it shoots up to a level that almost completely freezes my computer and makes things impossible for me to work on. It appears the processes doing this are kidle_inject/0-4 all spiking to about 15 (Intel i3-3110M CPU @ 2.40GHz × 4 ). I did some research and found out that the kidle_inject helps your Intel CPU from overheating. I have a relatively new computer and have not had this happen until about 5 days ago. 

I found some documentation online about this issue: [http://askubuntu.com/questions/482307/kidle-inject-uses-cpu-power-without-apparent-reason](http://askubuntu.com/questions/482307/kidle-inject-uses-cpu-power-without-apparent-reason) & 
[https://www.kernel.org/doc/Documentation/thermal/intel_powerclamp.txt](https://www.kernel.org/doc/Documentation/thermal/intel_powerclamp.txt) - I'm having a real hard time making sense of this info as I'm not the savviest guy around.

Could someone plz in layman's terms tell me what I can and should do in order to fix this issue. My computer is pretty much at a standstill atm :(

---

### Post by matt_symes on 2015-11-14
Hi

Firstly, did this start to happen after a kernel update ?

Can you boot into an older kernel from grub and see if you still get the same issue ?

I would do this first to confirm a kernel update has caused this and then we can look to see what changed in the kernel you now have.

Kind regards

---

### Post by jooge on 2015-11-14
I did a fresh install of 14.04 on Halloween. So I did not have an old kernal on this particular HDD.

---

### Post by grahammechanical on 2015-11-14
Relatively new or not, you should still think about the possibility that the machine is overheating somehow. From the little bit I have read the purpose of powerclamp is to force the CPU to slow down to reduce the heat given off. If this action is forcing the CPU to slow down to such an extent that the user interface is unusable, then I would be seriously thinking about why there is so much overheating.

I would be thinking: Are all the fans working? Especially the CPU fans. Are the ventilation slots clear or blocked? Is dust collecting on the motherboard? You could enter the BIOS/UEFI and go to the section on Temperatures and watch the readouts of motherboard & CPU temperatures. I have Psensor installed and that has an app indicator that has a drop down menu showing the temperatures of the CPU, Motherboard, GPU & hard disk. It also shows the speed the fans are going at & allows us to set alarm trigger temperatures.

Ubuntu uses something called thernald to prevent overheating. It works with powerclamp and other stuff.

> The thermald daemon prevents machines from overheating and was introduced  in the 14.04 Ubuntu Trusty LTS release. It monitors thermal sensors and  will modify cooling controls to keep the hardware cool. Thermald uses  the available CPU temperature sensors and will keep the CPU from  overheating. If hardware supplies a skin temperature sensor then by  default thermald will endeavour to keep the skin temperature under 45  degrees C.

I am not sure if thermald is installed by default in Ubuntu 14.04. Search for it in Ubuntu Software Centre that will tell you if it is installed.

[https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues)

Regards

[URL="https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues"]
[/URL]

---

### Post by matt_symes on 2015-11-14
Hi

I would have to agree with grahammechanical about the possibility of overheating, especially if this is a new install  and you have not installed Ubuntu on this PC before, as there is no precedent for overheating *not* to happen.

Install lm-sensors and run it in a terminal.

Open a terminal and type....

```
sudo apt-get install lm-sensors
```

follow the on screen installation instructions to configure it.

When it's installed type

```
watch -n1 sensors
```

and keep an eye on the temps.

Kind regards

---

### Post by jooge on 2015-11-14
Ok, In addition to the installation of that software, I'm gonna take the computer apart and make sure the the motherboard is clean, the fans still work properly ect...

In a tutorial on doing this it says that when cleaning the CPU/GPU and heatsink it is recommended to apply thermal grease/paste. Is this necessary as I dont have any of that on hand?

---

### Post by matt_symes on 2015-11-14
Hi

> **jooge said:**
> In a tutorial on doing this it says that when cleaning the CPU/GPU and heatsink it is recommended to apply thermal grease/paste. Is this necessary as I dont have any of that on hand?

Yes it's necessary. It creates a good thermally conductive junction between the top of the CPU and the bottom of the heatsink.

It's cheap to buy but don't get the cheapest brand you can find.

Kind regards

---

### Post by jooge on 2015-11-14
Ok. Wish me luck....

---

### Post by matt_symes on 2015-11-14
Hi

> **jooge said:**
> Ok. Wish me luck....

Good luck :)

If you still get the same issue after you are confident it's not overheating, we'll investigate further.

Kind regards

---

