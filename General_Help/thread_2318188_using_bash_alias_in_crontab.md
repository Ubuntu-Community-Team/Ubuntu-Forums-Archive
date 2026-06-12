---
title: "using bash alias in crontab?"
date: 2016-03-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-03-23
Hi all, 

Is it possible to use bash alias in crontab?
I tried it, but it says 

```
[COLOR=#000000]/bin/sh: 1: alias_name1: not found[/COLOR]
```

It works fine when I run it manually in console. 
Thanks ahead.

---

### Post by SeijiSensei on 2016-03-23
Cron doesn't have the same environment as you do.  You can set environment variables at the top of the crontab as I recall, but why not just use the complete path to the actual program, like /usr/bin/myapp.  That's a lot more reliable.

---

### Post by marchello_lippi2 on 2016-03-24
[**[COLOR=#000000]SeijiSensei,[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")

is that what should be set in the beginning of my crontab? 

#!/bin/bash

---

### Post by ian-weisser on 2016-03-24
No.
A crontab is not a bash script.
Crontabs are intended to be read by the cron application.

---

### Post by marchello_lippi2 on 2016-03-24
[COLOR=#DD4814][ian-weisser]("http://ubuntuforums.org/member.php?u=1841707"), 
thanks[/COLOR]

---

