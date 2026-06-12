---
title: "How to enable adjust for daylight saving time"
date: 2008-03-31
forum: General Help
---

### Post by ario on 2008-03-31
Hi
I've installed Ubuntu 7.10 AMD64 on my desktop. Orginally I didn't enabled "Automatic adjust for daylight saving time (DST)" in installation. Now I want to enable DST. but I can't find any button to enable that.
So how can I enable adjust for daylight saving time?
Thanks a lot for your attention.

---

### Post by erginemr on 2008-03-31
I suggest you to read:
[http://ubuntuforums.org/showthread.php?t=150472&page=2](http://ubuntuforums.org/showthread.php?t=150472&page=2)

esp. page 2 to get more insight to how Ubuntu addresses the computer clock in the presence of a dual-boot with Windows. This information was new to me as well.

The file in question is: **/etc/default/rcS**, where you can edit the "UTC=..." parameter.

But I suggest you to right click Gnome clock, select "Adjust Date & Time", from where you can install automatic web update support, whereupon the system clock will update itself from world-wide NTP servers.

---

### Post by ario on 2008-03-31
This is all about time all about date all about time zones but not **AUTOMATICALLY ADJUST CLOCK FOR DAYLIGHT SAVING TIME (DST)** Im getting sick for this:(

---

### Post by erginemr on 2008-04-01
> **ario said:**
> This is all about time all about date all about time zones but not **AUTOMATICALLY ADJUST CLOCK FOR DAYLIGHT SAVING TIME (DST)** Im getting sick for this:(


> ...But I suggest you to right click Gnome clock, select "Adjust Date & Time", from where you can install automatic web update support, whereupon the system clock will update itself from world-wide NTP servers...

But I believe setting the clock to be adjusted via NTP servers should also let them adjust it automatically in accordance with DST...

---

### Post by erginemr on 2008-04-01
Besides, the link I gave has interesting points, such as:

-> Having both Windows and Ubuntu handle daylight saving time can confuse the system with redundant time shifts in a dual-boot system. So, the question is whether you are dual-booting or not.

-> Editing the file /etc/default/rcS with
```
gksudo gedit /etc/default/rcS
```
and changing the UTS parameter to either: **UTC=yes** or **UTC=no** seems to enable/disable DST functionality.

(P.S. The biggest asset of a Linux user is *patience*.)

---

### Post by ario on 2008-04-02
> **erginemr said:**
> Besides, the link I gave has interesting points, such as:

-> Having both Windows and Ubuntu handle daylight saving time can confuse the system with redundant time shifts in a dual-boot system. So, the question is whether you are dual-booting or not.

-> Editing the file /etc/default/rcS with
```
gksudo gedit /etc/default/rcS
```
and changing the UTS parameter to either: **UTC=yes** or **UTC=no** seems to enable/disable DST functionality.

(P.S. The biggest asset of a Linux user is *patience*.)

Thanks. I think this one works for me. I've changed the UTC to Yes instead of No and now my clock working just like a clock!:)

---

### Post by erginemr on 2008-04-02
Great! :D I also advise you to setup your clock to automatically update itself via NTP servers by right-clicking on it, assuming your machine is connected to the Internet.

Take care.

---

