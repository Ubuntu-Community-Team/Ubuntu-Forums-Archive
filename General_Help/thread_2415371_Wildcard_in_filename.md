---
title: "Wildcard in filename ?"
date: 2019-03-24
forum: General Help
---

### Post by raleigh3 on 2019-03-24
The check for a .part file fails.

Is it because I used a wildcard?

```
file="/home/andy/Downloads/*.part"

if [[ -f $file ]];
then
echo "File download in progress."
        echo "Computer can not suspend until download is complete."
        echo "Now exiting."
        sleep 2      
exit 
fi

echo "This script will suspend computer in 10 minutes if there is no mouse or keyboard activity."
while :; do
  if (( $(xprintidle) >= 600000 )); then
    systemctl suspend
fi
  sleep 0.5
done
```

---

### Post by HermanAB on 2019-03-24
```

if [[ -f $file ]];

should probably be:
if [[ -f "$file" ]];

```

The double quotes will expand the variable.

---

