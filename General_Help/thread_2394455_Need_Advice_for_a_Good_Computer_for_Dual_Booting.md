---
title: "Need Advice for a Good Computer for Dual Booting"
date: 2018-06-16
forum: General Help
---

### Post by mountainman70 on 2018-06-16
I am in need of a good computer that will let me install Ubuntu along side of windows 10, without having to jump thru several hoops to install Ubuntu like I went thru with a Dell XPS 8900. I have a limited income and will be looking on Ebay. Any advice will be appreciated.

---

### Post by TheFu on 2018-06-16
Doing dual booting will always require "several hoops." Also, about once a year, an update from Microsoft will break Linux booting.  Knowing it will happen is part of the battle.  As you learn more, fixing it becomes less and less of a hassle.

If you get a computer new enough to support virtual machines, you can run Win10 inside a VM with Linux as the host.  Which OS is used as the hostOS will depend on your main requirements.  If you run CAD or high FPS games and those only work on Linux, then you want Linux as the hostOS.

---

### Post by yancek on 2018-06-16
I think the best place to start is at the site below which is the Ubuntu documentation page for dual booting windows 10/Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-06-16
Dell typically is one of the easier one's to install Ubuntu onto. But it does require some settings in UEFI be changed as do almost all systems.
And most others require major work arounds as they violated UEFI standard, so we have to do additional steps to get around that.
And some like Acer, need a special "trust" setting in UEFI. Not difficult once you know, but when you do not know that, it is very difficult.

What issues did you have with Dell?

And any system that is a year or two older works better than the very new systems as all the required updates may not be in a standard distribution like Ubuntu and then need manual updates to a newer kernel or special drivers.

---

