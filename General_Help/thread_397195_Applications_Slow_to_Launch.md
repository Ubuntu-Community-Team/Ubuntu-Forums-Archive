---
title: "Applications Slow to Launch"
date: 2007-03-30
forum: General Help
---

### Post by El_Matthews on 2007-03-30
Hello everybody,


I have a strange problem on my pc, when I launch an application it takes a long time before appearing on the screen. Even nautillius when I start it from Places/Home Folder. Once the applications are started everything works fine.

I use a P4 3GHZ with 1GB of Ram. NVIDIA G-Force 6600 GT with nvidia drivers installed.

I tested this on an other less performant pc in VMWARE and there the apps are faster in loading. How and where do I have to search to optimize this ?

---

### Post by gruffy-06 on 2007-03-30
There could be various problems here.

# Try disabling unnecessary startup programs in the "Services" tool
# Try uninstalling packages that you don't use
# Try installing the latest software updates

---

### Post by El_Matthews on 2007-03-31
thanks gruffy-06

I checked everything that's started in /etc/rc2.d and stopped everything I didn't need and indeed the pc seems to be faster.

Now how can I check if all hardware is working at correct speeds.
example I have two SATA drives. How can I check the speed the are working ? (100/133/150 mb/s)
memory: which bus speed?

---

### Post by kellemes on 2007-03-31
Changing WM can also **greatly** improve performance.
Assuming you're on Gnome I recommend to give XFCE a try..

---

