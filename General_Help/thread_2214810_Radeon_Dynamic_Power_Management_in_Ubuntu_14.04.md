---
title: "Radeon Dynamic Power Management in Ubuntu 14.04?"
date: 2014-04-03
forum: General Help
---

### Post by acutbal on 2014-04-03
I've just installed Ubuntu 14.04, I'm not sure if  Radeon  Dynamic Power Management is working because the laptop is hotter than my  previous Ubuntu 12.04.4 with kernel 3.11 plus adding the kernel  parameter "radeon.dpm=1" added in line GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash".


  Please, could someone confirm that DPM is active out of the box in kernel 3.13?


  Thank you very much and very best regards!!

---

### Post by acutbal on 2014-04-03
Well, finally I decided to do as usual, I've added the kernel  parameter "radeon.dpm=1", sudo update-grub, sudo reboot and voilà, the laptop is cooler again. So, I think that DPM isn't enabled by default in Ubuntu 14.04. Why? I don't know, perhaps because it's still in beta...

[http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04/326858#326858](http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04/326858#326858)

Very best regards!!

---

### Post by acutbal on 2014-04-22
Well, today I've installed again Ubuntu 14.04 but now with an iso downloaded directly from its site... And again I think DPM isn't activated by default, and now it isn't a beta version. 
Please, I'll really appreciate if some could confirm me DPM default activation.

Thank you very much!!

---

### Post by pme 72 on 2014-04-25
DPM did not seem to be activated by default after a fresh install last weekend for me in 14.04 either. Adding the kernel parameter you mentioned enabled dpm as it did for me in 13.10. Good to go.

---

### Post by acutbal on 2014-04-28
That confirms my suspicions, DPM is not enabled by default in Ubuntu 14.04, even though it had announced otherwise.

Thank you very much!!

---

### Post by acutbal on 2014-05-13
Well... again with the DPM!! Another fresh install and again doubts... 

After run in terminal:
dmesg | grep radeon

I find this in the return:
[   16.691793] [drm] radeon: dpm initialized

So, in theory DPM is enabled. But I remember that with Ubuntu 12.04.4 + kernel 3.11 with parameter "radeon.dpm=1" or Ubuntu 14.04 + parameter "radeon.dpm=1" the laptop is cooler.

Also, I follow this guide:
[http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature](http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature)

In this guide it's suggested to run this command:
cat/sys/kernel/debug/dri/64/radeon_pm_info

And the supposed return is:
uvd    vclk: 0 dclk: 0
power level 0    sclk: 22000 mclk: 25000 vddc: 900

But when I run this command this is my return:
default engine clock: 500000 kHz
current engine clock: 500000 kHz
default memory clock: 667000 kHz

I've tried several differents directories (as also suggested in the guide) but the return is always the same. In fact, there are some files called "radeon_pm_info".

In the other hand, if I see this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This page talks about the kernel 3.11 and later:
"Kernel 3.11.x (Ubuntu 13.10/Saucy) and Later

You can enable DPM on RadeonHD cards by adding a boot parameter. This should greatly help power consumption, especially when idle. To do so, edit /etc/default/grub and add the 'radeon.dpm=1' to the GRUB_CMDLINE_LINUX_DEFAULT line, so it would look something like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"
After you save/quit the text editor, update grub:

sudo update-grub".

And this page is updated on 19-4-2014, two days after release Ubuntu 14.04. I'm really confused... Is DPM enabled or not?

Best regards!!

---

### Post by pme 72 on 2014-05-13
Does not sound right to me either. In 13.10 and 14.04 before enabling dpm, dmesg | grep drm would return output which included a line like:
> [4.936180] [drm] radeon: power management initialized

And sudo cat /sys/kernel/debug/dri/0/radeon_pm_info would look like this with an HD3000 RS780: 
> default engine clock: 350000 kHz
current engine clock: 343680 kHz
default memory clock: 800000 kHz

dmesg | grep power
> [    4.936180] [drm] radeon: power management initialized

 After enabling dpm by editing Grub adding radeon.dpm=1, the same line in the output of dmesg | grep drm reads:
> [   13.389832] [drm] radeon: dpm initialized

And sudo cat /sys/kernel/debug/dri/0/radeon_pm_info returns:
> uvd    vclk: 0 dclk: 0
power level 0    sclk: 11000 mclk: 30000 vddc: 1100

And dmesg | grep power:
> [   12.400348] == power state 0 ==
[   12.400358] 		power level 0    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400360] 		power level 1    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400361] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400366] == power state 1 ==
[   12.400376] 		power level 0    sclk: 11000 mclk: 30000 vddc: 1100
[   12.400377] 		power level 1    sclk: 30000 mclk: 50000 vddc: 1100
[   12.400379] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400381] == power state 2 ==
[   12.400388] 		power level 0    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400389] 		power level 1    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400391] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100
[   12.400394] == power state 3 ==
[   12.400400] 		power level 0    sclk: 11000 mclk: 75000 vddc: 1100
[   12.400401] 		power level 1    sclk: 30000 mclk: 75000 vddc: 1100
[   12.400402] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100
[   12.401496] switching from power state:
[   12.401506] 		power level 0    sclk: 60000 mclk: 75000 vddc: 1100
[   12.401507] 		power level 1    sclk: 60000 mclk: 75000 vddc: 1100
[   12.401508] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100
[   12.401511] switching to power state:
[   12.401516] 		power level 0    sclk: 11000 mclk: 30000 vddc: 1100
[   12.401517] 		power level 1    sclk: 30000 mclk: 50000 vddc: 1100
[   12.401518] 		power level 2    sclk: 60000 mclk: 75000 vddc: 1100




