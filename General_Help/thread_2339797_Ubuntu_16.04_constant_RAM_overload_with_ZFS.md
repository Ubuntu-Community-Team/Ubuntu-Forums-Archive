---
title: "Ubuntu 16.04 constant RAM overload with ZFS??"
date: 2016-10-12
forum: General Help
---

### Post by THEKINGDOM on 2016-10-12
So, I've been having this on-going issue with Ubuntu to the point where I've exhausted all ideas of why and I need help on the forums. 

**Version**: Ubuntu Desktop 16.04


**Issue**:  memory leak, constant RAM overload -16GB RAM total (usually sitting around 14gb) . The longer the system is left running the more and more RAM it consumes until the computer will become unresponsive. It usually becomes unresponsive after log-in, I'll be unable to click any desktop items. 
I'm running 2(x)3TB drives in a raid 1 format, only using 300GB of that space. I'm using the _ZFS built in_ filesystem. I suspected that this is the reason for high ram usage, but it should never use this much RAM. Even on FreeNAS is never used this much RAM.

Currently, "unity-setting-daemon" is using 1.9**GB** of RAM alone...??
"java" is using 364.7MiB

I recall running ZFS on an earlier version (can't remember.. maybe 15.04 **without** this issue), I always like to stay up-to-date.

Anybody have any suggestions? Is there a ZFS memory leak bug in 16.04?

---

### Post by Rich_Murphey on 2016-10-14
On 16.04, when using zfs, there is a command, arcstat.py, which will report the RAM used by ZFS:

[COLOR=#000000]/usr/sbin/arcstat.py
[/COLOR]    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  arcsz     c                                                                                                                                                                                                
11:34:19     0     0      0     0    0     0    0     0    0    36G   47G             


The above reports 47GB used on a system with 96GB ram.
This is the general case, where ZFS is using half the total physical RAM.

This is one way to tell whether there's a leak.

Note that ZFS needs a significant amount of RAM in order to perform well.
On systems with limited RAM available, other filesystesm, such as ext4, may be a better fit if performance is one's highest priority.

---

### Post by jerome1232 on 2016-10-14
Just a shot in the dark, but I've had the issue of nothing opening up when I clicked it, only it was actually because my file system had become read only due to my disk beginning to fail. Are there any errors in the tail end of dmesg when this happens? I was able to hit ctrl+alt+F1 and see errors getting printed out on that tty.

---

### Post by THEKINGDOM on 2016-10-14
> **Rich_Murphey said:**
> On 16.04, when using zfs, there is a command, arcstat.py, which will report the RAM used by ZFS:

[COLOR=#000000]/usr/sbin/arcstat.py
[/COLOR]    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  arcsz     c                                                                                                                                                                                                
11:34:19     0     0      0     0    0     0    0     0    0    36G   47G             


The above reports 47GB used on a system with 96GB ram.
This is the general case, where ZFS is using half the total physical RAM.

This is one way to tell whether there's a leak.

Note that ZFS needs a significant amount of RAM in order to perform well.
On systems with limited RAM available, other filesystesm, such as ext4, may be a better fit if performance is one's highest priority.


Wow I didn't know this command! Thank you!
time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  arcsz     c  
20:47:20     0     0      0     0    0     0    0     0    0   1.4G  1.4G

so we can say that this isn't ZFS.. hmmm.

unity settings daemon is using 3.1GB isn't that a lot?

---

### Post by THEKINGDOM on 2016-10-22
> **Robert_Matear said:**
> Wow I didn't know this command! Thank you!
time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  arcsz     c  
20:47:20     0     0      0     0    0     0    0     0    0   1.4G  1.4G

so we can say that this isn't ZFS.. hmmm.

unity settings daemon is using 3.1GB isn't that a lot?

BUMP

unity settings daemon is using 3.1GB isn't that a lot?
Seems like Ubuntu 16.04 has a serious memory leak to be using up all 16gb of RAM to the point that the computer starts freezing at around 14GB+ used.

The freezing generally happens right after login, the mouse and keyboard are still responding but the desktop icons cannot be clicked, nor anything in the status bar.

Any suggestions? I've tried a complete re-install a couple of months ago when I had more time on my hands, issue returned.

---

### Post by THEKINGDOM on 2016-11-02
okay.. ubuntu users... so I finally GAVE UP.. trying to figure out why my system was stalling with 16GB of ram pretty much maxed out.. went out to buy basically an entire new PC, best 1151 Motherboard, intel core i5 6600-1151, 32GB of DDR4 RAM, M.2 for base OS........
Now I'm running 16.04 with barely any programs.. downloading a few torrents to my newly installed ZFS mirror raid 1 storage and I'm using between 22-24GB of RAM... How is this possible??? Is ubuntu a RAM hog?
I could run a full fledges windows OS using not even a 1/3 of this amount of RAM..

Can anybody with knowledge please chime in.. this is getting ridiculous.

Thanks

---

