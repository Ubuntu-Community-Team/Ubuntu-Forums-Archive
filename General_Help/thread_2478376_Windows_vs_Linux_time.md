---
title: "Windows vs Linux time"
date: 2022-08-24
forum: General Help
---

### Post by Autodave on 2022-08-24
I tried to search, but it isn't working.  I have found this many times before though...

What is the command to synchronize Window's time with Ubuntu's time?

---

### Post by Bashing-om on 2022-08-24
Autodave - Hey hey

That is the  ' timedatectl ' command;

see:
[https://ubuntuforums.org/showthread.php?t=2368923](https://ubuntuforums.org/showthread.php?t=2368923) <- set Windows to UTC
[http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/](http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)

[INDENT]should help
[/INDENT]

---

### Post by Autodave on 2022-08-24
Thank you!  I had that saved before, but HD died and I had to replace it.  I tried the search function here, but it apperently isn't working.....I just had the spinning cursor for way over a minute and gaave up.  For anyone that needs it:
timedatectl set-local-rtc 1 --adjust-system-clock

---

