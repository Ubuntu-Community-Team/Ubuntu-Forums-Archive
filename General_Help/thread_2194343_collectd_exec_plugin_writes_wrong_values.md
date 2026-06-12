---
title: "collectd exec plugin writes wrong values"
date: 2013-12-17
forum: General Help
---

### Post by alsim114 on 2013-12-17
I have a script that collectd's exec plugin calls, but for some reason it stores the value "5" into csv.

Here is the script:
#!/bin/bash


pid=`pgrep slapd`
randin=`lsof -p $pid -n | wc -l`
echo "PUTVAL `hostname -f | tr . _`/exec/current N:$randin"

i have tried using logfile to debug this, nothing gets displayed. If i try storing a variable with a manually assigned variable, the correct value is stored in csv logs. When i run the script manually, i get the output "PUTVAL hostname/exec/current N:70". I have looked at at least 40 different threads on various forums and read the collectd documentation at least 80 times with no luck. HELP!

---

### Post by alsim114 on 2013-12-18
Update, this script stores the value fine

#!/bin/bash


pid=`pgrep slapd`
lsof -p $pid -n | wc -l > /tmp/wcslapd
randin=`cat /tmp/wcslapd`
echo "PUTVAL `hostname -f | tr . _`/exec/current N:$randin"

but feels kinda messy. If possible, a solution that doesnt need to make an external file would be great. Any suggestions?

---

