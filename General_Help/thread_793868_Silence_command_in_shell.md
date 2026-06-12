---
title: "Silence command in shell"
date: 2008-05-14
forum: General Help
---

### Post by AcidHawk on 2008-05-14
I am trying to run the following script.
```

#!/bin/sh

PPP=`ifconfig ppp0 | grep 'Device not found'`
if [ "X$PPP" = "X" ]; then
   echo "No 3G connection"
else
   echo "3G connection found"
fi


```

The problem is that if I do not have a 3G connection I also get the followin line before my echo...which I do not want to see.
```

ppp0: error fetching interface information: Device not found

```

I am wanting to so something like @echo off in dos... gulp...

---

### Post by chrisccoulson on 2008-05-14
Have you tried running your script like this:
```
./script 2>/dev/null
```
...wlll redirect stderr to /dev/null

---

### Post by AcidHawk on 2008-05-14
So I changed how I was doing this thing!!!

my script now looks like
```

#!/bin/sh

PPP=`ifconfig ppp0 >/dev/null 2>&1`
if [ $? -ne 0 ]; then
   echo "No 3G connection"
else
   echo "3G connection found"
fi

```

Works like a charm.

---

