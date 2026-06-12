---
title: "stress-ng and iperf simultaneusly"
date: 2020-06-18
forum: General Help
---

### Post by alonsosara44 on 2020-06-18
Hi! 

How can I run stress-ng and iperf at the same time? I want to stress the cpu with stress-ng and then measure the bandwidth with iperf. But when I run stress-ng I can't run any other command until it ends. Is possible to do what I want? How could I do it?

Thanks,
Sara

---

### Post by kneutron on 2020-06-20
--Open up another tab in Terminal, or start another xterm, or install/use GNU ' **screen** ' package, or put an '&' at the end of the command to start it in the background

Example usage:

```

stress-ng& iperf&

```

--You can monitor which jobs are running by issuing ' **jobs** ' at the bash prompt, and ' **kill** %1 ' to kill e.g. the 1st job

--Perfectly Safe Example:

```

$ sleep 30 & sleep 30 &
[1] 58970
[2] 58971


~ $ jobs
[1]-  Running                 sleep 30 &
[2]+  Running                 sleep 30 &

$ kill %2
[2]+  Terminated: 15          sleep 30
```

---

### Post by Impavidus on 2020-06-21
Just open a second terminal. I often have 5 to 8 terminals open at the same time. If you have no GUI, use the tricks mentioned above.

---

