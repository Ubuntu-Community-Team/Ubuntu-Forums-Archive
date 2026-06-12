---
title: "Rainman-like question on 'date' output"
date: 2015-07-09
forum: General Help
---

### Post by ofnuts on 2015-07-09
If  I do:
```

$date -d 00:00:00 +%s
1436392800

```

(ie show me the seconds since the Epoch of today at midnight) the answer is currently an integer multiple of 3600, in other words, an integer number of full hours happened between 1970-01-01 00:00:00 UTC and 00:00:00 today. Which for most people make sense since there was an integer number days (if in UTC+0 timezone) and a day is 24x3600 seconds. For those in other time zones, we get an integer number of days plus an integer number of hours... 

Not so fast.... how about leap seconds? Since they added a leap second recently (and AFAIK this isn't the first) there is no longer an integer multiple of 3600 seconds since the epoch at midnight... so I should be getting:

```

$date -d 00:00:00 +%s
1436392801

```

once the leap second has been added. Or is there a conspiracy to steal these precious seconds from our lives? Is this related to chemtrails?  Inquiring minds want to know.

---

### Post by limbenjamin on 2015-07-09
It should not end with a 1

That is because the ```
date
``` command is supposed to return the same time.

It would be a nightmare if the date was different depending on which output format you choose. There would be syncing issues if different applications choose a different format in obtaining the date from the system. Google explains it better. [http://googleblog.blogspot.sg/2011/09/time-technology-and-leaping-seconds.html](http://googleblog.blogspot.sg/2011/09/time-technology-and-leaping-seconds.html)

---

### Post by ofnuts on 2015-07-09
'-d' gives a date to display (otherwise you get the current time).

My point is: "date -d 00:00:00 +%s" returns the number of seconds between the Epoch and today at 00:00:00 (1436392800). If I issue "date -d 'tomorrow 00:00:00' +%s" I will get a new number which is 86400 (3600*24) seconds later: 1436479200. However, if there were a leap second inserted today, "date -d 'tomorrow 00:00:00' +%s" would be 8640[SIZE=5][COLOR=#ff0000]**1**[/COLOR] [/SIZE]seconds later, so "date -d 'tomorrow 00:00:00' +%s" should return 143647920[SIZE=5][COLOR=#ff0000]**1**[/COLOR][/SIZE], and all the "midnights" from now on would end with '1', until another leap second is inserted so that "midnights" end with '2', etc... And since there were 26 leap seconds inserted since 1972, we should currently have "midnights" end in "0026".

However, I just found the [Rainman-like answer](https://en.wikipedia.org/wiki/Unix_time). I'm a happy camper now. Please excuse me while I go to K-mart buy a new pair of boxer shorts to celebrate :)

---

### Post by limbenjamin on 2015-07-10
Apologies, was too quick to assume that -d changes the format. Have modified my answer above for future users.

The point still stands that "date" command should not return different dates in different formats. Case in point: if auth process uses the epoch time and your application uses human friendly format. Consider what would happen if you log in and immediately start your application within 26 secs. If you look through the logs, it will appear as though the application started before you logged in. This will have implications on data forensics.

---

### Post by ofnuts on 2015-07-11
> **limbenjamin said:**
> Apologies, was too quick to assume that -d changes the format. Have modified my answer above for future users.

The point still stands that "date" command should not return different dates in different formats. Case in point: if auth process uses the epoch time and your application uses human friendly format. Consider what would happen if you log in and immediately start your application within 26 secs. If you look through the logs, it will appear as though the application started before you logged in. This will have implications on data forensics.

I don't see where what I wrote can make you think that I would expect different formats to yield different time values. There is a precise second in time, counted as seconds since the epoch, which for someone in London is July 11th at 00:00:00, and for someone in most of western Europe is July 11th at 01:00:00. What I was talking about is that this second isn't the 1436569200th second since the Unix epoch, but the 1436569226th one because leap seconds should be taken in account. It happens that Unix somehow considers that midnight UTC is always N*24*3600, and use the same "second count" to designate a leap second and the regular second that precedes it (thus creating ambiguous timestamps...)

---

