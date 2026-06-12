---
title: "start-stop-daemon"
date: 2006-07-20
forum: General Help
---

### Post by Gujs on 2006-07-20
Hello,

Is it possible to start program wit some options like this:

start-stop-daemon --start --exec "/usr/bin/java -jar some.jar"

Thanks

---

### Post by swamytk on 2006-07-20
if some.jar is a daemon, what you say is ok.

if some.jar is not a daemon, why do you need start-stop-deamon for a ordinary program? just u can call "/usr/bin/java -jar some.jar"

---

