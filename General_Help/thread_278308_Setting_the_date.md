---
title: "Setting the date"
date: 2006-10-16
forum: General Help
---

### Post by riksweeney on 2006-10-16
Hi,

I'm trying to set the date of my system clock. At the moment, if I type in date, I get

16 October 2006 09:00:00 UTC

I've tried using ntp to set the date correctly, but it can't connect to any servers. The date on my desktop is correct, but that's because I set the timezone that I'm in.

Does anyone know what I can do to fix this?

Thanks

Richard

---

### Post by yopnono on 2006-10-16
Have you tried system - admin - time/date

---

### Post by riksweeney on 2006-10-16
> **yopnono said:**
> Have you tried system - admin - time/date

I have done and set my Timezone to Europe/London, but when I save the changes and type date into the shell, it brings back UTC again.

When I go back into configuring the date, it then says Europe/London UTC (at the moment it should be saying BST).

---

### Post by CatKiller on 2006-10-16
I suspect that **date** will always return UTC unless you tell it not to.

If you're bothered by the fact that the hardware clock is set to GMT regardless of what the clock says, [this]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29") might help.

---

### Post by riksweeney on 2006-10-16
> **CatKiller said:**
> I suspect that **date** will always return UTC unless you tell it not to.

If you're bothered by the fact that the hardware clock is set to GMT regardless of what the clock says, [this]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29") might help.

Thanks for the link. The clock being UTC only became a problem when I was doing some Java to make a thread execute at a particular hour, and it wouldn't. It took me quite a while to realise it was because the system clock was an hour behind the clock on my desktop! I'll give your suggestion a go when I get home from work.

---

