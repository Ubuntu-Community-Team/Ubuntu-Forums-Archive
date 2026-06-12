---
title: "Notebook wake-up issue"
date: 2015-08-31
forum: General Help
---

### Post by yevghenn on 2015-08-31
Sorry for my bad english.

Everything work like a charm, but when i close my lid, and then open it and wake up from suspend, my CPU load is 100%. If i open firefox, then firefox load is 100%. If i close it and open gimp, it will be 100% load for gimp. Same for any application i open. In result my notebook work like slow turtle and notebook FAN work really loud. And this problem will go away only after reboot. After reboot everything is ok, but when i close my lid again... this thing happen.

This thing happen on all ubuntu-like distros. Linux mint, Ubuntu, Xubuntu, Ubuntu MATE. When i install clean OS - everything is ok, but when i install all updates this thing happens.

Notebook is Dell Latitude E5420(late 2011)
Processor i5-2520M
RAM: 16GB

I am not big specialist in Linux, dont know where is problem.

Ow, and some more info about OS.

Right now i have Ubuntu MATE 14.04, kernel 3.16.0-46 generic

---

### Post by cubenerd on 2015-08-31
Once you boot into your laptop after opening it, check your systems monitor.
Do you see anything unusual using a high percentage of your CPU?

---

### Post by yevghenn on 2015-08-31
When i open lid and enter from suspend-mode:

If i have running Firefox and System Monitor it will show 50% CPU for Firefox and 50% for System Monitor. No matter what application i have running, it will eat everything. If i have multiple apps running, they will share CPU usage. But it will be always 100% in sum.

If i close everything - it will be ok. But when i start browser, or gimp or any other app, it will overload my CPU. Only reboot fix it :/

I dont have swap-partition. Maybe this is problem? But i heard swap is old technology, only for low-RAM machines. Am i wrong?

Uhm?

---

