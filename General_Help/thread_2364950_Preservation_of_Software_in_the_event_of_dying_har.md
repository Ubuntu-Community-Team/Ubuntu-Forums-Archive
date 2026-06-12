---
title: "Preservation of Software in the event of dying hardware"
date: 2017-06-30
forum: General Help
---

### Post by bask185 on 2017-06-30
I was not sure in which forum tree I should put this, so I hope I guessed right.

At our work we produce human machine interfaces. These are panel PCs at the moment. Applications for these panel PC are still being developped in Visual Basic 6 on a windows 7 PC. Because these systems are getting obsolete I have been doing research for a more Open Source replacement. Long story short, I have set up a Raspberry with a touchscreen for which I can cross-compile Qt applications.

I have set-up a PC with Ubuntu 16.04, I installed Qt creator and with instructions from [www.qtrpi.com](www.qtrpi.com) and I downloaded and installed compilers so I can cross-compile for the Pi. I would like to keep this setup for as long as possible, say 10 years. As long as this PC does not die, I am good. Unlike Windows I have no fears for virusses and mallware when the support stops, besides I barely use the internet on that PC at all. 

But if my PC would die in say 7 years, I would have to set-up a new system. I can safe a copy of 16.04 LTS on a USB stick, but I would also have to set up the system again for cross-compiling. So I would also need to install the same versions of Qt and Qt creator and the right compilers. The Raspberry's OS can be cloned 101 so that is not a problem. It is likely that in 10 years, Qt still supports cross-compiling for the Pi but it is not guaranteed. And there are also no guarantees that I don't have to change settings of the Rpi with it's current set-up. 

TL:DR version: I need to back up my current version of Ubuntu 16.04 LTS with the Qt software and compiler settings.

