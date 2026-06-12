---
title: "Ubuntu becomes slow after some time"
date: 2014-06-21
forum: General Help
---

### Post by alexander-l on 2014-06-21
I've encountered this problem a few days ago. After some time of normal work (usually 5-30 min), Ubuntu 14.04 becomes extremely slow. ATOP shows that CPU is fullly loaded, but not by one specific process, but by all of them. E.g. if the music is playing, then CPU is loaded by player itself and pulseaudio, if the browser is opened, then CPU is loaded by browser etc. It looks like the CPU frequency is set to minimum, but executing "sudo cpufreq-set -g performance" helps nothing. Reinstalling the system from s&#1089;ratch changes nothing as well.

My PC:
CPU : Intel® Core™ i3-2310M
Graphics:  Intel® Sandybridge Mobile 
Memory:  2GB RAM, 3GB swap

Some screenshots from ATOP:
[http://oi58.tinypic.com/14j9lq9.jpg](http://oi58.tinypic.com/14j9lq9.jpg)
[http://oi58.tinypic.com/2l9irnc.jpg](http://oi58.tinypic.com/2l9irnc.jpg)
[http://oi58.tinypic.com/339otqa.jpg](http://oi58.tinypic.com/339otqa.jpg)

---

### Post by uudruid74 on 2014-06-21
> **alexander-l said:**
> I've encountered this problem a few days ago. After some time of normal work (usually 5-30 min), Ubuntu 14.04 becomes extremely slow. ATOP shows that CPU is fullly loaded, but not by one specific process, but by all of them. E.g. if the music is playing, then CPU is loaded by player itself and pulseaudio, if the browser is opened, then CPU is loaded by browser etc. It looks like the CPU frequency is set to minimum, but executing "sudo cpufreq-set -g performance" helps nothing. Reinstalling the system from s&#1089;ratch changes nothing as well.

My PC:
CPU : Intel® Core™ i3-2310M
Graphics:  Intel® Sandybridge Mobile 
Memory:  2GB RAM, 3GB swap


I wonder if your problem is related to mine.  I get *ALL* X Apps at full CPU usage, more or less evenly distributed, including DBUS, IBUS, all the running panel apps, even stuff thats sleeping.  All of X dims to tell me that all applications are not responding ... and then it goes away in 15-20 seconds.  I'm still working on how to record a screenshot since I can't use X while it happens!

Similar?

---

### Post by robin7 on 2014-06-21
Too much "swappiness," perhaps?  I'm guessing, since I routinely reduce my "swappiness" with every new installation (but I have a very old, very low-powered computer).  From this web site: [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu) :

> 
[h=3][SIZE=3]**Decrease the swap use (very important!)**[/SIZE][/h] 1.5. This is especially noticeable on computers with relatively low RAM  memory (1 GB or less): they tend to be far too slow in Xubuntu, and  Xubuntu accesses the hard disk too much. Luckily, this can be helped.

On the hard disk there's a separate partition for virtual memory, called  the swap. When Xubuntu uses the swap too much, the computer slows down a  lot. 

Xubuntu's inclination to use the swap, is determined by a setting. The  lower the setting number, the longer it takes before Xubuntu starts  using the swap. On a scale of 0-100, the default setting is 60. Which is  much too high for normal desktop use, and only fit for servers.

a. First make sure that you have installed the applications [COLOR=#0000FF]gksu[/COLOR] and [COLOR=#0000FF]leafpad[/COLOR]:

Menu button - Accessories - Terminal Emulator

Type (use copy/paste): 
[COLOR=#0000FF]sudo apt-get install gksu leafpad[/COLOR]

Press Enter and submit your password. Please note that the password will  remain invisible, not even asterisks will show, which is normal.

b. Now check your current swappiness setting. Type in the terminal (use copy/paste):
[COLOR=#0000FF]cat /proc/sys/vm/swappiness[/COLOR]

Press Enter.

The result will probably be [COLOR=#0000FF]60[/COLOR].

c. To change the swappiness into a more sensible setting and improve the  cache management as well, type in the terminal (use copy/paste):
[COLOR=#0000FF]gksudo leafpad /etc/sysctl.conf[/COLOR]

Press Enter.

Scroll to the bottom of the text file and add your swappiness and cache  parameters to override the defaults. Copy/paste the following lines:

[COLOR=#0000FF]# Decrease swap usage to a reasonable level
vm.swappiness=10
# Improve cache management
vm.vfs_cache_pressure=50[/COLOR]

d. Close the text file and reboot your computer.

e. After the reboot, check the new swappiness setting:

Menu button - Accessories - Terminal Emulator

Type (use copy/paste):
[COLOR=#0000FF]cat /proc/sys/vm/swappiness[/COLOR]

Press Enter.

Now it should be [COLOR=#0000FF]10[/COLOR].

***Note:*** your machine might benefit from an even bigger decrease in swappiness. A useful rule of thumb might be this:
1 GB RAM or more: set swappiness to 10
Less than 1 GB RAM: set swappiness to 5


Note that this is for Xubuntu, which is what I use. There's a page written about optimizing Ubuntu for SSD drives [here]("https://sites.google.com/site/easylinuxtipsproject/ssd"), too, which might be useful.

---

### Post by buzzingrobot on 2014-06-21
I may be wrong, but I don't believe "swappiness" should impact CPU use. Swap is all about substituting physical disk space for RAM when there is insufficient RAM available (something, of course, more likely to occur on hardware with low RAM).

An exception, perhaps, might be possible if the swap algorithm is overwhelmed moving tiny packets to and from the swap partition due to swappiness settings. That's a guess, but it might be worth a look.

i don't agree with suggestions to avoid swapping on low-RAM hardware.

---

### Post by LastDino on 2014-06-21
Avoiding swapping on low ram machines basically beats the purpose of using swap in first place. With OP's 2GB RAM, I suspect this has anything to do with SWAP all together. 

Especially when SWAP uses is zero in screen shot OP is posting. 


@OP, Are numbers from atop tallying up with system monitor? Is the behaviour consistent on different OS?

---

### Post by alexander-l on 2014-06-21
The system monitor shows full CPU load, but it can't even update the processes tab, when this problem occurs.
As for now, Ubuntu is the only system on my PC, I'll try tomorrow installing something else.

UPD. It seems like the problem was with power. The cable to notebook has three threads, one of which was brocken, I've soldered it, seems like everything is OK.

---

