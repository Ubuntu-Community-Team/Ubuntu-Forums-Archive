---
title: "Choppy graphics"
date: 2013-12-20
forum: General Help
---

### Post by slaya786 on 2013-12-20
I've been using Ubuntu 12.10 for quite some time now and I really enjoy the experience, especially in comparison to Windows. I have one general issue though, that is, the graphics are choppy. Specifically, if i'm scrolling (in a browser, terminal, gedit, ect) the scrolling is not smooth at all and almost seems as if it is refreshing the page every time I scroll. Another example would be, when dragging a window around it's very laggy and choppy, very similar to the scrolling experience.

A comparison of what i'm experiencing would be similar to a Windows install without graphics drivers installed. In that, everything works, just really choppy. As a note, video playback is fine.

My assumption would be a problem with the graphics drivers or settings in general. I'm curious to know if these symptoms are to be expected in Ubuntu?

I'm currently running Ubuntu 12.10 as stated earlier, with the latest AMD graphics (13.12), on my laptop, AMD A6-3420M APU with Radeon(tm) HD Graphics × 4.

I do intend to upgrade to 13.10, although, I don't think that would make any difference for this problem.

It's a very annoying problem that i've dealt with for a while, and any input regarding a fix or solution would be greatly appreciated.

Thank you

---

### Post by ajgreeny on 2013-12-20
With your AMD A6-3420M graphic card I think you can only use the open source radeon driver that was used at installation, so if you've added another proprietary driver I suggest you remove it to see if that overcomes any confusion in the system.

---

### Post by slaya786 on 2013-12-20
I've uninstalled all flgrx/amd drivers, and reverted back to the open source drivers. However, i'm still experiencing the same issues.

I'm confident my hardware is fast enough, because under Windows everything runs really smooth.

---

### Post by ajgreeny on 2013-12-20
I think I may have jumped too quickly here, thinking the AMD 3420 was the graphic chip, but having taken more time to look in detail I see it is your cpu, and has a 6xxx series graphic card, which shopuld indeed work OK with a proprietary driver.

I wonder if your problem is related to your kernel version and perhaps an updated kernel may help.  I am running 12.04 so am not sure what kernel is used by default in 12.10, not how far you can go in getting a newer kernel for that version.

---

