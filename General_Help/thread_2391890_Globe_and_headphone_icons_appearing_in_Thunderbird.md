---
title: "Globe and headphone icons appearing in Thunderbird email list"
date: 2018-05-14
forum: General Help
---

### Post by stepheny on 2018-05-14
Since I upgraded from 17.10 to 18.04 whenever I open Thunderbird there is a globe icon, and sometimes also headphones icon, appearing in my list of new emails. These icons hide the titles of my emails. (See attached image) When I move the mouse over the icons they partially disappear. When I scroll down there is another globe icon further down the list.

Found the solution in this post [https://ubuntuforums.org/showthread.php?t=2390875](https://ubuntuforums.org/showthread.php?t=2390875)

Installing the fonts-symbola package fixes the problem.

```
sudo apt-get install fonts-symbola
```

---

