---
title: "Processes with &quot;idle&quot; priority hog disk"
date: 2014-02-23
forum: General Help
---

### Post by halfbeing on 2014-02-23
I regularly find that my computer becomes unusable for long periods (typically 20 minutes or more) while various background tasks hog the disk. When I look at what is going on in iotop I see that some of these processes have idle priority. My understanding (and tell me if I'm wrong) is that idle priority is supposed to mean that these processes won't use the disk while processes with higher priority are using it. But that is not what is happening. For instance after I started a software update a little while back a "find /" process spontaneously started with user nobody and priority idle. Now the two processes are fighting over the disk and consequently even typing this simple little message is a real battle.

Is there any way to tame these background tasks so that they really do only use the disk when it is idle?

---

