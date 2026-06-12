---
title: "Epiphany browser launcher script"
date: 2007-05-31
forum: General Help
---

### Post by htor on 2007-05-31
Hi,
Here is the script (I didn't want to deal with writing epiphany extensions) that I use in my epiphany launcher in order to keep him clean :

```
#! /bin/sh

epiphany &
sleep 5

while [ `ps -C epiphany -o cmd|wc -w` -eq 2 ]
do
sleep 5
done

rm -r /home/papa/.gnome2/epiphany/mozilla/epiphany/Cache 
rm /home/papa/.gnome2/epiphany/mozilla/epiphany/cookies.txt 
rm /home/papa/.gnome2/epiphany/ephy-history.xml
```

What do you think? anyone has suggestions how can I to improve this script ?

---

