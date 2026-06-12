---
title: "kworker blocking important ports (80)"
date: 2013-07-06
forum: General Help
---

### Post by Khugin on 2013-07-06
Hello!

Since 2 days, after an update, NGINX on my fileserver wasnt able to start anymore. A quick use of ps aux told me that the 'kworker' process was blocking it:

# ps aux | grep worker
root         4  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/0:0]
root         9  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/1:0]
root        11  0.0  0.0      0     0 ?        S    Jul05   0:05 [kworker/0:1]
root        14  0.0  0.0      0     0 ?        S    Jul05   0:03 [kworker/2:0]
root        22  0.0  0.0      0     0 ?        S    Jul05   0:04 [kworker/4:0]
root        26  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/5:0]
root        30  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/6:0]
root        34  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/7:0]
root        49  0.0  0.0      0     0 ?        S    Jul05   0:03 [kworker/1:1]
root        51  0.0  0.0      0     0 ?        S    Jul05   0:04 [kworker/3:1]
root        52  0.0  0.0      0     0 ?        S    Jul05   0:05 [kworker/4:1]
root        53  0.0  0.0      0     0 ?        S    Jul05   0:01 [kworker/5:1]
root        54  0.0  0.0      0     0 ?        S    Jul05   0:01 [kworker/6:1]
root        55  0.0  0.0      0     0 ?        S    Jul05   0:01 [kworker/7:1]
**root        80  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/u:4]**
root        81  0.0  0.0      0     0 ?        S    Jul05   0:02 [kworker/u:5]
root       103  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/3:2]
root       839  0.0  0.0      0     0 ?        S    Jul05   0:00 [kworker/2:2]
root     18524  0.0  0.0   9388   924 pts/0    S+   05:32   0:00 grep --color=auto kworker

I tried to reboot several times, or upgrade - everything seems up-to-date
# uname -r
3.2.0-49-generic

And the other two servers, that basically are identical, dont seem to have this issue.

My question is, how can I stop that kworker to block port 80? - Since until then, I'm not able to access the files over web.

---

### Post by DJ_Max on 2013-07-06
"kworker" is a placeholder process for kernel worker threads. It doesn't use ports, nor does it block any.

What you think is port 80 is actually PID(process ID) 80

Use this, if nothing is displayed than nothing is using port 80

```
netstat -lnptu | grep -P '\:'80''
```

What error message did you get when trying to start Nginx? What do your logs say?

---

### Post by Khugin on 2013-07-06
You were right - sorry. I didnt notice that it's the PID and not the port.

With that tip, I could investigate further, and apparently it had to do with NGINX itself - at the end, this solved the issue:
Sorry for the confusion, I'm not fully used to ubuntu / linux yet

# fuser -k 80/tcp

---

