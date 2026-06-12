---
title: "Change the formatting of hwclock to like it was in 16.04"
date: 2018-09-07
forum: General Help
---

### Post by crital on 2018-09-07
Hey,

We have an application which is fetching the system time via hwclock which represents the time in the following format:
     2018-09-07T11:03:56+02:00

However on our previous server (Ubuntu Server 16.04) hwclock represents the time in the following format:
     Fri 07 Sep 2018 11:26:52 AM CEST  .838868 seconds

Is there a way to change 18.04 to use the same formatting as 16.04 ?

---

### Post by Impavidus on 2018-09-07
Interesting. When I use hwclock I get this format:```
sudo hwclock --show
2018-09-07 19:47:30.139530+0200
```The manual page says```
       -r, --show
       --get
              Read the Hardware Clock and print its time to standard output in
              the ISO 8601 format.  The time shown is always  in  local  time,
              even   if  you  keep  your  Hardware  Clock  in  UTC.   See  the
              --localtime option.
```Your new version follows that standard, my version more or less (some variation is allowed, but there should be a T separating date and time) and your old version doesn't.

You could use **date** to convert the time from one format into another:```
date --date="date in one format" +"any format you like"
```Read the manual for date to see how you specify the format.

---