---

### Post by acutbal on 2014-05-15
Thanks for your response!! 

Definitely I think that in some cases for some weird reason Dynamic Power Management in some cases it isn't enabled in Ubuntu 14.04. Why? I don't know... 

After adding again  "radeon.dpm=1" the laptop gets cooler. And the various commands returns are now ok.

sudo cat /sys/kernel/debug/dri/0/radeon_pm_info - sudo cat /sys/kernel/debug/dri/64/radeon_pm_info
uvd    vclk: 0 dclk: 0
power level 0    sclk: 20000 vddc_index: 

dmesg | egrep 'drm|radeon'
15.513870] [drm] radeon: dpm initialized

dmesg | grep power
[   15.507045] == power state 0 ==
[   15.507052]         power level 0    sclk: 50000 vddc_index: 2
[   15.507053]         power level 1    sclk: 50000 vddc_index: 2
[   15.507056] == power state 1 ==
[   15.507061]         power level 0    sclk: 20000 vddc_index: 2
[   15.507062]         power level 1    sclk: 50000 vddc_index: 2
[   15.507064] == power state 2 ==
[   15.507069]         power level 0    sclk: 20000 vddc_index: 1
[   15.507070]         power level 1    sclk: 20000 vddc_index: 1
[   15.507072] == power state 3 ==
[   15.507077]         power level 0    sclk: 50000 vddc_index: 2
[   15.507078]         power level 1    sclk: 50000 vddc_index: 2
[   15.507080] == power state 4 ==
[   15.507085]         power level 0    sclk: 38000 vddc_index: 1
[   15.507086]         power level 1    sclk: 38000 vddc_index: 1
[   15.507088] == power state 5 ==
[   15.507093]         power level 0    sclk: 38000 vddc_index: 1
[   15.507094]         power level 1    sclk: 38000 vddc_index: 1
[   15.508644] switching from power state:
[   15.508655]         power level 0    sclk: 50000 vddc_index: 2
[   15.508657]         power level 1    sclk: 50000 vddc_index: 2
[   15.508659] switching to power state:
[   15.508664]         power level 0    sclk: 20000 vddc_index: 2
[   15.508665]         power level 1    sclk: 50000 vddc_index: 2
[   18.542482] == power state 0 ==
[   18.542491]         power level 0    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.542492]         power level 1    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.542493]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.542496] == power state 1 ==
[   18.542502]         power level 0    sclk: 15700 mclk: 20000 vddc: 1120 vddci: 0
[   18.542504]         power level 1    sclk: 40000 mclk: 50000 vddc: 1120 vddci: 0
[   18.542505]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.542507] == power state 2 ==
[   18.542512]         power level 0    sclk: 50000 mclk: 80000 vddc: 950 vddci: 0
[   18.542513]         power level 1    sclk: 50000 mclk: 80000 vddc: 950 vddci: 0
[   18.542515]         power level 2    sclk: 50000 mclk: 80000 vddc: 950 vddci: 0
[   18.542516] == power state 3 ==
[   18.542522]         power level 0    sclk: 40500 mclk: 80000 vddc: 1120 vddci: 0
[   18.542523]         power level 1    sclk: 40500 mclk: 80000 vddc: 1120 vddci: 0
[   18.542524]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.542526] == power state 4 ==
[   18.542532]         power level 0    sclk: 15700 mclk: 20000 vddc: 900 vddci: 0
[   18.542533]         power level 1    sclk: 15700 mclk: 20000 vddc: 900 vddci: 0
[   18.542534]         power level 2    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542536] == power state 5 ==
[   18.542541]         power level 0    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542542]         power level 1    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542544]         power level 2    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542545] == power state 6 ==
[   18.542551]         power level 0    sclk: 45000 mclk: 50000 vddc: 900 vddci: 0
[   18.542552]         power level 1    sclk: 45000 mclk: 50000 vddc: 900 vddci: 0
[   18.542553]         power level 2    sclk: 45000 mclk: 50000 vddc: 900 vddci: 0
[   18.542555] == power state 7 ==
[   18.542560]         power level 0    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542562]         power level 1    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.542563]         power level 2    sclk: 30000 mclk: 30000 vddc: 900 vddci: 0
[   18.545424] switching from power state:
[   18.545436]         power level 0    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.545438]         power level 1    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.545439]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   18.545441] switching to power state:
[   18.545447]         power level 0    sclk: 15700 mclk: 20000 vddc: 1120 vddci: 0
[   18.545448]         power level 1    sclk: 40000 mclk: 50000 vddc: 1120 vddci: 0
[   18.545450]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   40.040693] switching from power state:
[   40.040706]         power level 0    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   40.040707]         power level 1    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   40.040708]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0
[   40.040711] switching to power state:
[   40.040717]         power level 0    sclk: 15700 mclk: 20000 vddc: 1120 vddci: 0
[   40.040718]         power level 1    sclk: 40000 mclk: 50000 vddc: 1120 vddci: 0
[   40.040719]         power level 2    sclk: 75000 mclk: 80000 vddc: 1120 vddci: 0




It could be a good idea whether other users share their experiences, just for our info.

Thank you very much and best regards!! :D

---

### Post by pme 72 on 2014-05-15
Good news, you had me worried. Following the developement of the community supported open source Radeon driver has been a great learning experience. I have always enjoyed reading others' experiences.

---