I collected 4 ideas:
- I understand that one can run Ubuntu live from an USB stick. If I do this and if I than install Qt and the compilers (is this even possible??), can I than use this USB stick on every/most PCs and use Qt creator to produce binaries for the Rpi?
- I could download all the required software and preserve that on either a usb stick or network storage. The usb stick/storage would contain the OS, Qt and Qt creator and the Compiler stuff. I would have to try an offline installation to see if this is viable.
- Our ICT expert said that use of a virtual machine like 'virtual box' or 'VM ware' would be the most practical. I have no experience with this but I've been told that you can send entire programs over the internet and people with virtual machines could run it. According to the ICT expert this would be the most practical solution.
- He also told about a certain way which involves a server. This way would remember everything you do with the OS and stores that what you downloaded in the progress. I believe you could install an OS an a PC and use the server in combination with a script which sets up your PC perfectly. But this was way too to far over my head [CENTER][COLOR=#000000]:confused: 

[/COLOR][/CENTER]I was hoping if anybody on this forum has experience with backing up his/her OS and applications and can give me some advice or share his/her findings.

---

### Post by TheFu on 2017-06-30
That's a bunch of background for a backup question.  

TL;DR
You should search these forums for all the backup threads and read them.

Longer answer ... 
Any computer that is connected to any network needs to be correctly maintained.  Risks don't just come from the internet, but from any other method that contact to the outside world might occur. That would include any networking, any wifi, any bluetooth or any storage that might be connected.  If there is a USB port on the device that isn't 100% disabled, then someone could harm the system using it.

Please don't make that mistake.

10 years is unrealistic.  4 yrs is all the support left on 16.04.  There is a trade-off that we've all learned the hard way.  You can

[INDENT]* wait as long as possible and try to do major migrations every 5-10
  yrs.  But look at how that worked out for all those companies still
  running WinXP.  Basically, they've gotten into a situation where they
  cannot migrate - ever.
  Since very few others are trying to migrate from 10+ yrs ago, you are
  completely on your own.[/INDENT]

[INDENT]* Move every 2 yrs to a new, well-supported, OS.  Since everyone else is
  also moving to the newer OS at the same time, you aren't alone. People
  will have similar reference points and memories.  Commonly experienced
  issues will be readily solved.  Waiting even 4 yrs and that collective
  memory is vastly reduced.[/INDENT]

I moved my last server from 12.04 to 16.04 just a few months ago.  I'd moved about 15 other systems from 12.04 --> 14.04 2 yrs earlier and didn't have nearly as many little issues.  Finding solutions was much easier back then.

Raspberry Pi lifespans of 10 yrs would not be something I expected. By that point, a $5 replacement Pi will be 50x faster with 5x the RAM.

So this is a back question? Really?
If you want a 100% clone, then just clone the disk.  dd, ddrescue, clonezilla, partimage, are all tools that do it.  The backup storage really doesn't matter, but if it is the same size/type, you can completely clone it - bit for bit.  A clone isn't a good backup, since it isn't versioned and isn't efficient with storage as files change over time.

Virtualization is a commonly used method, though I've never done it between Intel-x86 and ARM.  I suppose it should be possible.

Your ICT guy (never heard of ICT before) might be correct. It appears you have misunderstood some of the key parts or over-simplified what that person said.  It really depends on the production environment and location.  The safe bet would be to select a virtual machine host for the deployment, then you can just push out a new VM image as needed.  That will entail GBs of updates, which might be a terrible idea.  There are lots of methods and tools to clone an OS, but in an efficient way - look into rsync - for example.

BTW, for years I earned a living writing code for a platform I didn't have, couldn't touch and only got to test via batch test submissions. I could compile my code, but couldn't link it into the full program.

You should search these forums for all the backup threads. There are probably thousands. I know I've commented on hundreds and it would be more efficient than retyping what has already been posted by many, smart people here.

---

### Post by TheFu on 2017-06-30
[http://wiki.qemu.org/Documentation/Platforms/ARM](http://wiki.qemu.org/Documentation/Platforms/ARM) is how to emulate ARM on x86.  Emulation is slower than virtualization, but for slower ARM CPUs, I'd expect a mid-level Intel CPU to be fine.

---

### Post by Autodave on 2017-06-30
Let me give you another possibility. This is one that I did. I needed an older version of Audacity to record with. Because of many changes made by Audacity, the newer version would not/could not do what I needed. Fearing that I may someday have the HD die and I would be at a loss to do what I needed, and not having an identical HD to clone it to, I simply removed my HD and installed another and did a new installation to that drive. I have a second drive installed to save all of the files that Audacity creates. I even have the first HD (with the system installed on it sitting in a slot inside the case. If and when the current HD dies, all I need to do is pull the cover, swap 2 connectors, and life goes on. (At least until the drive dies. :-))

---

### Post by QIII on 2017-06-30
*Moved to **General Help***

---

### Post by bask185 on 2017-07-03
> **TheFu said:**
> 
If you want a 100% clone, then just clone the disk.  dd, ddrescue, clonezilla, partimage, are all tools that do it.  The backup storage really doesn't matter, but if it is the same size/type, you can completely clone it - bit for bit.  A clone isn't a good backup, since it isn't versioned and isn't efficient with storage as files change over time.

You cannot simply clone the disc as it would not work on a different computer. For this to work, I would need an exact same system because of driver settings and such. We do this with our panel PC's where the hardware is the same. I just noticed that my PC has a Windows Vista sticker on it ):P to give an indication of how ancient my PC already is :D

I'll take a look on the other backup posts

---

### Post by bask185 on 2017-07-03
> **Autodave said:**
> Let me give you another possibility. This is one that I did. I needed an older version of Audacity to record with. Because of many changes made by Audacity, the newer version would not/could not do what I needed. Fearing that I may someday have the HD die and I would be at a loss to do what I needed, and not having an identical HD to clone it to, I simply removed my HD and installed another and did a new installation to that drive. I have a second drive installed to save all of the files that Audacity creates. I even have the first HD (with the system installed on it sitting in a slot inside the case. If and when the current HD dies, all I need to do is pull the cover, swap 2 connectors, and life goes on. (At least until the drive dies. :-))
 Yeah this I get but...

What if on one day, your CPU dies and you cannot get a new one??

---

### Post by QIII on 2017-07-03
> **bask185 said:**
> You cannot simply clone the disc as it would not work on a different computer. For this to work, I would need an exact same system because of driver settings and such.

Which is why you uninstall all proprietary drivers on a hardware installation  before cloning.  The kernel sorts out what it needs to use on the new system -- hardware or virtual (if you are moving one VM to another).  This does, in fact, work.  I have done it many times.

Hardware x86 to ARM?  Well, a quite different kettle of fish.

Need a new CPU and can't find an exact replacement?  Pop a new motherboard and a shiny new model of CPU in, hook things back up and push the power button.

---

### Post by TheFu on 2017-07-03
> **bask185 said:**
> Yeah this I get but...

What if on one day, your CPU dies and you cannot get a new one??

x86 compatible CPUs are close enough to being the same that is isn't an issue.  I've swapped HDDs between Pentium 4 computers and Core i7 computers. It booted and worked fine on the real hardware.  The worst problem would be with RAID cards or video drivers.  That's pretty much it as far as booting.

What if the HDD has failed?

What if the motherboard failed?

What if the GPU (addon or built-in) failed?

The same solution works.  Replace the failed hardware and either move the old disk into the new hardware or restore from a backup onto a new HDD/SSD/storage device.  SATA is SATA is SATA almost always with Linux.  x86 is x86 is x86 (close enough) that the OS deals with the changes going forward.  Going backwards isn't as easy, but going forward seems to **always** work.

If you use a HW-RAID card, then things become a little more complex, but if you use Linux software RAID, and I do, then it really is as simple as unplugging from the old system and connecting to the new system.  The OS settings are pulled forward and the RAID sorta ... just works.  I've done this 3 times with my home system expecting issues.  Never saw any issues moving a software RAID from 10.04 to 12.04 to 14.04 on different physical hardware running Ubuntu Server.

With ARM, the future is less clear. Those CPUs aren't as mature, but if you start with an ARM-64 type CPU, I wouldn't really be that concerned.

Did you know that Intel (and others) 80386 CPUs can be purchased today?  They are really cheap. Bet you can find whatever CPU you need. Motherboards are more scarce.  I haven't seen a failed CPU in a very long time.  The major vendors of CPUs have put in so many protections that prevent burnout it just doesn't happen.  Before a modern CPU overheats, it will turn off cores, slow down cores, protect against total failure.  But if you take a huge hammer at it, it will shatter.  That is sorta fun, for about 10 seconds.  ;)

A well thought out disaster recovery plan mitigates all of these issues. The main issue with poor DR planning is people tend to have the failover systems too close to the primary system.  My rule of thumb is at least 500 miles apart to mitigate regional disasters. I did this sort of planning for a living for almost a decade.

---

