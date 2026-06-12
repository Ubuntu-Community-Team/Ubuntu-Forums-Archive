---
title: "Huge memory Usage and crawling machine"
date: 2007-03-14
forum: General Help
---

### Post by phrizer on 2007-03-14
Hi all,

I do hope this is not received as just another "Why is my system using all my ram!?!" type question.
I'm fully aware that "unused ram is wasted ram" and that the Linux kernel will keep data floating around in memory as a cache for future use if needed.

However, here's my (short) story. I recently replaced my old system it was a 800mhz Athlon with 256mb of memory running Dapper LTS. This System worked pretty good at a reasonably speed and responsiveness. 

My new system is a Intel P4 2ghz with 256mb of memory running a fresh (4 days old) install of Edgy-Eft. Same amount of memory, but otherwise a much faster system.

The problem is my new system is running EXTREMELY slow with very very poor responsiveness. For an example, switching from one application to another application can take anywhere from 5 seconds to 30 seconds. Closing an application can take the same times, and in fact often just ends up locking up the application and asking me to force close it. Moving the mouse around the screen or dropping down the applications menu also takes a ridicules amount of time. Clicking 'show desktop' will VERY SLOWLY draw the desktop over a time span of about 10 seconds. launching an application again - takes an extremely long time. All the while my hard drive is chugging and grunting along very noisily. 

In other words, the responsiveness of this new "faster" computer is almost at the unusable level. Very disappointing. 

Here's some information I've obtained from my system:

~$ free
             total       used       free     shared    buffers     cached
Mem:        247852     243464       4388          0        396      25144
-/+ buffers/cache:     217924      29928
Swap:       722884     466520     256364


Thats right, all my physical memory is used up, and i often approach 500mb of swap.

Here's the output of 'top' sorted by memory % (the top 4 entries)" 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                         
 4655 lance     15   0  245m  97m  14m S  2.7 40.3  20:25.55 firefox-bin                                     
28228 lance     15   0  106m  24m 5436 S  0.3 10.3   4:59.57 gnome-panel                                     
28230 lance     15   0  117m  24m 5692 S  0.0 10.0   2:59.94 nautilus                                        
28136 root      15   0  273m  18m 3760 S  2.3  7.6  47:13.26 Xorg           

To me i can only think that the the cause of all this slowness and hard drive activity and very poor responsiveness is a side-effect of my system thrashing. Why is my system needing to use so much memory, and swap so much data? Thats insane! I never experienced anything like that on my 800mhz/256mb machine with dapper drake.

As a side note, my CPU usage sits typically around the 3 - 10% level. Better than my 800mhz machine in that regard.

Any advice to help make my new computer usable would be greatly appreciated.

Thanks.

---

### Post by peabody on 2007-03-14
Hmmm, methinks this may be related to drive performance.  Sometimes DMA doesn't work out on drives in Linux and the read/write speed drops into the single digits.  You're gonna swap a lot at only 256 megs of RAM and if your disk access times suck, speed in general will suck.  hdparm might come in handy here, it's been a while since I've used it.  You might try:

sudo hdparm -t /dev/hda

Replace /dev/hda with whatever your drive is.  See what the results are.

---

### Post by russell.h on 2007-03-14
You might also try a different web browser, or see if you can find a way to keep down firefox's memory usage. It looks like its using about 100mb of physical RAM and 250 of swap, which is almost half of the RAM being used total.

One thing you can try is restarting firefox every so often. Uh... thats strange, system monitor doesn't seem to be installed..... (I just had some updating troubles in Feisty), but if memory serves correctly firefox usually uses 70-80mb of physical memory on my machine, and I have 1GB to burn...

---

### Post by phrizer on 2007-03-14
> **peabody said:**
> Hmmm, methinks this may be related to drive performance.  Sometimes DMA doesn't work out on drives in Linux and the read/write speed drops into the single digits.  You're gonna swap a lot at only 256 megs of RAM and if your disk access times suck, speed in general will suck.  hdparm might come in handy here, it's been a while since I've used it.  You might try:

sudo hdparm -t /dev/hda

Replace /dev/hda with whatever your drive is.  See what the results are.

I've tested my hdd read speed, it's typically > 40MB/s which is in fact slightly faster than my older machine.
My older machine use to have only 256mb of memory and it never swapped this much.

