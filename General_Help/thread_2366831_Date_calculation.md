---
title: "Date calculation"
date: 2017-07-22
forum: General Help
---

### Post by zkab on 2017-07-22
I have two dates and want to see the difference in hh:mm:ss but it seems that when I pass 24 hours then I get HH set to 00.
Part of my script looks like:
```

echo $s1
echo $s2
sum_tot=$(date -u -d @$(($(date -d "$s2" '+%s') - $(date -d "$s1" '+%s'))) '+%T')
echo $sum_tot
```
but I get :
2017-07-20 11:10:01
2017-07-22 11:55:01
00:45:00
Actually I want the hours to be accumulated like 24:45:00 ...

---

### Post by TheFu on 2017-07-22
Convert to seconds. Do the math, convert back to whatever format you want.  Just know that on 32-bit systems, this will fail sometime in 2038 when the 32-bit second counter rolls over to 0.  It shouldn't be an issue on 64-bit systems, in theory.

I've never attempted these calculations in Bash - perl is my poison of choice.  Can't see any reason why it shouldn't work in Bash.
Google found this: [https://www.cyberciti.biz/faq/shell-script-to-get-the-time-difference/](https://www.cyberciti.biz/faq/shell-script-to-get-the-time-difference/)
Their example uses seconds too.

When I have issues with commands that I think will work, I simplify and test.  If that doesn't show the issue, then I simplify again and test again. Over and over.

---

### Post by Keith_Helms on 2017-07-22
Try something like this to convert the two dates to seconds and format the seconds between them as hh:mm:ss.
```
    
    secs1=`date -d "$s1" +"%s"`
    secs2=`date -d "$s2" +"%s"`
    elapsed=$(($secs2-$secs1))
    es=$((elapsed % 60))
        em=$(((elapsed / 60) % 60))
        eh=$((elapsed / 3600))
    if [ $elapsed -lt 3600 ]
    then
        elapsedtime=`printf '%d:%02d' $em $es`
     else
        elapsedtime=`printf '%d:%02d:%02d' $eh $em $es`
    fi
    echo $elapsedtime

```

---

### Post by zkab on 2017-07-23
> **Keith_Helms said:**
> Try something like this to convert the two dates to seconds and format the seconds between them as hh:mm:ss.
```
    
    secs1=`date -d "$s1" +"%s"`
    secs2=`date -d "$s2" +"%s"`
    elapsed=$(($secs2-$secs1))
    es=$((elapsed % 60))
        em=$(((elapsed / 60) % 60))
        eh=$((elapsed / 3600))
    if [ $elapsed -lt 3600 ]
    then
        elapsedtime=`printf '%d:%02d' $em $es`
     else
        elapsedtime=`printf '%d:%02d:%02d' $eh $em $es`
    fi
    echo $elapsedtime

```

Thanks - worked like a Swiss clock ...

---

