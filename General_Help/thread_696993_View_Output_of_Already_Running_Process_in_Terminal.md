---
title: "View Output of Already Running Process in Terminal"
date: 2008-02-14
forum: General Help
---

### Post by jobsonandrew on 2008-02-14
Im starting Valve's CounterStrike Source dedicated server from a script.. so I cant see the terminal output.. (I dont want to have a terminal open all the time for it) is there a way that i can view the output of an existing process? maybe a simple terminal command without installing/using 'screen'?

---

### Post by pointone on 2008-02-14
You could pipe the output to a file/terminal from your script, as in:

```
dedicated_server >output.log
```
... or:
```
dedicated_server >/dev/tty1
```

---

