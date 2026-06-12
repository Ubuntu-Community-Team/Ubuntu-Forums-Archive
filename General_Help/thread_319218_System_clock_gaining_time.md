---
title: "System clock gaining time"
date: 2006-12-15
forum: General Help
---

### Post by theplatypus on 2006-12-15
The system clock on my dapper install is gaining timing at an alarming rate(10 min/day +-). Three days ago I noticed the time was off so I adjusted it to EST. Yesterday I noticed the time was off again by about 9 minutes and today its off by almost 20 minutes. 

Right now hwclock -r shows
Fri 15 Dec 2006 08:51:51 AM EST  -0.712580 seconds

While my system clock shows it as 9:12am. 

Any idea what is going on here?

---

### Post by mcduck on 2006-12-15
> **theplatypus said:**
> The system clock on my dapper install is gaining timing at an alarming rate(10 min/day +-). Three days ago I noticed the time was off so I adjusted it to EST. Yesterday I noticed the time was off again by about 9 minutes and today its off by almost 20 minutes. 

Right now hwclock -r shows
Fri 15 Dec 2006 08:51:51 AM EST  -0.712580 seconds

While my system clock shows it as 9:12am. 

Any idea what is going on here?

Most common reason for computer's clock running too fast is that the CMOS battery on your motherboard is dying. Replacing the battery with a new one should fix the problem. It's usually located somewhere around bottom right corner of your motherboard.

---

