---
title: "Dualboot Win8/Ubuntu: Rebooting into Windows, time/clock have changed"
date: 2014-03-25
forum: General Help
---

### Post by diablo75 on 2014-03-25
I noticed this behavior on a friends computer and didn't want to bother looking into it, but I just noticed that the same thing happens on my computer at home.  I don't use Ubuntu much these days but I was bored today and decided to apply all the latest updates before 14.04 comes out.  After rebooting back into Windows from Ubuntu I noticed that the time in the corner on the task bar read 7 hours earlier than the actual time (I'm central time by the way; don't know if that's relevant).  Is there a way to prevent Ubuntu from adjusting the system clock?  It seems like it is, in some way...

---

### Post by slooksterpsv on 2014-03-25
Ubuntu uses Universal Time; your BIOS and Windows use Local Time. That's why it shows like that, you can change Ubuntu to use Local time or Windows to use UTC its up to you. Here's an old (possibly outdated) article on it:
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by Mark Phelps on 2014-03-25
That's a long and complicated article.  

The "easy" way to fix this (which I have done repeatedly on multi-boot machines" is the following:
1) edit /etc/default/rcS
2) add or change the following section

    > # Set UTC=yes if your hardware clock is set to UTC (GMT)
    UTC=no

---

