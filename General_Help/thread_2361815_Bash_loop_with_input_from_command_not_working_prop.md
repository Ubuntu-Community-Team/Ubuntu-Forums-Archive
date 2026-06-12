---
title: "Bash loop with input from command not working properly"
date: 2017-05-21
forum: General Help
---

### Post by Andrew_Welham on 2017-05-21
I have a script to analyse DNS queries for failed calls and is meant to monitor the query log live

The loop which reads the log looks like this

#!/bin/bash
while read LOGLINE
do
echo $LOGLINE
done < <(tail -f /var/log/named/query.log)

Unfortunately it misses entries is the log, almost as if while its processing other lines in the script it is missing input. The other weird part, is sometimes a number of past entries appear several seconds later , like they have been in a que. Not much good for live monitoring.

Any ideas how to make this part of the script more reliable


Many Thanks

---

### Post by steeldriver on 2017-05-21
The second issue is most likely due to buffering: see for example [How to get &#8220;instant" output of &#8220;tail -f&#8221; as input?](http://stackoverflow.com/a/22162811/4440445). Try prefixing the tail command with stdbuf -oL

The first issue I can't comment on

---

