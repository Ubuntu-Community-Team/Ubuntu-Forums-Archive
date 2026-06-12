---
title: "Shell script apending time to file no workies :("
date: 2008-02-22
forum: General Help
---

### Post by Snoopy381 on 2008-02-22
hi, im trying to make a quick shell script and all it does is append the current time to a file.
iv been trying to get this to work for a couple of hours (yes sad i know seeing how complex it is :P) so far what if got is

```

TIME=$(date)

sed -i '$a\Time is `$TIME` ' sed.php;

echo $TIME
```

the echo comes up with the right time (current time, but when i look in sed.php all it apended was Time is `$TIME`. i know its probley something very simple (quotes mabe?)  but after a couple or hours looking i am resorting to asking the ppl how hopefully know. also it would be good if i could get this to work with 1 line without declaring TIME. 

btw im usunbg ubuntu 7.10 and the BASH shell.

---

### Post by dje on 2008-02-22
You want to add $TIME to sed.php?
try this:
```
TIME=$(date)

sed -i '$a\Time is `$date` ' sed.php;

echo $TIME >> sed.php
```
hope that helps you

dje

---

### Post by kpkeerthi on 2008-02-22
echo "Time is $date" >> myfile.php

---

### Post by Snoopy381 on 2008-02-22
sweet thanks guys works perfect, looks like i was going about this the wrong way, dje your example worked straight away and kpkeerthi i removed the $ and it also works, sweet

---

### Post by dje on 2008-02-22
You're very welcome Snoopy381

dje

---

