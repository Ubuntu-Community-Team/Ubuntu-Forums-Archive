---
title: "Trouble with cronolog"
date: 2016-10-17
forum: General Help
---

### Post by rsodhia on 2016-10-17
I'm hoping someone can help me figure this out. I was recently introduced to cronolog by one of the sysops at my office, so I thought I would try to use it over logrotate to organize my Apache logs better. I setup cronolog as best as I could figure out based on various websites as follows:


```
ErrorLog "|/usr/bin/cronolog /www/log/gamersplane/%Y/%m/%d/error.log"
```


When I restarted Apache, no errors. But now it's days later, and there has not been a single error logged under /www/log/gamersplane/, nor in the old folder where logs used to go. /www/log/gamersplane/ exists and has the same rights that the old folder did. Unfortunately, I'm new to the sysop side of webdev, and I can't figure out what's wrong or what the next steps to figure out what's wrong would be. Any advice is appreciated.

---

