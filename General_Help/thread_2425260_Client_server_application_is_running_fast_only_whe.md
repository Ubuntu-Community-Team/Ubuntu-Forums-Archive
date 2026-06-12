---
title: "Client server application is running fast only when I click or hover the mouse"
date: 2019-08-22
forum: General Help
---

### Post by harsh6894 on 2019-08-22
Client and server both are same host on which we are running application and that application is taking too much time (3 hours). If we continuously click or hover the mouse or runs the "while(1) { print "Hello World" } script in terminal with the application then application is running fast and completing in 15 minutes. What can be the reason of application running fast when we do above mentioned activities? What is the solution such that application runs fast without doing continuous click/ hovering the mouse/running hello world script? My impression is when we don't click or hover the mouse at that time some other ubuntu application is taking most of the CPU time or system is going in sleep state. Could anyone help if they know what the issue is here.

---

### Post by uRock on 2019-08-22
What is the application you're running? Which version of ubuntu?

---

### Post by harsh6894 on 2019-08-22
Application is ZMQ 4.3.2. An ubuntu version is 16.04.3 LTS.

---

### Post by TheFu on 2019-08-22
[https://unix.stackexchange.com/questions/25372/turn-off-buffering-in-pipe](https://unix.stackexchange.com/questions/25372/turn-off-buffering-in-pipe)  - I'm guessing it is an output buffer thing.

Ask your admin for the performance monitoring data.  That should be able to point out where the bottle neck is happening.  Is it pretty standard admin work, so she/he should have it available. If not, get a monitoring tool installed and gather some facts about the system, RAM, processes, file I/O, network I/O, disk I/O, scheduling.
 
Is ZMQ the same as ZeroMQ?

---

### Post by harsh6894 on 2019-08-23
Let me turn off the buffering to check it's an output buffer causing the delay or not. Thank you so much for the link. I will also collect performance monitoring data to know the bottle neck. What can be the reason of such bottleneck disappearing when we have some mouse activity or while(1) script on terminal?

[COLOR=#000000]Is ZMQ the same as ZeroMQ? --> Yeah it's same[/COLOR]

---

