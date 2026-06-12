---
title: "5 minute boot time"
date: 2008-05-06
forum: General Help
---

### Post by getabetterpic on 2008-05-06
Hi, I've done some searches trying to find something that will improve my boot time.  I'm running Xubuntu 8.04 with the following hardware.  Oh, this is a laptop btw.

366 MHz Pentium II
256MB RAM
Integrated Video
Wireless PCMCIA card
30 GB Hard Drive

I've gotten everything to working correctly (well, most.  The tab key doesn't work :confused:) but its taking about 5 minutes to boot up.  Even XP isn't taking but 1.5 - 2 minutes to boot.  What gives?  Would Fluxbuntu work any better?  I really like Xubuntu, and once it's booted it runs fine for what I do, but the wife isn't going to live with a 5 minute boot time.  Please help.  Thanks.

Daniel

---

### Post by darco on 2008-05-06
Wow thats a pretty old Lappy!....Check the output of dmesg and see if you can tell whats slowing it down...

darco

---

### Post by xwyantx09 on 2008-05-07
i know xubuntu uses gnome still if im not mistaken, I also know that Ubuntu has some RAM qualifications, youve gotten it installed, and im not sure of what the things are, but i know fluxbox does work better with less RAM so yeah that would more than likely fix that problem

good luck

---

### Post by getabetterpic on 2008-05-07
Xubuntu uses Xfce for windows management (I think that's different than gnome? but maybe I'm thinking about the wrong thing).  Xubuntu's recommended requirements are a 300Mhz and 256MB of RAM, so I'm right there with the recommended and well above the minimum.

I think I'm going to wind up using Puppy Linux, although I'm going to check out Fluxbuntu before making that call.  So far I really like Puppy aside from the graphics, and Puppy 4 is supposed to be a bit better.  So we'll see.  Although if someone can still give me some tips to getting Xubuntu booting faster, I'd still like to use it since it runs fine.

---

### Post by Zorael on 2008-05-07
You could install bootchart. It logs your boot process and draws a nifty diagram, which it saves somewhere in /var/log/. If it shows something taking an unreasonably long time to start up, well, perhaps something can be done about that. Chances are your system is just lazy, though.

Available from main repositories.

```
zorael@sunspire:~$ apt-cache search bootchart
bootchart - boot sequence auditing and chart generator
zorael@sunspire:~$ apt-cache policy bootchart
bootchart:
  Installed: (none)
  Candidate: 0.9-0ubuntu7
  Version table:
     0.9-0ubuntu7 0
        500 http://se.archive.ubuntu.com hardy/main Packages
```

---

### Post by getabetterpic on 2008-05-08
I had tried bootchart, but the couple times I had checked after rebooting, it wasn't outputting anything.

After subsequent reboots, Xubuntu is getting better though.  I'm down to a 2-3 minute boot time.  I'm dual-booting Xubuntu and Puppy for right now, going to see which one the wife likes better.

---

