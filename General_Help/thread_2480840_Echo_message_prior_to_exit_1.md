---
title: "Echo message prior to exit 1"
date: 2022-11-11
forum: General Help
---

### Post by raleigh3 on 2022-11-11
This works well at running Seamonkey only once per 24 hours. Firefox is my main browser but I can not use the ReminderFox plugin with it. 

It only works with Seamonkey.

I want to put an echo statement prior to exit 1 showing that Seamonkey has already ran once today.

```
#!/bin/bash
#
#  Run this script only once a day
#  Delay is necessary

# Creates this file /var/tmp/SeaAfter5.sh.flag
flag="/var/tmp/$(basename -- $0).flag"
min_age=$(( 60 * 60 * 24 )) # 24 hours

if [ -e "$flag" ] ;then
  (( $(date +%s) - $(date +%s -r "$flag") > min_age )) || exit 1
fi
touch "$flag"

# Proceed with starting Seamonkey
sleep 5 && seamonkey

```

---

### Post by &amp;KyT$0P# on 2022-11-12
Try changing that line to be an if statement instead?  Something like this -
```
if (( $(date +%s) - $(date +%s -r "$flag") > min_age ));then
  :  # do nothing
else
  echo 'Seamonkey has already ran once today'
  exit 1
fi
```

---

