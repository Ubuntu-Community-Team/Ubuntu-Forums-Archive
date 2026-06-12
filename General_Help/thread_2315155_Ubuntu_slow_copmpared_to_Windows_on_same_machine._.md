---
title: "Ubuntu slow copmpared to Windows on same machine. Need ideas for fix"
date: 2016-02-26
forum: General Help
---

### Post by sp40140 on 2016-02-26
I have HP EliteBook laptop with 2nd gen core i7, 6 gigs ram, 256 gigs ssd and 500 gigs platter hd with onboard nvidia graphics. I have this with dual boot ubuntu 15.10 and win7. Almost always I use ubuntu. However, there are some rare times I HAVE to boot windows.  And at those rare times I have found that browsers (chrome and ff) perform much much better on windows, renders pages remarkably quickly. I can see the difference with my eyes. Now, since its same hardware (yes, both win & ubuntu are on ssd), I can think of two things, 1] graphics drivers 2] the version of application implemented for win vs ubuntu.  I just want ideas on what can I do to boost performance of ubuntu? As I know the hardware is capable of much more.  Thanks, Bheju

---

### Post by mörgæs on 2016-02-27
Let's see more about the graphics then. Please run ```
sudo lshw -C video
``` and post the results in CODE tags.

---

### Post by sp40140 on 2016-03-09
```

  *-display               
       description: VGA compatible controller
       product: GT218M [NVS 3100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:33 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:d3080000-d30fffff



```

I was out of town for few days.

---

### Post by HermanAB on 2016-03-09
What you are saying is that the browser is faster on Windows.

There can be multiple reasons:
1. You may be using a better or different configuration of the same Adblocker.
2. You may be using different Name Servers.
3. Your Ubuntu video driver could be bad.

My money is on the first two.

---

### Post by sp40140 on 2016-03-09
What you are saying is that the browser is faster on Windows.
No. I am saying that the graphics performance is hugely different. Browser was just an example.
There can be multiple reasons:
1. You may be using a better or different configuration of the same Adblocker.
Nope. I use same extension and same configuration. It could be possible that that implementation on different platform is a factor.
2. You may be using different Name Servers.
Nope. Same Name Servers.
3. Your Ubuntu video driver could be bad.
Using Prop Nvidia drivers. But this could be it. Open to suggestions on how to improve it. (I have already disabled / enabled, tried opensource ones).

Thank you for feedback.

---

