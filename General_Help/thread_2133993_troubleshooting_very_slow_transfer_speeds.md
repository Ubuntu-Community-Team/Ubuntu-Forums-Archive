---
title: "troubleshooting very slow transfer speeds"
date: 2013-04-09
forum: General Help
---

### Post by Eniac on 2013-04-09
Hello, I have been running an ubuntu 10.10 server in a company for a long time. we basically use it as a file share server with raid. it works fine on its own.

lately I've been getting reports of atrocious transfer speeds, but only during certain times of day and I am trying to discover what is going on.

the fact that it is recurrent probably means its a cron, except our cron only has one task and does not occur at the problematic time of the day, in the morning.

We have several automated backup operations from all clients to the server every day. each client uses the software GoodSync to schedule backup of their data on the server, at night.

The entire company is wired on gigabit, so transfer speeds at night are exceptionally fast, each client requires no more than 10 minutes to backup their stuff.

therefore, in the morning, server load should be back to normal.

I will admit that my technical skills with ubuntu are "fair". I am moderately comfortable with the command line, editing configs with nano, following & adapting guides for more difficult task in linux but otherwise I lack that deep understanding of linux commands to even know where to start.

My question to you is: how do I start finding out what is going on? Is there any log I can have created to monitor application network usage? or, specifically, how can i identify the network hog. Once i know what the problem is, I probably can deal with the problem.

Thank you for you help.

---

