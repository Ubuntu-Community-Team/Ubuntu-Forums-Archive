---
title: "OS started to lag/freeze"
date: 2017-05-15
forum: General Help
---

### Post by conamorek on 2017-05-15
Hello,

I am using Ubuntu 16.04 LTS and it's the only OS on my disc.
My problem is that after installing a new SSD the system started to freeze/lag while managing some processes. Everything was fine for a week and after that the problems came. 
It's like it's working properly for a minute and after this the process is 'not responding' and goes black/white colour. After a 15~ seconds everything goes well till the next process freezes.
I haven't changed any hardware except this HDD -> SSD. I also tried to autoclean/autoremove, checked disc by system settings and checked the temperatures of CPU/GPU which are on a really decent level (35 Celsius Degrees~).

Any ideas? Maybe any software to optimize the performance?

---

### Post by Bashing-om on 2017-05-15
conamorek; Hello; Welcome to the forum.

I experienced a similar issue with system crashes . By trial and error I did determine was a graphic's driver issue.
What is the graphic's set you are running ?
```

lspci -nnk | grep -iA3 vga

```
as a place to start looking.

[INDENT][INDENT]maybe this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by conamorek on 2017-05-15
@[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] [1002:6819]
    Subsystem: Hightech Information System Ltd. Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] [1787:2320]
    Kernel driver in use: radeon
    Kernel modules: radeon


```

I did not install any external drivers for GPU but a Ubuntu's standard ones, which were provided while installing Ubuntu.
My GPU is Radeon HD 7850.

---

### Post by Bashing-om on 2017-05-15
conamorek; Well ..

Decent card and the correct driver is loaded .

All I can suggest at this point is to watch 'top' and tail the log file(s), see if you can spot some  anomaly - ( running out of memory ?)


[INDENT]not much -
[INDENT][INDENT]a tough nut to crack
[/INDENT][/INDENT][/INDENT]

---

### Post by conamorek on 2017-05-15
[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508");

Where can I find them, or at least which files shall I check?

---

### Post by Bashing-om on 2017-05-15
conamorek; Well.

What I do, is in my main work space
activate a terminal and in this terminal execute
(resize the window to suit )
```

top

```
activate an additional terminal ( here where you can watch it, again_ :
execute in this new terminal:
```

journalctl -f

```

[INDENT]see what you can see
[/INDENT]

---

### Post by conamorek on 2017-05-16
[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508");

I've tried to do that but when the processes are starting to not respond then the top/journalctl -f , they don't work too. I mean, there is no ability to check if there was any higher usage of CPU/RAM or error.

---

