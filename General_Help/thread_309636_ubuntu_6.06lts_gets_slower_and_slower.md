---
title: "ubuntu 6.06lts gets slower and slower"
date: 2006-11-29
forum: General Help
---

### Post by spudley on 2006-11-29
I've been trying to put Ubuntu to work for some time now... various installs, etc... 

Lately, I'm trying 6.06LTS on a P4 2.8GHz machine with 512MB RAM and decent video..  Its a clean install too - no dual boot or anything like that.

On first boot, everything seems good - everything runs quick - I have gdesklets (disk, network and memory monitors as well as goodweather) and the Deskbar applet running.  All is fine - but once I get using Firefox, things get slower and slower over time -- if I have a few tabs open, by the time the next day rolls around, things are going at a snails pace compared to when I first boot up.

I do have a couple of mounts - one to a w2k server drive and the other to a Linux NAS box - other than that - its a pretty clean install.

top reports xorg, firefox-bin, python and beagled as the top users of resources - firefox-bin being the top after a day or two followed by python.  beagled jumps around and doesn't seem too relevant.

I have lots of disk space available (~30gb free).

Any thoughts as to what I could look for?  Would an upgrade help?  I'm trying so hard to ditch my Windows machines, but can't justify it when Ubuntu starts slowing down!  I had to switch to my XP machine to download a few PDF files because just scrolling through the web pages was honestly way too slow.

Thanks for any advice on this issue!

---

### Post by Hmarroqu on 2006-11-30
im totally noob, but maybe gdesklets hogs lots of ram, i know that it did when i used it and i did notice slowing down( note i have 1g ram). also check for some processes running in the background on your system monitor.
heres my processes with the ones using the most mem first, the other ones not shown are regualar gnome procesess
[http://docs.google.com/View?docid=ddz6b2xx_5dhmt4q](http://docs.google.com/View?docid=ddz6b2xx_5dhmt4q)

---

### Post by cronholio on 2006-11-30
If yor PC really slows down so much that you notice it when scrolling, there must be a process that uses vitually all the CPU. Can you tell us how much CPU% the top process in top uses and what it is?

If you think the mounts can be the problem, uncomment them one by one in fstab and see if it changes after a reboot.

---

### Post by Cronjob on 2006-11-30
Are you using the shadow/translucency features in the control panel for your desktop? I would love to use those myself, but they slow things down to the point that they are unusuable, after awhile. I'm not on a weak machine, either. Dual-core AMD64 3800+ with 2gb DDR and a 512mb GeForce 7900. So I just do without them. It might be worth disabling them just to be sure and see what happens.

Meanwhile, I'm just going to wait until 7.04 which is hopefully (according to launchpad) going to have compiz as part of the default deployment.

---

### Post by kvonb on 2006-11-30
It might be beagle, it scans the entire filesystem building/rebuilding its database (so I believe).  I've heard of people complain about it eating up vast areas of hard drive space too, to the tune of 6+gigs!

Try disabling it in Menu -> Stsyem -> Prefs -> Sessions, just highlight it and click on disable.  If you notice an improvement then uninstall it!

Regardfs, KEv

---

### Post by mcduck on 2006-11-30
both gdesklets and firefox are known as memory hogs, and with only 512MB of RAM it's quite likely that after couple of days they have eaten all your free memory..

I'd suggest closing FF every now and then, and you could also try living without gdesklets for a while. Get adesklets or conky or gkrellm instead.

---

### Post by zephyrus54 on 2006-12-05
I'm using 6.10 edgy eft.  I recently had problems with a very slow firefox (it didn't seem to slow down the rest of my computer though), and I tried installing swiftfox (optimized version of firefox for Linux).  Since then, everything has been running a lot smoother/quicker, especially the web browser.  You might want to give swiftfox a try.

---

### Post by spudley on 2006-12-05
I 'fixed' my speed issue - strangely enough, changing resolution from the default 1024x768 to 1280x1024 improved things _drastically_ - I also run gdesklets, adesklets and beagle too.

I found my default video driver was 'vesa', so I did change it to 'SiS' - but the real performance increase didn't happen until I bumped my resolution....  strange but true!

---

