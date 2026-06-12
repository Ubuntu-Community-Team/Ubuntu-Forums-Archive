---
title: "X11 server instability"
date: 2006-08-01
forum: General Help
---

### Post by siplus on 2006-08-01
I installed Ubuntu 6.06 a few short days after it was released and loved it. It's replaced my previous installs of ubuntu and fedora without question, except for one thing I have noticed at varying degrees of severity.

I always leave my computer on while at college, and always leave programs running, primarily firefox, BOINC, some media player, and gaim.

This was fine with Ubuntu 5.10, but Dapper has been giving me problems when it is online for a prolonged period of time. Some of these problems incude programs crashing, unable to launch programs, or X11 crash (i just see black screen/ unresponsive GUI. ctrl-alt-del will show the system is unable to halt/shutdown, and a hard-reboot is required)

I figured my install of XGL and various other packages could have messed something up, so I did a fresh install of ubuntu on another partition and have been running it for about 3 weeks now instead of my first install. The same thing is happening. I will highlight occurances with gaim to hopefully give you and idea of what the problem may include.

Some mornings I would turn my monitor on and check for any messages from gaim, but it's not running. If I try to launch it, it immediately crashes. I must reboot the computer in order to launch the program.

The incredible thing is that it is apparently random! I may be away for a weekend and it'll still be running perfectly, or sometimes it can crash the first night after a boot.

I'm stumpted... I suppose it could be a hardware conflict of some type, perhaps RAM, but I honestly don't know. My computer is somewhat old now, as I built it probably 4 or 5 years ago with some components even older (ram ~ 2-3 years).

Basic overview of my hardware:
AMD 2600 (32-bit)
768mb DDR 266 (pc 2100)
nVidia GeForce ti 4200 (agp) (I'm using nVidia proprietary driver)
onboard VIA chipsets for lan/sound

I was planning on building a new computer this fall, but I was hoping my current one could still be stable. I'm not sure if it's a hardware problem or software, but I do have everything up-to-date on Dapper. Any help is appreciated!

---

### Post by zxee on 2006-08-01
Although it can be a pain looking through /var/log for messages might provide something or maybe doing dmesg right after this happens?

---

### Post by Riverside on 2006-08-01
> **siplus said:**
> I was planning on building a new computer this fall, but I was hoping my current one could still be stable. I'm not sure if it's a hardware problem or software, but I do have everything up-to-date on Dapper. Any help is appreciated!Do you have a screensaver configured?  If so, this may be your issue:

[http://www.ubuntuforums.org/showthread.php?p=1260256](http://www.ubuntuforums.org/showthread.php?p=1260256)

---

### Post by siplus on 2006-08-01
@zxee:

I just opened up /var/log/dmesg but I couldn't distinguish between normal messages and possible error messages. I can post if it may help identify the problem

@Riverside:

I have the screensaver running when idle, and it is what reminded me to install the nvidia proprietary drivers. I happened to be taking Organic Chem this summer, so I loaded up the 'molecules' screensaver which is apparently very demanding on the computer graphics because it was slow to render with the default driver.

I'll try using a different screensaver and see if ubuntu stops freezing up. I may just have to wait until I build a new computer to use that screensaver!

I will post in this thread next week or so to let the googler's know if it worked.

If I may ask, where would I file a bug report?

---

