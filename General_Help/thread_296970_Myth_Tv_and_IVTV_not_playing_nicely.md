---
title: "Myth Tv and IVTV not playing nicely"
date: 2006-11-10
forum: General Help
---

### Post by trubblemaker on 2006-11-10
OK so I got myth installed, looks awesome. Got data about all my channels, can even record.  Everything loads, runs.  But I recoded snow.  I checked recording with

```
 cat /dev/video0 > /tmp/test.mpg 
``` and it doesn't work it also records snow
```

ivtv-tune -c 16 -d /dev/video0 
cat /dev/video0 > /tmp/test.mpg 

```
but this also got snow, I changed a bunch of the maps, but still no love.   I did record tv earlier that day with the same commands.  Everything changed when I ran "mythtv-setup".  I got 13 channels on the first scan that wasn't good enough for me so I re-scanned.  Now i get none.  and snow when I record.  I checked the cable itself and it plays tv so I'm lost.  

(using hauppage pvr-350, with ivtv)

Any Ideas?  I will post ivtv dmesg later when I get home, but it was running fine with no obvious errors.

Please help.

---

