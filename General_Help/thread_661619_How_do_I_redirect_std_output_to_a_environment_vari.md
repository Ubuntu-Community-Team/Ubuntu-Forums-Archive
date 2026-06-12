---
title: "How do I redirect std output to a environment variable?"
date: 2008-01-08
forum: General Help
---

### Post by WereWisher on 2008-01-08
I want to redirect the system time (in seconds)  to an environment variable for use in a shell script.  

thetime=date -u +%s 
doesn't work 

neither does 

thetime= date -u +%s
or 
thetime=(date -u +%s)

Anyone know how to get it to work?

Thanks!

-WW

---

### Post by geirha on 2008-01-08
```

thetime=$(date -u +%s)
thetime=`date -u +%s`

```
Those two are identical, use the one you think looks the best :)

---

### Post by WereWisher on 2008-01-08
Thanks a lot, Works great ! :guitar:

-WW

---

