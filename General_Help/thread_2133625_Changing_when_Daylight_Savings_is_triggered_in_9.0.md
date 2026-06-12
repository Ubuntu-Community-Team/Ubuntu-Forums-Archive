---
title: "Changing when Daylight Savings is triggered in 9.04"
date: 2013-04-08
forum: General Help
---

### Post by poe503 on 2013-04-08
I have some Mythtv setups that use 9.04 as the OS.  They work great so I am not interested in updates or improvements.  

They both set Daylight Savings on the wrong week and I would like to set them to do the change on the correct week.  I only use them for over-the-air broadcasts so they are not connected to the internet and can't update time that way.  

If someone could point me to the correct configuration file so I could change this, it would be greatly appreciated.  Thanks.

---

### Post by steeldriver on 2013-04-08
I *think* the crossover dates are defined in the appropriate binary tzdata file in /usr/share/zoneinfo ('appropriate' meaning the file corresponding to the contents of your /etc/timezone file)

```
$ cat /etc/timezone
America/Toronto
$
$ file -L /usr/share/zoneinfo/America/Toronto
/usr/share/zoneinfo/America/Toronto: timezone data, version 2, 4 gmt time flags, 4 std time flags, no leap seconds, 232 transition times, 4 abbreviation chars
$
```

There's a utility 'zdump' for looking at the file contents e.g. to see the DST / GMT defs for 2013

```
$ zdump -v $(cat /etc/timezone) | grep 2013
America/Toronto  Sun Mar 10 06:59:59 2013 UTC = Sun Mar 10 01:59:59 2013 EST isdst=0 gmtoff=-18000
America/Toronto  Sun Mar 10 07:00:00 2013 UTC = Sun Mar 10 03:00:00 2013 EDT isdst=1 gmtoff=-14400
America/Toronto  Sun Nov  3 05:59:59 2013 UTC = Sun Nov  3 01:59:59 2013 EDT isdst=1 gmtoff=-14400
America/Toronto  Sun Nov  3 06:00:00 2013 UTC = Sun Nov  3 01:00:00 2013 EST isdst=0 gmtoff=-18000
$
```

I don't know if there's a tool to edit the contents - I guess you could try just installing an updated tzdata deb package, or just grabbing the /usr/share/zoneinfo/XXX/YYY file from somewhere

---

### Post by poe503 on 2013-04-09
Thanks for checking this out.  It's much appreciated.  I'll see what I can do.

---

