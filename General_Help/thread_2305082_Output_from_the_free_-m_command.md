---
title: "Output from the free -m command"
date: 2015-12-02
forum: General Help
---

### Post by c_xy on 2015-12-02
Hello,

I was curious about the output from the free -m command.

We are running a linux server and here is the following output

```

[%]free -m
             total       used       free     shared    buffers     cached
Mem:         96574      95998        575         46       2000      85905
-/+ buffers/cache:       8093      88480
Swap:       183103          0     183103


```
When I type, "top" I don't see any processes taking up much memory. So, I was concerned to see so much memory used in the first line (95998).

What is the difference between the Mem: line and -/+ buffers/cache line? Which line indicates how much memory is used?

Any help is greatly appreciated.

Thank you.

c

---

### Post by Doug S on 2015-12-02
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=2244787") thread.

---

### Post by c_xy on 2015-12-03
Doug S, thank you so much.

The linked thread answered all of my questions.

Thanks again,

c

---

