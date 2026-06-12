---
title: "CPUlimit trick?"
date: 2012-12-20
forum: General Help
---

### Post by taunnt on 2012-12-20
Hello I'm trying to use CPUlimit with Handbrake. What I do is enter this command in terminal:

cpulimit -l 50 ghb

That will launch Handbrake, but when it starts the encoding it uses 10% of the CPU (so it shows in the system CPU monitor). What ever setting I do (besides) 100 it will only use about 10% of the CPU. Is there some kind of trick to it? Any one else try to use CPUlimit and Handbrake?

---

### Post by cwsnyder on 2012-12-21
I think you are reading your documentation incorrectly.  CPUlimit is to set a maximum CPU usage so that you can use your computer for other processes besides the transcoding.  It does not increase the usage to that limit, it sets a maximum usage.

---

### Post by Rexilion on 2012-12-21
Maybe you could try starting Handbrake with reduced scheduler priority?

```
nice ionice -c3 ghb
```

The kernel also contains a feature for automatic schedule grouping which distributes CPU time according to need and keeps it all quite even.

---

### Post by taunnt on 2012-12-21
Yep, the isse I have with Handbrake is that it freezes my comp. I tried with this:

nice ionice -c3 ghb

and it still freezes. What does the -c3 flag do exactly?

Thanks for your help.

> **Rexilion said:**
> Maybe you could try starting Handbrake with reduced scheduler priority?

```
nice ionice -c3 ghb
```

The kernel also contains a feature for automatic schedule grouping which distributes CPU time according to need and keeps it all quite even.

---

### Post by raja.genupula on 2012-12-21
[http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/](http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/)
[http://linux.101hacks.com/monitoring-performance/hack-100-nice-command-examples/](http://linux.101hacks.com/monitoring-performance/hack-100-nice-command-examples/)


These are the two best links i found for you .

---

### Post by Rexilion on 2012-12-22
> **taunnt said:**
> Yep, the isse I have with Handbrake is that it freezes my comp. I tried with this:

nice ionice -c3 ghb

and it still freezes. What does the -c3 flag do exactly?

Thanks for your help.

-c3 gives the process the 'idle' IO schedule (disk IO) priority, which is the lowest. Any other process accessing the disk will have an priority over this process.

Any last thing that I can think which freezes your computer is either:
- You are suffering from the Linux interaction bug with some IO controllers
- Handbrake is using hardware acceleration somewhere, which is not easy to throttle

---

