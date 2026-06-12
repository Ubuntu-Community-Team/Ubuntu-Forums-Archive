---
title: "How to diagnose the cause for hickups and lags?"
date: 2020-06-13
forum: General Help
---

### Post by onlineguy on 2020-06-13
Hi,

I experience random frequent "hickups" or temporary freezes when using my Ubuntu 20.04 desktop setup (multiboot with Windows 10). These hiccups make the system unresponsive. Some buttons do not react anymore but the mouse pointer can be moved normally. When I hit the Firefox logo the window appears in the bar but the browser does not start. After up to 10 seconds the system is back again. I cannot tell if the sysstems really hands as a whole. Using the terminal the actual process take very long. Today I ran an update after ~one week of absence, it took me nearly 15 minutes. Given my PC's hardware this should be much quicker. Please be aware that I installed Ubuntu on a 32 GB USB3 flashdrive. I know that this is not optimal performance-wise but I did this in the past as well and never experienced anything like this.

My hardware: Intel i7-8700, 64 GB RAM, Gigabyte Aorus MasterZ3990 motherboard, Gigabyte Aorus RTX 2080.

So, how doI diagnose the cause for these kind of hickups?

---

### Post by CelticWarrior on 2020-06-13
Did you install the Nvidia drivers?

---

### Post by onlineguy on 2020-06-13
Yes, but this does not feel like a graphics problem. There are no graphical glitches, ur just hangs.

---

### Post by GhX6GZMB on 2020-06-13
Is Firefox always open/running? This might be your issue, FF has a dysfunctional memory management (both on Ubuntu and Win).

---

### Post by onlineguy on 2020-06-13
No, it happens when I just use the terminal as well.

---

### Post by CelticWarrior on 2020-06-13
It's really hard to troubleshoot this kind of issues. Your original statement > Some buttons do not react anymore but the mouse pointer can be moved  normally. When I hit the Firefox logo the window appears in the bar but  the browser does not start. After up to 10 seconds the system is back  again. I cannot tell if the sysstems really hands as a whole. Using the  terminal the actual process take very long actually suggests graphical issues, hence my question. It's very similar to what happens with the open-source driver *nouveau* and high-end Nvidia graphics. But you confirm you're using the Nvidia proprietary drivers instead and since you're running the latest release then probably the recommended drivers are the best ones for such new card. So, likely not the problem.

Software misbehaving like Firefox as suggested above would then be a possibility. Web browsers, not only Firefox, may end up gobbling huge chunks of memory, it all depends on the usage, the amount of pages simultaneously open and the resources each one asks for, of course. But that is also unlikely because of the 64GB RAM. It should be enough for anything you may want to trow at it. And you said that it happens as well with only the terminal running. So, very unlikely it being related to Firefox or any other software.

Considering all the above there are very few hypotheses left. One that I think is quite plausible is the USB drive it is installed on. A flashdrive, even with USB3.0 is far from ideal but many work for the purpose. However, some really don't, either because the actual chips inside are somewhat slow (yes, the USB3.0 connection may not mean what you think it means) or the data transfer varies wildly for some other reason. Not all USB sticks are good for such usage even if the performance as removable/portable mass storage devices seems acceptable. Or the USB connection/hub itself is flaky.

---

### Post by onlineguy on 2020-06-18
But surely there must be logs to look for to see error messages or warnings related to the flashdrive or any other hardware or software component? 

By the way, I benchmarked my flashdrive before installing Ubuntu, it is a "real" USB3 drive (which does not rule out a hardware problem) which I used a year ago for a well working similiar setup.

---

### Post by dragonfly41 on 2020-06-18
I have Ubuntu 18.04 running very nicely on an external SSD via USB 3.0. Windows 10 still in primary drive.

You asked "[COLOR=#000000]how do I diagnose the cause" .. so I offer some steps I would take to pin this down.

First you might find this tool to be handy to monitor resources.
[Stacer]("https://github.com/oguzhaninan/Stacer").

If you click on Resources you can monitor history usage.

[Webmin]("http://www.webmin.com/") is another useful tool which at dashboard shows history going back 30 minutes or so.

You can try basic tests such as changing your port and/or USB cable to eliminate these as causes.

You can try running on USB 2.0 port instead of USB 3.0.

You can try launching a different user account/session.

You can try Lynis auditing tool in Ubuntu repo.

It is a lot of guesswork.


[/COLOR]

---

### Post by ActionParsnip on 2020-06-18
Webmin is awful. gnome-system-log will allow you to read the logs in a sleeker way

---

### Post by dragonfly41 on 2020-06-18
> [COLOR=#000000]Webmin is awful[/COLOR]

I know that it is disliked by many users who prefer cli and there are security holes if you don't use it wisely.
But I can easily development custom commands to reflect my workflow.  Replaces the old cli-companion.

The launch page shows stats.

---

