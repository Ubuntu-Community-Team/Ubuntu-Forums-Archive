---
title: "why 2 different services are enabled by default for same task in ubuntu feisty"
date: 2007-08-30
forum: General Help
---

### Post by cyneuron on 2007-08-30
Hello there !

in services section of my ubuntu feisty system, there are two different services for same task, namely :

1. anacron and atd for action scheduler.

2. klogd and syskogd for computer activity logger.

why are these two services enabled by default, while only one should be sufficient ?

and can both of these services stopped altogether without having any trouble ?

i have tried disabling these four services. i didnt notice any problem, so should i keep them disabled ?

---

### Post by bogolisk on 2007-08-30
> **cyneuron said:**
> Hello there !

in services section of my ubuntu feisty system, there are two different services for same task, namely :

1. anacron and atd for action scheduler.

2. klogd and syskogd for computer activity logger.

why are these two services enabled by default, while only one should be sufficient ?

and can both of these services stopped altogether without having any trouble ?

i have tried disabling these four services. i didnt notice any problem, so should i keep them disabled ?

Delayed program execution  is for command scheduling while anacron is cron for **non**-24/7 boxes. klogd is the helper daemon that pull kernel messages and relay it to syslogd.

There's no duplication.

---

