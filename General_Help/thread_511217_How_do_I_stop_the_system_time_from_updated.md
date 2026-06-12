---
title: "How do I stop the system time from updated?"
date: 2007-07-27
forum: General Help
---

### Post by oldcpu on 2007-07-27
I noticed that Ubuntu syncs the time with the server each time I disconnect and reconnect.  How do I stop this?

I know that the server time it connects to and syncs is more accurate, but local time is 2 or 3 minutes off.  So I have adjusted my time with BIOS.  But it gets reseted/updated/synced each time I disconnect and reconnect.

---

### Post by tgm4883 on 2007-07-27
Right click the time on the panel, select adjust date & time.  Then change configuration from keep synced with internet servers to manual

---

### Post by oldcpu on 2007-07-28
Not using Gnome/KDE/XFCE.

How would I do this from the terminal?

---

### Post by tgm4883 on 2007-07-28
Well you could remove ntp all together

sudo apt-get remove ntp ntpdate

---

### Post by Hallvor on 2007-07-28
> **oldcpu said:**
> I noticed that Ubuntu syncs the time with the server each time I disconnect and reconnect.  How do I stop this?

I know that the server time it connects to and syncs is more accurate, but local time is 2 or 3 minutes off.  So I have adjusted my time with BIOS.  But it gets reseted/updated/synced each time I disconnect and reconnect.

I just removed it,since it dropped my connections in aMule.. Have no idea why.

---

