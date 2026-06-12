---
title: "clock"
date: 2013-10-02
forum: General Help
---

### Post by johntd on 2013-10-02
How do I keep my clock right, I have to go into windows on my duel boot system to put the clock right, if I try in Linux manualy it just reverts back to an old time, about 2 years back, why wont it keep up with the proper time, I have it set to check the internet time.

---

### Post by Kirboosy on 2013-10-02
Run the following command.

```
sudo ntpupdate ntp.ubuntu.com
```

Does that grab the right Time and Date?

Hope that helps!
~Caboose

---

### Post by tgalati4 on 2013-10-02
If this is an older computer, then perhaps your motherboard battery is dead.  If the clock is only off by your timezone versus GMT, then you might have to set your BIOS clock to GMT or to Local.  In Windows, there is a clock setting for GMT, use that.  But if the clock is being set to some random value, then your real time clock (rtc) on the motherboard is having issues.  Does the correct time display in BIOS?

---

