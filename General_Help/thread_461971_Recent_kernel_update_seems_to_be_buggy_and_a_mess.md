---
title: "Recent kernel update seems to be buggy and a mess"
date: 2007-06-02
forum: General Help
---

### Post by ss0007 on 2007-06-02
H i All,
I was recently updated to latest kernel by the Update notification applet. The kernel version was updated to 2.16.20-16 generic.As soon as it was done , the following problems started ,
1. My folder shortcuts in the nautilus disappeared
2. I could not boot to Ubuntu unless the "root" partition value in the Grub menu was modified.
3. My Windows partitions listed in my desktop disappeared.
4. My daily apps like azureus, rthymbox stopped working since I store my downloads to a Windows partition.

Weird issues:
1. As I opened Home folder in the nautilus, I spotted the Wndows partitions labels on the left side (Places section) , when I double clicked it, gksudo was invoked for admin password and nothing happened for a while , so I again dbl clicked the same drive and now the folder contents appeared on the right side.Also ,the desktop shortcut for that drive appeared back in desktop.I have to repeat this for all drives .

2. As I navigated to /media folder , it seems that the latest kernel have not created any Windows partitions in it. The drive contains empty folders like sda1,sda5, ... 

Did you spot the same issues ?
Any quick replies to revert back to normal (using the same kernel) ?

---

### Post by oleoleole on 2007-06-02
I heard the new kernel-update takes advantage of normal device-loaction again, like /dev/hdxX and not /dev/sdxX. Its anyway annoying that they cant deside what too choose, and Im not using UUID instead of device-locations either (because it has been buggy here).

---

### Post by ss0007 on 2007-06-02
yep , I also agree . Using UUID is very confusing and cryptic sometimes ,like when 
we edit the grub conf file , indicating /dev/sda1 is more intutive than indicating UUID=3f321a90-3056-4e6d-852e-eb22d5c681db .

---

