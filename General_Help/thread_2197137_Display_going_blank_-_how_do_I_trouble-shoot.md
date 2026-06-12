---
title: "Display going blank - how do I trouble-shoot"
date: 2014-01-02
forum: General Help
---

### Post by guitars.gerry on 2014-01-02
I just set up an Ubuntu 12.04 system for my wife for Christmas... brand new desktop system. It's been running for a couple of weeks now, and yesterday we noticed some funny behaviour. 3 or 4 times during the evening, while my wife was on Facebook, or playing solitaire, etc. the screen went blank, as if the screensaver had kicked in. However, on one occasion the mouse pointer was still visible, and on another occasion, a cursor was blinking in the upper left corner (as if the computer were in text mode). Every time, we were able to get the desktop display back, on one occasion it came back when I hit the Super key. As I said, this seemed to just start yesterday. Clearly, I need to learn a little more about what is going on here before I can fix it (whatever it is). So, my question is, is there a log file that I could check after this happens, that might be able to tell me a little more about why the screen went blank? I checked in /var/log/ and had a look at a few of the log files... syslog, Xorg, etc. but didn't see any entries that seemed to be related to these screen blanking episodes.

A little about the system, that may be relevant:
- 64 bit 12.04 Ubuntu, everything updated
- i5-4670 CPU with integrated graphics
- SSD ADATA 128GB (single boot system, single partition)
- ASUS H87M-E Socket 1150 motherboard
- 8 Gig RAM
- running vanilla Unity desktop (I do have Screenlets installed, and have gotten some error messages as a result, and do suspect this could be related to the problem - but don't want to start making all kinds of changes until I better understand what's going on.)

Given that I have about one week left in the first 30 days, during which the store (Canada Cumputers) offers direct in-store warranty support (after that, I am dealing with the manufacturer), I would like to be able to rule out any hardware problems (e.g., with the integrated graphics).

---

### Post by guitars.gerry on 2014-01-03
Since posting yesterday, my further reading on this subject led me to two observations: (1) the screensaver in Ubuntu, whether in 12.04 or later versions is rather unpredicable at best, and (2) recent Intel graphics, such as the Intel HD 4670 on my new system, are better supported in the more recent versions of Ubuntu. On that basis, I decided to install 13.10 (I had originally installed 12.04, as my other Ubuntu box is running 12.04.) So far this morning, with 13.10 freshly installed and updated, the screensaver behaved as it should... that is, I set it to shut off the display after 60 minutes, and it did so. I'll post back on any further developments.

---

### Post by Bucky Ball on 2014-01-03
Welcome. Yep, keep an eye on it for 24 hours and if all still good mark it solved (instructions how in my signature).

13.10 will work better on some very new hardware and the bonus is it is upgradeable to the next LTS release, 14.04 LTS, when that is released in April. That will be supported for five years (13.10 is an interim release and only supported for nine months).

---

### Post by guitars.gerry on 2014-01-04
So over 24 hours later the 13.10 installation seems to be working fine with the Intel HD 4670 graphics.

---

