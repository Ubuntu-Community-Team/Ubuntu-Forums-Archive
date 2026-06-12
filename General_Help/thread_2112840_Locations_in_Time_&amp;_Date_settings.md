---
title: "Locations in Time &amp; Date settings"
date: 2013-02-05
forum: General Help
---

### Post by GeoffreyBernardo on 2013-02-05
Where can I get the database of locations Ubuntu uses in the Time & Date settings?

---

### Post by papibe on 2013-02-05
Hi GeoffreyBernardo.

More like a directory tree really:
```
/usr/share/zoneinfo/
```
They are all binary files. To see their content you can use 'zdump'. For instance:
```
zdump -v /usr/share/zoneinfo/America/Chicago
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by GeoffreyBernardo on 2013-02-06
Hi @papibe,

I tried it, but zdump did not give me the output I actually want.

> $ zdump -v /usr/share/zoneinfo/South\ Africa
/usr/share/zoneinfo/South Africa  -9223372036854775808 = NULL
/usr/share/zoneinfo/South Africa  -9223372036854689408 = NULL
/usr/share/zoneinfo/South Africa  9223372036854689407 = NULL
/usr/share/zoneinfo/South Africa  9223372036854775807 = NULL
What I was looking for is a list of tows/cities by province (specifically in South Africa) as shown in this Locations dialog which is part of Time and Date Settings.

---

### Post by rnerwein on 2013-02-06
> **GeoffreyBernardo said:**
> Where can I get the database of locations Ubuntu uses in the Time & Date settings?
hi
to get the time of the database ubuntu is running makes no sence. it's a internet (and that is meaning w"orld" "w"ide "w"web 
your box must to now where the updates are comming form and syncronise the time and date. (do you got ntpd running ?). manual in the net you got no change. the system will do the synchronication.
cheers

---

