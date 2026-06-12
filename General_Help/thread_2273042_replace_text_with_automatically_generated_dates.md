---
title: "replace text with automatically generated dates"
date: 2015-04-10
forum: General Help
---

### Post by sohlinux on 2015-04-10
Hello,

I have a text file which looks like this

test tom
test fred
test harry
test jim

there are 12000 names in the text file

I want to replace the word test with dates auto generated so it adds an extra hour to each name down the list

so I will end up with the following
2015-04-10 14:00 tom
2015-04-10 15:00 fred
2015-04-10 16:00 harry
2015-04-10 17:00 jim

once it reaches the end of the day it should continue to the next day and next month and year until the end

how is this possible to do with a bash script?

thanks

---

### Post by Holger_Gehrke on 2015-04-10
Save this
```

#!/bin/bash
date="2015-04-10 14:00"
while read line ; do
    line=${line##test }
    echo $date $line
    date=$(date --date="$date 1 hour" "+%Y-%m-%d %H:%M")
done

```
as dateinsert.sh and make it executable. Call it with
```

./dateinsert < inputfile > outputfile

```
Replace the date in the second line with whatever value you need, but be careful with format, date likes to guess date formats and often guesses wrong.

---

### Post by sohlinux on 2015-04-10
perfect. thanks :)

---

