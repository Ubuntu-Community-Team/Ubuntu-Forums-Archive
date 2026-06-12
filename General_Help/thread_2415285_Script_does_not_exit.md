---
title: "Script does not exit"
date: 2019-03-23
forum: General Help
---

### Post by raleigh3 on 2019-03-23
This runs ok, but does not exit?

```
#!/usr/bin/env bash
#
# The time is in milliseconds !! 3000 = 3 seconds
# 1 minute = 1000 x 60 = 60000
while :; do
  if (( $(xprintidle) >= 3000 )); then
    xdotool mousemove_relative 1 1
    echo "test of xprintidle...It's been 3 seconds of inactivity."
  fi
  sleep 0.5
done

```

---

### Post by sisco311 on 2019-03-23
It's an infinite loop [https://en.wikipedia.org/wiki/Infinite_loop](https://en.wikipedia.org/wiki/Infinite_loop)

---

### Post by raleigh3 on 2019-03-23
```
xdotool mousemove_relative 1 1
    echo "test of xprintidle...It's been 3 seconds of inactivity."
   **_ exit_**
```

---

