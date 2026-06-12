---
title: "Shutdown program after set time"
date: 2018-07-19
forum: General Help
---

### Post by raleigh3 on 2018-07-19
Is there a way to shut down a program after a set amount of time?

For example: Start Seamonkey and have it close after one hour.

This does not work.

```
#!/bin/bash
# Ubuntu_Mate 18.04 LTS
#
#
seamonkey
sleep 1
killall seamonkey
```

---

### Post by ajgreeny on 2018-07-19
For a start, that script would kill it only 1 second after starting it, not one hour as you say you want.
From man sleep:
> sleep NUMBER[SUFFIX]...

Pause  for NUMBER seconds.  SUFFIX may be 's' for seconds (the default), 'm' for minutes, 'h' for hours or 'd'
       for days.
Have you tried
```
#!/bin/bash
seamonkey
sleep 1h; killall seamonkey
```
or just use a simple compound command  ```
seamonkey & sleep 1h; killall seamonkey
```

---

### Post by raleigh3 on 2018-07-19
Thanks. Both methods worked. :-)

---

