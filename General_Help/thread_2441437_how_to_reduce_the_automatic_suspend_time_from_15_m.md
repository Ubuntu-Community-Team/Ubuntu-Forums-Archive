---
title: "how to reduce the automatic suspend time from 15 min to 5 min?"
date: 2020-04-23
forum: General Help
---

### Post by tojonukokhadush on 2020-04-23
my system works on direct power as my battery does not support at all. now when the power is out suddenly, i get only few minutes life before the laptop dies. so what i expect is if i could reduce the automatic suspend time from 15 min to say 5 minutes or still lower, i could save my system from crashing. is this possible anyway?

---

### Post by TheFu on 2020-04-23
A battery that bad would mean that suspend shouldn't be used either.  Look for hibernation instead, but not if you care about security. Hibernation is anti-security.

---

### Post by tojonukokhadush on 2020-04-23
okay i manged it in other way. i assigned shortcut key for hibernate so that i could hit them as soon as the power is off. this saves me a lot in my available time. hybrid suspend seems to be what i had expected but it needs to be worked in system files which i am not daring as i am just a newbie in programming.

i was curious how hibernation is anti-security; could you elaborate that for me? thanks in advance.

---

### Post by TheFu on 2020-04-23
> **tojonukokhadush said:**
> okay i manged it in other way. i assigned shortcut key for hibernate so that i could hit them as soon as the power is off. this saves me a lot in my available time. hybrid suspend seems to be what i had expected but it needs to be worked in system files which i am not daring as i am just a newbie in programming.

i was curious how hibernation is anti-security; could you elaborate that for me? thanks in advance.

Hibernation takes a copy of all RAM and stores it in the swap file.  Anyone who can access that file in anyway will have access to the full contents of RAM.  That probably includes passwords, crypto-keys, browser logins, and if you left a password manager running, everything inside that program's DB.

Standby keeps the RAM full, but uses a little power to keep the RAM active. With a battery that has 5 minutes of runtime, I'd guess that standby time might be 20 minutes, then all work would be lost.

I use full-disk encryption on my laptops, which encrypts the swap file/partition/LV, but not hibernation since someone with access to the disk would effectively have unlimited time to break the encryption layers.  

I use standby only when the system isn't being moved. The system batteries usually have 6-10 hrs of time. If I'm taking them in a vehicle, I'll shutdown completely since the data is much more important than the convenience to me.  I also use 2FA at boot time with a hardware key for a challenge-response to unlock the storage inside the system pre-boot.  

I wasn't always this way. Had a smartphone stolen while traveling and got to spend the next 8 months dealing with the data it had being leaked, having my contacts being hassled for all sorts of scams.  Within about 20 minutes of the phone being stolen, I'd changed all the account passwords on that device, but still ... it harmed my reputation with clients.  Reputations are hard to recover. As a consultant, there are few things more important.

---

### Post by tojonukokhadush on 2020-04-24
okay i got the point. thanks for the time. i guess this is solved for me. the info was useful.

---

