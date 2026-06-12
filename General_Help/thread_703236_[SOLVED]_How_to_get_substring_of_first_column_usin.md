---
title: "[SOLVED] How to get substring of first column using gawk command in shell?"
date: 2008-02-21
forum: General Help
---

### Post by abcuser on 2008-02-21
Hi,
I am using Ubuntu 7.10 Desktop and i would like to write script in bash shell to to get all rows from log file that first 10 characters representing current date are equal to current date.

Sample of my data:
```

2008-02-20-15.57.59 AAA XXX
2008-02-21-09.51.30 BBB XXX
2008-02-21-09.52.38 CCC XXX

```

Result: I would like to get second and third row because first 10 characters are '2008-02-21' which is today's date.

I have written so far:
```

CURRENT_DATE=`date '+%Y-%m-%d'`
echo $CURRENT_DATE  --> displays 2008-02-21
gawk 'substr($1,1,10)=="2008-02-21" {print $0}' myfile.txt 

```
Above code works, but I don't know how to replace "2008-02-21" in gawk command with variable $CURRENT_DATE. I tried:
gawk 'substr($1,1,10)==$CURRENT_DATE {print $0}' myfile.txt
but it doesn't work.

Any help is appreciated.
Regards,
Abcuser

---

### Post by abcuser on 2008-02-21
Hi,
I have found out the solution:
```

 gawk 'substr($1,1,10)==CURRENT_DATE {print $0}' CURRENT_DATE=`date '+%Y-%m-%d'` myfile.txt

```
Thanks,
Abcuser

---

