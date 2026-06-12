---
title: "Script: Using dd to write crap to disk (secure erase)"
date: 2007-08-30
forum: General Help
---

### Post by zwanzig on 2007-08-30
I tried to use this script for using dd to write crap to disk (secure erase)

```
for (( i = 0;i<10;i++ )); do
 dd if=/dev/urandom of=/dev/hda && dd if=/dev/zero of=/dev/hda
done
```
 but I get the output:
```
1: Syntax error: Bad for loop variable
```

---

### Post by zwanzig on 2007-08-30
Never mind.
This worked a lot better. Dunno what made the difference thow
```
#!/bin/bash
for ((a=0;a<10;a++))
do dd if=/dev/urandom of=/dev/hda && dd if=/dev/zero of=/dev/hda
done
```

---

