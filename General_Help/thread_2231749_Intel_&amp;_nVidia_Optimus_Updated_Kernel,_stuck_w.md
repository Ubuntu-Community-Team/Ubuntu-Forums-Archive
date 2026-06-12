---
title: "Intel &amp; nVidia Optimus: Updated Kernel, stuck with 640x480 resolution"
date: 2014-06-27
forum: General Help
---

### Post by Beta_Grumm on 2014-06-27
Good afternoon.

I had an interesting journey yesterday as I attempted to update my kernel on my laptop install of Ubuntu 14.04. Long story short, I managed it and everything was working just fine. All work programs, my triple monitor setup, everything.
I was surprised.

Later that evening I booted my laptop from home without my dock or triple monitors, (just using the laptop display) and my resolution is stuck at 640x480. 

I've tried updating, and reverting back drivers. Updated my intel drivers (My laptop uses nvidia optimus, so it's an ugly intel and nvidia conbination) but so far nothing has had any affect. 

Most google searches result in topics concerning VMs and the solutions are not applicable.

My hope is that this is something simple-ish that I can fix without reverting back to an old kernel.

Info:
Lenovo Thinkpad T430s
Ubuntu 14.04
Kernel 3.15.2
Intel & nVidia Optimus display (NVS 5200M)

Any advice?
Thanks.

---

### Post by Beta_Grumm on 2014-06-27
Ok. Now that I've posted, I think I may have found my own answer. 

I found this little gem of a post: [http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode](http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode)

tl:dr I had the bumblebee project installed from 13.10 and after my experimentation of nvidia drivers from yesterday, apparently bumblebee was trying to load bad drivers. 
An uninstall of bumblebee seems to have solved my issue.

---

