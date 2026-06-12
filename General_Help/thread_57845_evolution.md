---
title: "evolution"
date: 2005-08-18
forum: General Help
---

### Post by hpinar on 2005-08-18
evolution doesn't start... either from panel or command line it just seems as if it's processinng and then nothing...

---

### Post by nocturn on 2005-08-18
What kind of output do you get on the command line?

Can you try:
evolution --force-shutdown

and start it again.

---

### Post by hpinar on 2005-08-18
[QUOTE=nocturn]What kind of output do you get on the command line?

Can you try:
evolution --force-shutdown

and start it again.[/QUOTE]

i don't get any output. it just drops root shell back after a few seconds... It doesn't hang up, it just ends the process without any result

---

### Post by nocturn on 2005-08-18
[QUOTE=hpinar]i don't get any output. it just drops root shell back after a few seconds... It doesn't hang up, it just ends the process without any result[/QUOTE]

Are you running as root (you shouldn't)?

---

### Post by JoshWilson on 2005-08-18
[QUOTE=hpinar]evolution doesn't start... either from panel or command line it just seems as if it's processinng and then nothing...[/QUOTE]
 Try the following to see if it simply isn't able to determine your default display.

/usr/bin/evolution-2.2 --display=10.15.3.59:0

substitute 10.15.3.59 with your IP Address of the machine.

---

