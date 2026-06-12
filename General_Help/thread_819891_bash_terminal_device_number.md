---
title: "bash: terminal device number"
date: 2008-06-05
forum: General Help
---

### Post by joeboentoe on 2008-06-05
One simple question:

Which variable or which command can tell me the current terminal device number. I found some things like 'env' but they don't have the current number. So I need something similar then 'pwd' but then for the current terminal device number.

Example:
If the terminal is dev/pts/0 then I would need the '0'.

Thanks.

---

### Post by cariboo on 2008-06-05
Try the **who** command it will tell you which terminal you're in.

Jim

---

### Post by utsuprainfra on 2008-06-05
also, w will output:

heretic@diderot:/etc$ w
 19:59:07 up 42 min,  2 users,  load average: 0.31, 0.24, 0.20
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
heretic  tty7     :0               19:27    0.00s 52.97s  0.12s x-session-manag
heretic  pts/0    :0.0             19:27    0.00s 24.26s  0.00s w


where the second column is the device.

---

### Post by iaculallad on 2008-06-05
Use **tty** command instead to display the exact terminal number you're using. The **who** command determine the users logged on the machine.

```
tty
```

---

### Post by joeboentoe on 2008-06-05
Ok that was what I was looking for, thanks!

---

