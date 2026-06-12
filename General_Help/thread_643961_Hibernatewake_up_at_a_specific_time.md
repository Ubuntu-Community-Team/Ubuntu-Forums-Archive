---
title: "Hibernate/wake up at a specific time"
date: 2007-12-18
forum: General Help
---

### Post by localgod11 on 2007-12-18
Is there away to make ubuntu hibernate and wake up at certain times? Say wake up at 8 and sleep @ 0030?

---

### Post by oscarsfriend on 2007-12-18
EDIT: I should add that the following requires you to get your hands dirty with some scripting.  So if you want to know if there is an easy way to do what you want: the short answer is (probably) no.

As far as waking up is concerned you should check this out: 

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

It's for MythTV running under Ubuntu, but it should do pretty much what you want.  However, you will almost certainly have to fudge things yourself, as BOISes are fairly idiosyncratic in how they deal with waking up.  Basically there are two methods: acpi, and nvram.  The second is a bit dangerous (from what I gather) as it involves flashing the BIOS to set the wake up time.  I use the first method which works perfectly, though I had to hack together my own script to do it (based on the above).  

As for hibernation, I can't help, as I never got it working, and am not really bothered about it as I have a desktop, and don't really see the point.  Shutting down automatically should be easy enough however, and could be done using cron.

---

### Post by njparton on 2007-12-18
Write a script for sleeping and get cron to run it for you.

Waking is probably more difficult as you'll need an eternal hard event (such as a button push) or soft event (such as a magic packet) to do this.

Cron will not obviously be running.

---

### Post by njparton on 2007-12-18
Ignore my post, the link above is excellent!

---

