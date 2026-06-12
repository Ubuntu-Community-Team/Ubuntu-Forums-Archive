---
title: "internet time?"
date: 2007-08-21
forum: General Help
---

### Post by Chymera on 2007-08-21
the system watch in linux can be set to 12hour, 24hour unix time, and internet time. How do i "read" the last two?

---

### Post by mcduck on 2007-08-21
Unix time counts seconds from midnight (UTC) of January 1, 1970. It's how all Unix-and Linux-based systems count time internally. Some of the log files also use this time format.

Internet time divides the day into 1000 "beats", and has no time zones, instead always using BMT (UTC+1). It was created by Swatch and was supposed to be universal time format for Internet use (as using it the time is always the same, no matter what time zone you are in.).

Having your clock display either one of these would be more of a curiosity, not anything useful, so you probably don't even want to try to actually read them..

[http://en.wikipedia.org/wiki/Unix_time]("http://en.wikipedia.org/wiki/Unix_time")
[http://en.wikipedia.org/wiki/Swatch_Internet_Time]("http://en.wikipedia.org/wiki/Swatch_Internet_Time")

---

### Post by Spr0k3t on 2007-08-21
You may be referring to internet time as "swatch beats".  A fad from the 90s that never made big.  More details on swatch beats can be found here on the wiki: [http://en.wikipedia.org/wiki/Swatch_Internet_Time](http://en.wikipedia.org/wiki/Swatch_Internet_Time)

24HR time, aka military time is more or less the same as 12HR time without AM or PM.  Unix time is a little different and confusing to explain really... so here's another wiki link: [http://en.wikipedia.org/wiki/Unix_Time](http://en.wikipedia.org/wiki/Unix_Time)

---

### Post by Spr0k3t on 2007-08-21
> **mcduck said:**
> Unix time counts seconds from midnight (UTC) of January 1, 1970...

Arg!  Bested by mcduck!

---

### Post by Chymera on 2007-08-21
> **Spr0k3t said:**
> 
24HR time, aka military time is more or less the same as 12HR time without AM or PM.
Pffff ..... 10x for the info man how did you find that out? do you work in the army?

---

### Post by Spr0k3t on 2007-08-21
I R Clock 13:37!  :lolflag::lolflag:

---

