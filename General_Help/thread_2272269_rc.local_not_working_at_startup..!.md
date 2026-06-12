---
title: "rc.local not working at startup..!"
date: 2015-04-05
forum: General Help
---

### Post by aathi on 2015-04-05
I just tested whether script written in etc\rc.local works..
my rc.local  :- 

```
#!/bin/sh -e
sudo chmod u+x /home/<USERNAME>/scripts/test.sh
exit 0

```
my shell script (test.sh)
```


#!/bin/bash
firefox



```

Idea is to open firefox when system boots. I get nothing. Could anyone identify the error in my code..

---

### Post by coffeecat on 2015-04-05
Support request, not Ubuntu, Linux and OS Chat thread.

*Thread moved to **General Help**.*

---

### Post by ian-weisser on 2015-04-05
> **aathi said:**
> Idea is to open firefox when system boots. I get nothing. Could anyone identify the error in my code..

You haven't told the system which display to use.

---

### Post by steeldriver on 2015-04-05
... as far as I can see, you haven't actully told the system to **execute** your script, just to **set its execute permission bit**

Regardless, rc.local just isn't the right place for something that needs a desktop session to run within - you should be using the GUI's 'Startup applications' settings

---

