---
title: "Reducing Load Average on my Kubuntu 12.04 desktop"
date: 2013-08-11
forum: General Help
---

### Post by silconsystem on 2013-08-11
Hi All,

I've got a question about lowering CPU loads, if I understand correctly when I issue the 'uptime' command I get 3 values representing 5, 10 and 15 minutes of average CPU load.
My current stats are around:
load average: 0.57, 0.72, 1.42
offcourse they fluctuate but the 15min value is always between 1.40-1.80, from what I understand everything above 1.00 is NOT okay.
My specs are:

Intel(R) Celeron(R) D CPU 3.20GHz single core processor

1GB Ram, 1GB swap, 512MB zram:
Filename                                Type            Size    Used    Priority
/dev/sdb7                               partition       3004116 129688  -1
/dev/zram0                              partition       480316  2212    100

Kubuntu 12.04 is on a 80GB drive with about 35GB used, this is the OS and programs, all files I work with or download are located on another drive.

When I issue 'top' I can see no big activity from the systems deamons and background processes. Its mostly the browsers, gimp and stuff like eclipse and codeblocks that take up a lot of memory.
But I mostly dont run more than 2 programs together anyway.
Also I've disabled window animations and effects.

The system also responds, reads and write at a good speed.

So how can I have such a high average?
And are there any more tools to get more info and control over CPU processes?





Greets,Rob

---

### Post by zitch on 2013-08-11
I could be wrong, but there is no such thing as a "NOT okay" load value. The load is just a number that's calculated using your CPU usage, IO wait times, swap usage, and other things in a mesh that spits out a number, but if your system seems to be working fine for you (which is itself subjective), I'd not worry too much about load.

As a comparison, I'm running on a Core Two Duo 2.56 HGz dual core processor, with 8 gigs of ram, 10 gigs of swap, running Kubuntu 13.04 and my load number look like:
0.65, 0.62, 0.89

I have numerous chromium windows and tabs open, eclipse running, but am just browsing for the past hour or so.

---

### Post by silconsystem on 2013-08-11
Thanks for your reply,

I'm always trying to find info on how to maintain and improve my system so thats how I got into this subject. From what I understood if your system goes over the 1.00 mark its actually like your processors average is over 100%.
You have 2 processors so you even have to divide the average by 2 resulting in around 0.40 wich is good.

I guess your right, for the specs of my computer and the performance it gives I cant complain but if I can take some steps to ensure that it keeps running like this I think its worth the effort.
Still its hard to find a simple awnser to reducing CPU load, I think its the sum of many different factors.

Whem I check the 'top' processes the system processes hardly go over 10%, its just the Browser, Gimp, Eclipse and such that use large percentages at startup. Is there maybe a way to restrict their CPU usage so they would be slower but less consuming?


Greets,


Rob

---

### Post by zitch on 2013-08-11
The easiest way I could see of reducing the load (without changing what programs you run or going to a lighter desktop environment) would be to upgrade your CPU and increase your RAM. Other than that, I can't see how you would be able to reduce load in software; most tweaks are done not for the direct purpose for reducing your load, but for increasing performance or for increasing the "responsiveness" of the desktop. Here're a few tweaks I have done on my work laptop for example:

1) Installed the low latency kernel, which seems to help with desktop and gaming responsiveness while under high load - [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real_time_.28-rt.29_and_Low_latency_.28-lowlatency.29_kernels](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real_time_.28-rt.29_and_Low_latency_.28-lowlatency.29_kernels)
2) Experimented with the swappiness value to change how the system pushes to swap (current have it set to 10, but I've not seen definite proof that this is helping) - [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

I have no recommendations to do the above steps for you, and neither of the above were done in order to reduce my load, but to increase the responsiveness of the system when it's under load (I.E., gaming, or busy compiling). If anything, the above tweaks actually slightly reduces the overall performance of my machine in the name of UI responsiveness.

Your suggesting of restricting programs' CPU usage when running is not a route most people would take, so I doubt you'd find much research on that.

UPDATE: BTW, the rule of thumb seems to be your system is overloading if the value is higher than the number of cores (I.E., 1 for single core, 2 for dual core, etc.).  Maybe waiting until Mir and Wayland are in general use would help too (Xorg on my system seems to be the top processes using about 5%-15% of 2 CPUs (so... 2-8% total cpu usage) at all times on idle). Here's wiki's article describing load, but it doesn't give me many clues on tweaks to reduce it on a system: [http://en.wikipedia.org/wiki/Load_(computing)](http://en.wikipedia.org/wiki/Load_(computing))

---

### Post by SeijiSensei on 2013-08-11
Load averages above one are not, *per se*, a problem.  I've had machines that ran in the 3-4 range.  They're sluggish, but they still work.  I've even had machines break into the double digits with load averages of 12 and above.  Again, they keep working, just slowly.

---

### Post by silconsystem on 2013-08-12
Hi,

Thanks for your awnsers, I've also experimented with the swappiness and I ended at 10 aswell. The low-latency kernel might improve performance aswell. I've had Ubuntu Studio installed aswell and it responded quite good but for music production itself I guess I really need more ram. Now I got it on a laptop with 2GB RAM and an Intel core 2 duo and there it works without any Xruns out of the box.

Anyway its good to know that its nothing to worry too much about and it seems I took the right steps already to keep the system running as good as possible.

Thanks Guys !!

---

