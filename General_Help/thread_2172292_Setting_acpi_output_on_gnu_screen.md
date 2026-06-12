---
title: "Setting acpi output on gnu screen"
date: 2013-09-04
forum: General Help
---

### Post by CkDGTAT on 2013-09-04
Hi,

I need to have a continuous output of acpi on one gnu screen window, I tried this

```

mkfifo ~/.f
screen -t fifo 2 tail -f /home/user/.f



```

and a crontab that would redirect acpi in .f every minute.

The problem is that gnu screen fails to update the pipe

---

### Post by CkDGTAT on 2013-09-07
Hi all,

Suppose I'd like to have a acpi continuous output in one window. What might be the best way of doing it?

I tried 

```
mkfifo .acpi
```
```
 tail -f ~/.acpi 
```

and a crontab that would send acpi ouput to the pipe.

The window refuse to refresh itself. I use Konsole.

Thanks

---

### Post by steeldriver on 2013-09-07
What exactly is on the other end of the pipe? are you sure it's not just because the stream is being buffered on that side?

---

### Post by matt_symes on 2013-09-07
Thread merged.

---

### Post by CkDGTAT on 2013-09-25
Find another solution

> watch -n 1 acpi

---

