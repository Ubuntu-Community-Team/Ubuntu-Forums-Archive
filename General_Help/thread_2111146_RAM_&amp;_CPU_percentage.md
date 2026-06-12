---
title: "RAM &amp; CPU percentage"
date: 2013-02-01
forum: General Help
---

### Post by babakflame on 2013-02-01
Dear Buddies
Hi

Iam using ubuntu 11.10 (oneiric ocelot). How can I find that How much percent of my system RAM and CPU is involved during running a program?

---

### Post by codemaniac on 2013-02-01
Hi bavakflame,

The below document should help you. Please see the "System Information Commands" section.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by rnerwein on 2013-02-01
> **babakflame said:**
> Dear Buddies
Hi

Iam using ubuntu 11.10 (oneiric ocelot). How can I find that How much percent of my system RAM and CPU is involved during running a program?
hi
just open a terminal and using the "ps" command.
ps uax | grep your_process
for further information see: man ps
! memory is VSZ and RSS (VSZ shouldn hassle you, RSS more.
but that's not all ! if top show you your process using 100% of CPU (same as top, htop and system-monitor) this means your process is using 100% of ! one cpu. and 100%, even
you got only one mustn't be bad. it depends of what you are running and in wich mode is
the CPU (e.g. you are running a huge zip-file "one" cpu will be at 100% in usermode).
cheers

---

### Post by dcstar on 2013-02-04
> **babakflame said:**
> Dear Buddies
Hi

Iam using ubuntu 11.10 (oneiric ocelot). How can I find that How much percent of my system RAM and CPU is involved during running a program?

Use the System Monitor.

---

### Post by babakflame on 2013-02-07
Dear buddies
Hi
Thanks for all ur helps. However, I found ps uax the best. I did not find system monitor in ubuntu 11.10. Maybe its in other versions of ubuntu.:guitar::guitar:

     Regards
     Bobi

---

### Post by mörgæs on 2013-02-07
If this solves your problem, please mark the thread so.

[Linuxatemyram]("http://www.linuxatemyram.com/") might prevent misunderstandings regarding memory use:

---

