---
title: "start a script from another tty"
date: 2008-05-04
forum: General Help
---

### Post by moka on 2008-05-04
Hello all,

im quite new to linux and was wonder if there was a way to start a script e.g. ./script1 on another tty

for example im on /dev/pts/0 and i want to start a script called ./script1 on /dev/pts/1

how would i go about doing this?

thanks alot
moka

---

### Post by macaholic on 2008-05-04
If I understand you correctly, you jsut want to start another script without halting the fist one? If that is the case, then you can jsut switch to another tty terminal and have at it.

---

### Post by moka on 2008-05-04
sorry i didnt explain myself too well,

basically im creating a server/client simulation and need to be able to start a script on another terminal from the first terminal without touching it... 

is there not a command to start a script called for example ./script1 from pts0 on pts1

thanks

---

