---
title: "system became unusable after update"
date: 2021-01-07
forum: General Help
---

### Post by aaahaaah on 2021-01-07
Hi All,
My system is Ubuntu 20.04 running on Lenovo M30-70.
Everything was perfect until today's (7 Jan 2021) update.
I can boot the system, but opening any application leads to hang up.
Mouse is still moving though.
I cannot even see the IP address in order to connect remotely.
Computer turned into a brick effectively ...
Could anyone suggest a solution besides full reinstallation?

---

### Post by Autodave on 2021-01-07
I would start by making an .iso boot disk and trying that.  If you can boot from that, then something obviously is wrong with you install.

---

### Post by GhX6GZMB on 2021-01-07
Could it be that you've done some manual program/application "cleanups"?
You won't experience problems until an update, where missing dependencies will bring the house down.

---

### Post by aaahaaah on 2021-01-07
I tried to reinstall Ubuntu desktop & unity by booting in terminal model.
Reinstallation does not help.
However, if I boot with the previous image (5.4) instead of the latest one (5.8) everything is fine again.
Something is broken in the latest update.
It looks like the problem resides in GUI part, but is difficult to say for sure because once inside the latest
image, nothing does work (even xterm).

---

### Post by kansasnoob on 2021-01-07
Try booting an earlier (older) kernel. To display grub boot menu either press (and hold) Esc (for EFI systems) or Shift (for non-EFI systems) right at the moment the BIOS screen disappears. Then select Advaced options and it'll display all installed kernels.

---

### Post by aaahaaah on 2021-01-07
Yes, I did and it works. So, the problem is with the new image based on kernel 5.8, although the update run smoothly.

---

### Post by GhX6GZMB on 2021-01-07
Just ran a sudo update/upgrade/autoremove cycle with subsequent reboot (20.04).

No problems at all.

It's more likely that you've fiddled with something you should't have.

---

### Post by sysus90065 on 2021-01-07
Same thing happened to me today. Rebooted and continually get a flashing cursor. I&#8217;ll give the older kernel suggestion a try.

UPDATE: after selecting the previous kernel, the system booted up fine.

UPDATE++: My issue was a result of a known bug with nvidia drivers: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1885344](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1885344)

---

### Post by kansasnoob on 2021-01-07
I maintain a fairly large number of PC's and I've gotten about 25 calls today. In my case most because of broken Broadcom wifi drivers. I'm really steamed that they jumped from the 5.4 version kernel to 5.8 with no notice. That was NOT the blueprint:

[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

I've not found anything googling for why the devil this change was made, but saying I'm steamed is an understatement! That said I see another 5.8 update is landing in the repos right now so we'll have to see how that one goes. I feel especially bad because some of the users involved are nursing home residents and due to COVID-19 restrictions I can't just "go in" and fix things in person. I picked up 5 laptops today and need to pick up several more tomorrow! I also don't have enough Intel wifi cards or USB wifi adapters to just go that route, although I did order a bunch more.

---

### Post by kansasnoob on 2021-01-07
> **ml9104 said:**
> Just ran a sudo update/upgrade/autoremove cycle with subsequent reboot (20.04).

No problems at all.

It's more likely that you've fiddled with something you should't have.

Not ALL hardware is effected, but it is for sure a bum kernel update!

---

### Post by t-jeske on 2021-01-21
> **ml9104 said:**
> It's more likely that you've fiddled with something you should't have.
No. Ubuntu pushed the 5.8-HWE kernel in preparation for point release 20.04.2. Unfortunately, seems like they didn't really tested it well enough.

---

