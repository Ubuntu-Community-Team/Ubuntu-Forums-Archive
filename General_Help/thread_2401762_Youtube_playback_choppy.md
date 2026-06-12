---
title: "Youtube playback choppy"
date: 2018-09-22
forum: General Help
---

### Post by jackandcrack on 2018-09-22
Hi, so I have noticed that my in browser video playback is pretty poor.  Its choppy and seem to have trouble maintaining a consistent framerate.  This seems to be consistent across sites, although seeing the dominance  of HTML5 I'm not sure if its just a problem with that particular player  or all video players. This is on a fresh install of Ubunto 18.04 (with  the "extras -media codecs etc." installed). 

I'm currently trying to switch over to using mainly Ubuntu on my daily  laptop, which i use mainly for casual web browsing, youtube videos, and  netflix. The videos typically aren't what i would call unwatchable but  it is bad enough to be fairly annoying, and given that video browsing is  mainly what i use this laptop for if i can't figure this out i may have  to go back to OSX :'(

I'm currently running it on a virtual machine on my Macbook air with a  1.8-2.6 GHz Intel i5 (2 core, 4 thread) with 4 gigs of DDR3.
The VM is allocated 2.5 gigs of ram and 1 CPU core (2 threads) to work with. 

I realize this isn't the ideal setup for milking premium performance,  however i have noticed the same problem on the VM im running on my  desktop which is allocated 6 gigs of ram and 3 cores (6 threads) of CPU  power so i don't think that horse power is the only issue at play here.  -note the desktop does experience the issue to a slightly lesser extent.

Any thought/fixes/ideas are much appreciated.

Could this just be a result of running on a VM? Just something inherent to Ubuntu/Linux? 

Thanks in advance!

---

### Post by ajgreeny on 2018-09-22
> **jackandcrack said:**
> Could this just be a result of running on a VM? Just something inherent to Ubuntu/Linux? 

Thanks in advance!
This is most likely related to the OS being a VM.

Using what; VirtualBox, Vmplayer, or something else?

---

### Post by jackandcrack on 2018-09-22
yes virtualbox. I did up the power on my desktop VM to to 8 gigs of ram and 4 cores 8 threads and still had the issue so horsepower within the VM i think is pretty definitively not the problem, it vary well may be just inherent to it being a VM at all. I'll try installing a dual boot on the laptop and see if that fixes it.

---

### Post by ajgreeny on 2018-09-23
No matter how good the hardware is on which you run a virtual machine in VBox, the best graphics you can get is still pretty poor, so I suspect this is your main problem.

As you say, a full dual boot may be a great deal better.

---