---

### Post by phrizer on 2007-03-14
> **russell.h said:**
> You might also try a different web browser, or see if you can find a way to keep down firefox's memory usage. It looks like its using about 100mb of physical RAM and 250 of swap, which is almost half of the RAM being used total.

One thing you can try is restarting firefox every so often. Uh... thats strange, system monitor doesn't seem to be installed..... (I just had some updating troubles in Feisty), but if memory serves correctly firefox usually uses 70-80mb of physical memory on my machine, and I have 1GB to burn...

The strange thing is though I never had this problem with Dapper Drake on my older machine with the same amount of memory. Is there THAT much difference between Dapper and Edgy? Is there that much difference between Firefox 1.5 and 2.0?

On a side note doesn't the "VIRT" output of 'top' simply mean all the memory the process has access too including code, data AND shared memory (shared libraries) including pages swapped out, and not simply all the memory the process requires for itself exclusively?

I guess whats troubling me here is, is there that much of a difference between dapper and edgy such that it would cause a much 'faster' machine running edgy to run ALOT slower than a 'slower' machine running dapper? 

i.e should a (2ghz + Edgy) run slower than a (800mhz + Dapper)
Where both systems have the same amount of memory.

Or is there something funny going on with my system?

---

### Post by russell.h on 2007-03-14
I think there's something wrong with Firefox. I had heard of memory leaks in 2.0, and here is my top output for firefox (actually firefox32, I'm running 64 bit Feisty):

32134 russell   15   0  126m  43m  15m S    1  4.3   1:01.80 firefox-bin

---

### Post by tribaal on 2007-03-14
Does the system go back to normal if you close firefox? From your top output it would seem that Firefox is using up half of your system's memory...

Did you install lots of firefox extensions? Theses can get pretty buggy sometimes...

Hope we'll solve the problem fast :(

- trib'

---

### Post by phrizer on 2007-03-14
> **tribaal said:**
> Does the system go back to normal if you close firefox? From your top output it would seem that Firefox is using up half of your system's memory...

Did you install lots of firefox extensions? Theses can get pretty buggy sometimes...

Hope we'll solve the problem fast :(

- trib'

Closing Firefox "relieved" the symptoms slightly. And i mean SLIGHTLY.  But it did not even get anywhere near back to speeds and responsiveness that i was getting with my older 800mhz system, let alone surpass them as i was hoping when i first got this newer computer. Even with Firefox closed, right click menu's take a good 5 or 10 seconds to appear, and all the usual troubles i have, just *slightly* not as bad.

And no i have not installed any Firefox extensions.

---

### Post by davidbarton on 2007-04-01
Since upgrading to Feisty, my FF memory usage has rocketed up to 1.2 - 1.4 GB!!!!  This is after a day of browsing, whereas I used to run for weeks.

Is the FF for Feisty compiled with debug info or something??  It slows down my entire machine and the only way to get respite is restart FF.  Scrolling, tab switching, clicking links pretty much everything has this 1 - 5 second lag.

I am turning off extensions to see if that does something.  I am suspicious of Firebug, I'll post back the results.

On the plus side, OO.org 2.2 runs great.  The version that came with Edgy was so unstable I resorted to running an X session to a dapper machine.

David

---

### Post by davidbarton on 2007-04-02
It seems Firebug was the culprit.  I disabled it and memory usage is down to a "lean and mean" 390MB after a day of browsing.  

I wish it didn't use so much RAM, but I'm now back with the blame squarely at Fire Fox, and not Feisty.

BTW, Feisty rocks even more, my wireless card "just worked" after a recent apt-get upgrade yaay!

---

### Post by PatrickMay16 on 2007-04-14
I have a similar problem. 

I used to use an old laptop with 256MB RAM, and ubuntu Dapper installed. When I first installed it, it used about 113 MB of RAM after logging into gnome. After tweaking things and so on, I got it to 67MB RAM after booting and logging into gnome.

Now I have a new laptop with 1GB of RAM, and have edgy installed on it. When I first booted into it, it was using about 200MB just sitting there after logging into gnome! I tweaked it in much the same ways as before, and now I've got it to 136MB of usage after booting and logging in to gnome.

It's crazy. If anyone has any idea on how to get the memory usage down, please let me know.

---

