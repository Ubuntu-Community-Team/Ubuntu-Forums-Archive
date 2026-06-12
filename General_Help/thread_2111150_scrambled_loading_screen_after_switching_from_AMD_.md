---
title: "scrambled loading screen after switching from AMD to Nvidia"
date: 2013-02-01
forum: General Help
---

### Post by ZombieApocalypse on 2013-02-01
Hi. I've just treated myself to a GTX 660 ti (and very nice it is). 

I'm running Kubuntu 12.10 AMD64. My previous card was an AMD/ATI HD5850 for which I was using the catalyst 13.1 drivers and have now purged from my system. 

However, when my system boots I now get a scrambled loading screen after GRUB, which then changes into text which comes up with some error messages - something to do with being unable to load certain amd modules, but it's too quick to read (I'll try to take a photo tonight). I then get the KDE splash screen and Kubuntu loads normally. Even after installing the proprietary Nvidia drivers (using the current package installation which is version 304), I still get the scrambled loading screen followed by the error messages. 

The system mostly works as expected, but I get some graphical quirks (like strange colours when watching you tube videos, frequent screen tearing despite having v-sync enabled and variable window performance). I ran Team Fortress 2 in Linux Steam and that ran fine (60fps), aside from the frequent screen tearing despite v-sync being enable. Also watching a DVD in VLC was fine (ie normal colours and behaviour).

Is there another process I should have carried out after or before changing graphics cards?

I'm tempted to do a fresh install of the system.

---

### Post by furything on 2013-02-01
Hi
I had similar problems. 
Did you remove the amd drivers first before shutting down PC?

Boot into terminal remove amd and get nvidia-current.
Cannot remember if you you have to run any config or if the install does that for you. It sounds like you still have amd config in your xorg.conf

This post had same issues and is solved
[http://forum.manjaro.org/index.php?PHPSESSID=vuh8h729v9brdb99omcbpqpei1&topic=1153.15](http://forum.manjaro.org/index.php?PHPSESSID=vuh8h729v9brdb99omcbpqpei1&topic=1153.15)

have not see a guide anywhere though

also see this
[http://ubuntuforums.org/showthread.php?t=1148753](http://ubuntuforums.org/showthread.php?t=1148753)
which tells you how to regenerate the xorg.conf form scratch for nvidia
Examine the file before and after - at worst case rename the old file and get nvidia-xconfig to generate a new one

---

### Post by ZombieApocalypse on 2013-02-01
Hi. Yes I removed the AMD drivers the day before the card arrived! I also tried deleting the xorg.conf and generating a new one for the Nvidia card, but it didn't make any difference.

But I might work through that post you linked to and see how I get on.

---

### Post by furything on 2013-02-01
Did you do nvidia-settings?

Is it installed?

try going through this config first then run the nvidia-xconfig. Apparently it uses the info you set in settings.

I have a feeling when I swapped AMD for nNvidia I rebuilt my system from scratch. Had an LVM mapped as my /var/lib so after reinstall I just remapped LVM. It is a myth box so can't allow it down too long otherwise I miss recording my fav shows:D

I should state that I had my distro up to date and did the same with the new install before remapping.

Of course it may have been another reason such as doing a version upgrade as they have stuffed my myth box a number of times.

What was your reasoning for jumping ship AMD to nVidia?
From previous post you seemed to know all about AMD and quite happy with it?

---

### Post by ZombieApocalypse on 2013-02-01
Thanks, I'll give that a try.

---

### Post by ZombieApocalypse on 2013-02-02
Playing with the settings made no difference. In the end I did a clean install and now my display is working correctly with the Nvidia drivers.

---

### Post by furything on 2013-02-04
Yeah sometimes a reinstall is easier if you don't have any important data or an external hd to back up first.

---

