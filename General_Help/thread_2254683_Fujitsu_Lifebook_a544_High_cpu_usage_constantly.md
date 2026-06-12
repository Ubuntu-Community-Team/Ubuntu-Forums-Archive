---
title: "Fujitsu Lifebook a544: High cpu usage constantly"
date: 2014-11-29
forum: General Help
---

### Post by jmmrly on 2014-11-29
I have a fujitsu lifebook a544 and have the latest version of ubuntu installed. I've noticed that my laptop fan is constantly on and fairly loud. This is not the case in windows and is usually silent due to very low cpu usage in windows (0-2% cpu usage idle) However, i loaded up task manager and shows cpu usage ranging from 20-30% idle. How do i find the issue and fix it?
Thanks.

[http://oi62.tinypic.com/wbubd1.jpg](http://oi62.tinypic.com/wbubd1.jpg)

---

### Post by mcduck on 2014-11-29
For starters, you could click on the "CPU%" column to sort based on CPU use, and take a look at what's highest...

---

### Post by jmmrly on 2014-11-29
> **mcduck said:**
> For starters, you could click on the "CPU%" column to sort based on CPU use, and take a look at what's highest...

That's what I did. But it shows all the processes as 0%.

---

### Post by mcduck on 2014-11-29
click it again to sort in opposite direction.

Or open a terminal and run "top" for a better view of what's running on the system. I don't think I've ever uses the rak manager you have in your screenshot (System Monitor has a bit more features), but it seems to be only listing processes owned by your user, while it could just as well be some system process using the CPU...

---

### Post by ajgreeny on 2014-11-29
Are you absolutely sure it is your cpu that is causing the problem?

I also suggest you use terminal command **top** for seeing better what is going on. With top open hit upper-case P to sort the columns by cpu %age and upper-case M for memory usage.

---

### Post by jmmrly on 2014-11-29
[http://oi60.tinypic.com/2hicfw7.jpg](http://oi60.tinypic.com/2hicfw7.jpg)

Is this normal? It approximates that my laptop will last 2 and a half hours on battery when windows lasts around 4 to 6 hours.

---

### Post by ajgreeny on 2014-11-30
No, it is not normal. Kworker is a kernel activity of some kind that should never take 77&#8240; cpu, so more investigation is needed, I will have to investigate more and will try to come back with a mote helpful answer.

However, there are lots of references to this problem but not one single answer, so you may also need to search  using search term
Kworker high cpu %age

Good luck.

---

### Post by jmmrly on 2014-11-30
> **ajgreeny said:**
> No, it is not normal. Kworker is a kernel activity of some kind that should never take 77‰ cpu, so more investigation is needed, I will have to investigate more and will try to come back with a mote helpful answer.

However, there are lots of references to this problem but not one single answer, so you may also need to search  using search term
Kworker high cpu %age

Good luck.

Thought so. Thanks anyway - Thought it was something alike the windows "System Idle Process" but guess not.

---

### Post by jmmrly on 2014-11-30
[http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)

This worked for me. And it was the same high value which was noted in this post. (gpe13)

---

