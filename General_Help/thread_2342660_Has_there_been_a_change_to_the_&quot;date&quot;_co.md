---
title: "Has there been a change to the &quot;date&quot; command between 15.10 and 16.04?"
date: 2016-11-08
forum: General Help
---

### Post by inhumangeek on 2016-11-08
Good evening. I have a script which has been working fine for four years but I have just got around to upgrading from 15.10 to 16.04 LTS and now it seems to have broken. The (I think) relevant section of code is as follows:

```
date_started=`date`
date -d "$date_started"

```

This appears to be where my script is falling over as I get the error "date: invalid date ‘Tue  8 Nov 21:15:05 GMT 2016’". I believe this must have been working prior to the upgrade. I have had a bit of a search on this error and the resolutions mostly relate to daylight savings/time zones but I do not believe this is the problem here.

Can anyone shed any light please?

Many thanks.

---

### Post by SeijiSensei on 2016-11-08
What are you trying to accomplish?  The first line stores the date string in the date_started environment variable.  Why are you then running date again?  What output are you expecting?  Are you looking to retrieve the "Unix date," e.g, 1478640864?  For that, just use "date +%s".

---

### Post by inhumangeek on 2016-11-08
Hi, thanks for your reply. There is a bunch of superfluous code missing; in between those two lines I have a program which takes a while to run, and after a certain time I kill it. The full script compares the difference between two date commands to see if the right time has passed, and therefore needs to store the start time (in $date_started).

If you want a bit more context;

```
date_started=`date`
[main code]
date_now=`date`
date_diff=$(echo `date -d "$date_now" +%s` - `date -d "$date_started" +%s` | bc)
```

---

### Post by inhumangeek on 2016-11-08
(potentially there is a better way to find the number of seconds between two commands but I would still be interested to know why my script has stopped working!!)

---

### Post by SeijiSensei on 2016-11-08
I always put the format before any parameters:
```
date +%s -d 'some date string'
```

But why not just store the Unix date in the start and end variables and use expr like this

```

started=$(date +%s)
[stuff]
ended=$(date +%s)
elapsed=$(expr $ended - $started)
```

---

### Post by inhumangeek on 2016-11-08
That's great, appears to be working well. Thanks very much for your help. Haven't seen "expr" before.
If anyone knows what changed I would still be interested!

---

