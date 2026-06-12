---
title: "Kill Signals"
date: 2007-02-01
forum: General Help
---

### Post by gaillard on 2007-02-01
I am writting a script and I need to get the stop signals sent but its not working out.

if I use```
 trap "echo EXIT" EXIT 
``` for example, even when I explicitly send ```
kill -s KILL pid_of_whatever
```  it still echos EXIT.  No matter what signal I send I always get EXIT (0) and I have two events I need to send two different signals and recieve them.  Any idea why this is happening?

---

