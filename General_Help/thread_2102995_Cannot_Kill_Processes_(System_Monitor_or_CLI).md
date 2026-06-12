---
title: "Cannot Kill Processes (System Monitor or CLI)"
date: 2013-01-08
forum: General Help
---

### Post by powerofpi on 2013-01-08
A very concerning problem started recently: I cannot kill misbehaving processes (eg. java, skype). 

**Action:** Highlight the process in the System Monitor and 'End Process'
**Result:** No response, the process lives on.

**Action:** Do killall <processname> on the terminal.
**Result:** No response, the process lives on.

**Action:** Do kill <pid> on the terminal.
**Result:** No response, the process lives on.

Any ideas? This problem is infuriating. Typically, the process that cannot be killed is using 100% of one CPU core.

---

### Post by kaushikgaurav on 2013-01-08
try this:

 kill -9 PID (PID of the program you are trying to stop)

---

### Post by ScottDeagan on 2013-01-08
```

sudo killall -9 skype

```

---

### Post by LuciferRex on 2013-01-08
Nevermind.....:(

---

### Post by ScottDeagan on 2013-01-09
Did you manage to close down Skype and Java?

---

### Post by powerofpi on 2013-01-09
> **ScottDeagan said:**
> Did you manage to close down Skype and Java?

Not just yet- I'm waiting for a process to act up again. As soon as there is one and I can test, I'll reply back.

---

### Post by powerofpi on 2013-01-09
> **ScottDeagan said:**
> ```

sudo killall -9 skype

```

killall -9 java worked, thank you guys. I wish the signal mapping were covered in the man page for killall. I don't know what '-9' corresponds too, but it must be powerful sauce ;)

---

### Post by Impavidus on 2013-01-10
Use```
kill -l
``` (that's lower case L) to get the signal mapping.

-9 means kill, the default is terminate, which can be ignored by the program you wish to kill.

---

