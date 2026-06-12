---
title: "8 minute download and install"
date: 2018-02-22
forum: General Help
---

### Post by Gnusboy on 2018-02-22
Hey all

A strange thing happened today. There was an auto update notification and I clicked to install it. It was a very big d/l with imports for multiple packages, updating all parts of Libre Office 5. It took 8 minutes to download and install. I've never seen an update like it. It seems to work OK, but I'm curious about why it was so slow.
Also
I need to find a Ubuntu specific hardware app. My system hangs nearly every day under one or another programs. It hangs a lot under Firefox, but not so much using Chromium browser.
I might have as many as 7 or 8 windows open at a time, or just 2 or 3. 
When it hangs, it's sometimes just a few seconds. Other times it can be a minute or more, but that's less frequent. I first guessed it as a high memory use, but the system monitor does not show it.
I want to rule out any hardware problem, before I spend hours trying to locate software flaws.  
I did run a memtest a couple of days ago and it showed up "normal." However, I only ran one pass. Do I need to run multiple passes?

I have 4 GB ram installed on an older AMD Phenom quad core system.
The Sys monitor shows 3.6 GB ( I think the other .4 GB is system overhead?) But now I'm showing another .4 GB memory draw from the 3.6 Ram, leaving just 3.2 GB ram available.
I'd like to know if this situation is normal, or if it's causing the the hangs.
I appreciate any help figuring this out.
Thanks.

---

### Post by TheFu on 2018-02-22
4G of RAM is a pretty limited system today, especially if you use a "Modern browser" which are all RAM hogs.
When the system swaps RAM into swap (HDD virtual memory), it gets slow.  That is a hint that RAM is over committed. If both RAM and virtual memory run out, the system will likely crash.

System RAM is often used by the GPU/iGPU on lower cost systems or those that Intel CPUs that provide integrated GPUs.

Please check the system logs for issues.  You can google for "ubuntu log files" for a guide.

memtest is usually best run for 6-12 hours. 1 pass is not sufficient. As memory heats and cools, it behaves differently.

I've never used any of the GUI monitoring tools. There are lots that work well in a terminal plus you can copy/paste that output here for more help.

top, free -h, netstat, iostat, vmstat are the commonly used tools. Each has a manpage which explains the use and switches to get the outputs you want/need.

---

### Post by vasa1 on 2018-02-22
The LibreOffice package is large. Plus there was a kernel update. Yesterday was a busy day.

---

### Post by Gnusboy on 2018-02-22
Thank you. I didn't know there was big update.

---

### Post by missmoondog on 2018-02-23
while 4 gigs of ram is low by today's standards, i have 2 laptops here (32bit) with only 2 gigs and 2 other laptops (64bit) with only 4 gigs that run any and all browsers very well. i use lubuntu which is meant more for older machines but also have it installed on a couple other, newer machines with a little more memory. i do limit the number of tabs/windows i have open but that's only because it makes absolutely no sense to me to have mega numbers of them open. personally, i can only see 1 at a time, so why have multiple open?

as far as yesterdays updates, feel fortunate that your machine only took 8 minutes. the machine i was on yesterday took 40 minutes! that happens every once in a while and i have a couple topics here even asking why just checking the repositories takes so long. usually doesn't last for to long.

---

### Post by TheFu on 2018-02-23
I agree with MissMoonDog 100% and didn't mean to suggest that lower end machines aren't extremely useful. For a 2G RAM system, I'd limit browser tabs to 10 and for a 4G system, probably 15 tabs.  YMMV.  I've had 30 tabs open on my 4G systems.

There are techniques to address some of the limitations for having less-ram-than-browsers-want.

My laptop is a chromebook with 4G of RAM.  It used to lock up due to running out of RAM. I increased the swap to be 4.1G and made the swap compressed (which I think is the default on newer releases, but wasn't on 16.04).  I don't recall the exact steps, sorry.
```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-2                               partition       4300796 15456   -1
```  
dm-2 is the compressed LV from ... ```
$ lvs 
  LV     VG             Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  swap_1 ubuntu-vg -wi-ao----  4.10g  
```
Current RAM and swap use ... 12 tabs open and 2 browsers, thunderbird and about 10 xterms with ssh into other systems.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.7G        2.6G        441M        222M        745M        694M
Swap:          4.1G        322M        3.8G
```

That system is encrypted using dm-crypt/LUKS too, so swap is inside an encrypted partition. That's some of the weirdness.

I remove most addons and plugins from Firefox (no flash, no cisco h.264 stuff). This reduces the memory needed for each tab.  Firefox is my at-home browser. Adblocker, javascript disabled by default, except known sites, ghostery, and 3 others are left. Of those tabs, all but 1 allow javascript.  Trusted places.

Chromium is used in a **firejail --private** mode when not at home, so that anything written is wiped at close. That's the theory and it *seems to work*, since chromium acts like a new browser with all those pesky issues of the first-run. Just a little sandbox for the browser doing less safe things, like airline ticket stuff.

My main desktop only has 4G of RAM w/ a tiny bit stole for video memory.
```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:           3.9G        1.9G        530M        141M        1.5G        1.5G
Swap:          3.1G        2.0M        3.1G

```  Might need to add some swap. ;)  I think 4.1G of swap is the perfect amount for a desktop, regardless of the RAM amount.  On low-RAM systems, the extra swap is useful for a few reasons.  On systems with more RAM, having more swap really shouldn't be necessary.  The old 2x RAM rule of thumb for swap is dead.

As for updates, I only do patching on the weekends, never during the week.  This way I have more time and can better tell if an update broke something.  With daily patching, I can't tell what might have broke. Too hard.

Other people will have different techniques that might better fit your needs.  Hope you can find something useful.

---

### Post by tinylagarto on 2018-02-24
I have also 4 GB of RAM and I am relatively happy with it. Before I had only 2 GB, so for me it was an upgrade. 
I still consider 4 GB of RAM or even 2 to be sufficient in most cases. I mostly use older hardware but it is true that by today's standards it seems to be low. That is why I use lightweight desktops or flavors of Ubuntu like Mate or Xfce.

Maybe try one of the lighter *buntus. 

To monitor RAM usage I prefer to use *htop*, *free* and *top* from the command line. That is not to say that there are no GUI apps like* task-manager* in Xfce or *Gnome System Monitor*.

---

### Post by kostkon on 2018-02-24
> **Gnusboy said:**
> The Sys monitor shows 3.6 GB ( I think the other .4 GB is system overhead?) But now I'm showing another .4 GB memory draw from the 3.6 Ram, leaving just 3.2 GB ram available.
I'd like to know if this situation is normal, or if it's causing the the hangs.
I appreciate any help figuring this out.
Thanks.
Maybe some of that "missing" RAM (probably the first 400Mb) is shared with your graphics card, especially if you happen to have a system with on-board graphics.

---

