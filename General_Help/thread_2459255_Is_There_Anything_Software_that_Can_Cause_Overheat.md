---
title: "Is There Anything Software that Can Cause Overheating?"
date: 2021-03-14
forum: General Help
---

### Post by rebeltaz on 2021-03-14
I had an old laptop that I had running Ubuntu 18.04LTS. It got where doing pretty much anything, it would go from 50-60 degrees up to about 80c. Things like running a zip compression where worst. It started doing this more and more gradually. On a couple of occasions I had cleaned everything and redid the thermal paste and that seemed to fix it for a bit. Then it got to where that did nothing, so I just figured that the whole computer was just getting too old. I bought a new-to-me E7450 with an intel i7 and put the old hard drive in here. This system is still doing the same thing only this one is going up to over 90c. 

Is there anything that I can check for software related that could cause this? Since the same drive in two different systems acts the same, I figure it must be software?

---

### Post by QIII on 2021-03-14
Could you run 

```
top
```

and post the top ten or so results?

---

### Post by rebeltaz on 2021-03-14
> **QIII said:**
> Could you run 

```
top
```

and post the top ten or so results?

It changes pretty quickly, but this is what I got:

```

derek@laptop:~$ top

top - 17:31:24 up 1 day,  4:55,  2 users,  load average: 1.46, 1.64, 1.46
Tasks: 281 total,   1 running, 226 sleeping,   0 stopped,   0 zombie
%Cpu(s): 15.3 us,  5.2 sy,  0.0 ni, 79.0 id,  0.0 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem :  8037816 total,  1085732 free,  4526104 used,  2425980 buff/cache
KiB Swap:  2097148 total,  1914108 free,   183040 used.  2510724 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
13180 derek     20   0 2902472 270700  69180 S  22.2  3.4 163:51.25 Web Content 
 1076 derek     20   0 3448052 641096  44844 S   7.3  8.0  11:50.97 4kvideodow+ 
  950 derek     20   0 1129652 152152 132532 S   5.3  1.9  53:32.86 Xorg        
 6490 derek     20   0 3288436 261576  87548 S   4.3  3.3  50:02.76 firefox     
30186 derek     20   0  812720  40996  30092 S   3.0  0.5   0:00.55 gnome-term+ 
  515 root     -51   0       0      0      0 S   2.3  0.0   8:07.05 irq/49-iwl+ 
12539 derek     20   0 36.922g 368716 300572 S   2.3  4.6   9:56.76 brave       
 1845 derek     20   0 7424700 213844  86512 S   2.0  2.7  25:59.12 skypeforli+ 
 1808 derek     20   0 1221660  62984  34704 S   1.7  0.8  21:05.19 skypeforli+ 
12102 derek     20   0 1588992 435664 130232 S   1.7  5.4  11:40.51 brave       
12134 derek     20   0  661832 122564  79116 S   1.7  1.5   6:12.38 brave       
25444 derek     20   0 3135000 370512 107872 S   1.7  4.6   0:44.94 cura        
 1232 derek      9 -11 2899328  16864  14412 S   1.0  0.2  27:46.61 pulseaudio  
27050 root      20   0       0      0      0 I   1.0  0.0   0:01.53 kworker/1:1 
 1449 derek     20   0  821204  34216  24572 S   0.7  0.4   8:39.41 metacity    
 1666 derek     20   0 3968916  73348  22100 S   0.7  0.9   2:09.78 java        
 6102 derek     20   0 3002284 631444  29216 S   0.7  7.9   4:53.23 transmissi+
```

---

### Post by TheFu on 2021-03-14
4kvideodow, java, Skype, Firefox and Brave?  Those seem to be heavy processes.  

Would be helpful if the output were wrapped in code-tags so the columns lined up and were readable.  
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.

---

### Post by HermanAB on 2021-03-15
Video and advertisements in your web browser...  Install a better advert blocker?

---

### Post by TheFu on 2021-03-15
79.0 id says the system is about 80% idle.  You'll want to watch that over time and look at cooling issues. 

Install the **sensors** package and **psensor** to watch different temperatures.  Not all CPUs and motherboards are well supported, so you'll probably need to tweak what can be watched. How is different for each motherboard.  I can only get 2 temperatures on my newest system.
CPU & GPU. Each core doesn't have a separate temperature output.  I only get the GPU fan speed, none of the case or CPU fans are picked up.

A hard working CPU should get hotter, but it should never go over the specifications from the CPU vendor. Look those up.  It should also quickly recover once the work is done if the cooling system is working.  I'm using the included CPU cooler/fan, GPU fan and the PSU fan for my newest system. It has been fine, but that's because it has an SSD and 1 HDD. The GPU is low-end, no extra power connectors.

On another system, it has 3 addon PCIe cards (SATA and eSATA and a NIC) with 4 internal HDDs. That system has cooling pulled in across all the HDDs, a case fan, CPU cooler, and the PSU fan. It doesn't have a separate GPU.

Check the cooling.

And I'd stop watching 4k video, unless you actually have a 4k capable monitor.

---

### Post by GhX6GZMB on 2021-03-15
Did you check the fan? You say you've cleaned it, but there may be things like bearing wear that slows it down.

---

### Post by Autodave on 2021-03-15
Try using *uBlock *in your browser.

---

### Post by rebeltaz on 2021-03-15
> **Autodave said:**
> Try using *uBlock *in your browser.

> **HermanAB said:**
> Video and advertisements in your web browser...  Install a better advert blocker?

Well, Firefox is only running as a monitor for a 3d printer running Octoprint, so no ads there. Brave is supposed to be pretty good blocking ads and such, but as an added bonus, I have uBlock Origin installed as well. I don't think I've seen an ad in a decade :)

> **ml9104 said:**
> Did you check the fan? You say you've cleaned it, but there may be things like bearing wear that slows it down.

On the old laptop, I don't think I did, but You could hear the fan spin up when it got hot. Same with this one. You can hear the fan spin up so I can only assume that it's running properly. As it does cool back down quickly once the program(s) is through running. It just bothers me that it gets that hot in the first place. 

> **TheFu said:**
> 79.0 id says the system is about 80% idle.  You'll want to watch that over time and look at cooling issues. 

Install the **sensors** package and **psensor** to watch different temperatures.  Not all CPUs and motherboards are well supported, so you'll probably need to tweak what can be watched. How is different for each motherboard.  I can only get 2 temperatures on my newest system.
CPU & GPU. Each core doesn't have a separate temperature output.  I only get the GPU fan speed, none of the case or CPU fans are picked up.

I  do have those installed. That's why I know that the temp is getting so hot :) When I go to preferences, though, it shows a collapsed menu for libsensors and i8k sensors. I don't know what's what and which is which. The one I have enabled is CPU under the libsensors menu, but there are so many others:

libsensors - temp1; temp1 [no, that's not a typo]; temp2; temp3; Package id 0;Core 0; Core 1; Processor Fan; CPU; Ambient; SODIMM; and Other

i8k - temp1 (CPU); fan1; and fan2


> **TheFu said:**
> And I'd stop watching 4k video, unless you actually have a 4k capable monitor.

Oh, no... 4kvideo is a video downloader. It downloads videos from streaming sites so you can watch them offline. It has nothing to do with real 4k video.

> **TheFu said:**
> 
Would be helpful if the output were wrapped in code-tags so the columns lined up and were readable.  
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.

Sorry. Yeah, I usually do use the code tag, but I didn't think about it here.

---

